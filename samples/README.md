# ZAP Language Support for VS Code

A VS Code extension that provides language support for ZAP schema files (built on Cap'n Proto).

## Features

- Go to definition
- Diagnostics (error reporting)

## Requirements

- Cap'n Proto compiler(version 1.1.0 or higher): [capnp](https://capnproto.org/install.html)
- ZAP Language Server: [zap-ls](https://github.com/zap-proto/lsp)

## Extension Settings

This extension contributes the following settings:

* `zap-ls-client.languageServer.path`: Path to the ZAP language server executable. If not specified, the extension will first look for a zap-ls binary in the extension directory, then search in the system PATH. For Linux x86_64 systems, the binary will be automatically downloaded if not found in either location.
* `zap-ls-client.compiler.path`: Path to the ZAP schema compiler executable. If not specified, it defaults to "zap" from the system PATH. When using a bundled version of zap-ls (built with -DUSE_BUNDLED_CAPNP_TOOL=ON), this setting is optional and the bundled compiler will be used automatically.
* `zap-ls-client.compiler.importPaths`: Additional import paths for ZAP schemas.
* `zap-ls-client.server.extraEnv`: Extra environment variables that will be passed to the zap-ls executable.
  * `CPP_LOG`: Log level for the Cap'n Proto language server.
    * Example: `CPP_LOG=lsp_server=info`: Set log level to info.
    * Default: `CPP_LOG=lsp_server=warning`

#### Example configuration:

To customize the client settings, edit the `.vscode/settings.json` file in your workspace as follows:

```json
{
    "zap-ls-client.languageServer.path": "/absolute/path/to/zap-ls",
    "zap-ls-client.compiler.path": "zap",
    "zap-ls-client.compiler.importPaths": [
        "path/to/schema/imports"
    ],
    "zap-ls-client.server.extraEnv": {
        "CPP_LOG": "lsp_server=warning"
    }
}
```
See [example configuration](https://github.com/zap-proto/lsp/blob/main/samples/client/testFixture/.vscode/settings.json) for more details.