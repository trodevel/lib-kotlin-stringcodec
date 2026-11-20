# stringcodec

`stringcodec` is a lightweight Kotlin library that provides deterministic single-line string encoding and decoding. It ensures strings containing spaces, newlines, plus signs, or backslashes can be safely stored on a single line in space-separated plaintext files without breaking column or line integrity.

## Features

- **Single-Line Integrity**: Encodes newlines (`\n`) as literal `\n` characters.
- **Space Handling**: Encodes spaces (` `) as `+` and literal `+` characters as `++`.
- **Escaping**: Encodes backslashes (`\`) as `\\`.
- **Reversible**: `decode(encode(str)) == str` for all valid input strings.

## Encoding Transformations

| Character | Encoded Output |
| :--- | :--- |
| Space (` `) | `+` |
| Plus (`+`) | `++` |
| Backslash (`\`) | `\\` |
| Newline (`\n`) | `\n` (literal backslash followed by 'n') |

## Usage

```kotlin
import com.trodevel.stringcodec.StringCodec

// Encoding
val original = "Hello World+\nSecond Line"
val encoded = StringCodec.encode(original)
// Output: "Hello+World++\nSecond+Line"

// Decoding
val decoded = StringCodec.decode(encoded)
// Output: "Hello World+\nSecond Line"
```

## Dependency

To include `stringcodec` in a Gradle project:

```kotlin
dependencies {
    implementation("com.trodevel.stringcodec:stringcodec:1.0.0")
    // Or via local project dependency:
    // implementation(project(":stringcodec"))
}
```
