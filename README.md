# test-protos

A protobuf grammar showcase covering every major language construct across
proto2, proto3, and editions 2023/2024.

Syncs to [buf.build/svanburenorg/test-protos](https://buf.build/svanburenorg/test-protos)
via [buf-action](https://github.com/bufbuild/buf-action) on push.

## Structure

### `proto2/`

| File | Demonstrates |
|---|---|
| `custom_options.proto` | `extend` on all 8 descriptor option message types |
| `scalars.proto` | All 15 scalar types × `required`/`optional`/`repeated`; every default-value literal (`inf`, `-inf`, `nan`, octal, hex, string escapes, adjacent-string concatenation); `packed`, `ctype`, `jstype`, `debug_redact`, `json_name` |
| `enums.proto` | Closed enums; `allow_alias`; enum-value options; `reserved` with number ranges and `max` |
| `messages.proto` | Nested and recursive messages; `oneof`; all map key types; `group` fields (`optional`/`repeated`/`required`); extension ranges; `reserved` with single-quoted strings |
| `extensions.proto` | `extend` at top level and nested inside a message; complex message-literal option values |
| `services.proto` | All four RPC streaming modes; `idempotency_level`; service and method options |
| `imports.proto` | `import public` (transitive re-export) and `import weak` |

### `proto3/`

| File | Demonstrates |
|---|---|
| `custom_options.proto` | `extend` on descriptor option types in proto3 syntax |
| `basics.proto` | Implicit vs explicit-optional presence; open enums; all map key types; `packed = false` opt-out; single-quoted `reserved` strings |
| `services.proto` | All four RPC streaming modes in proto3 |

### `editions/`

| File | Demonstrates |
|---|---|
| `edition_2023.proto` | All six `features.*` overrides (`field_presence`, `enum_type`, `repeated_field_encoding`, `utf8_validation`, `message_encoding`, `json_format`) at file, field, enum, and message scope; bare-identifier `reserved` names |
| `edition_2024.proto` | `export`/`local` visibility on messages and enums; `import option` |

## CI

On every push, [buf-action](https://github.com/bufbuild/buf-action) runs
`buf push` to sync to the BSR.
On pull requests it runs `buf build`, `buf lint`, and `buf breaking`.

Requires a `BUF_TOKEN` repository secret
(Settings → Secrets and variables → Actions).
