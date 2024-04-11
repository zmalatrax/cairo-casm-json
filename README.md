# Folder Organization

## `src`

Cairo programs, to be compiled with `scarb build`

## `sierra_compiled`

`*.casm.json` : Output of modified [Cairo v2.5.4 compiler](https://github.com/zmalatrax/cairo/tree/feat/2.5.4-casm-json)

## `cairo_to_zero`

Manually (atm) crafted `*.json` files, to be executed on a Cairo Zero runner (e.g. python VM)

The fields `accessible_scopes` and `flow_tracking_data` content is only needed for hints with references (to be confirmed)

The GasBuiltin specified in `main_func.signature.param_types` has no equivalent in the defined builtins of the Cairo Zero runner, it might be the current issue
Adding a user segment for it might be a solution (how ?)

## `starknet`

Starknet compilation artifacts

- `*.contract_class.json`: Result of `starknet-compile`, output a serialized JSON of the Sierra (For Cairo programs, equivalent to `*.sierra.json` from Scarb)
- `*.compiled_contract_class.json`: Result of `starknet-sierra-compile`, otput a serialized JSON of the CASM (no current equivalent for Cairo programs, either in Scarb or compiler, `*.casm.json` files aim to provide this equivalent)

## `scarb_artifacts`

Compilation results from Scarb (`*.casm`, `*.sierra`, `*.sierra.json`), annotated with their respective Cairo program.
The modified compiler adds a new executable `sierra-compile-json` which takes a `*.sierra` file as input and outputs a json
(similar use as `sierra-compile`, different output)

## `zero`

Compiled Cairo Zero programs (with v0.13.0 or v0.13.1)

### `src`

Cairo Zero programs