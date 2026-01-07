# Ruby LSP Plugin for Claude Code

Provides Ruby language intelligence for Claude Code via the [Ruby LSP](https://github.com/Shopify/ruby-lsp) language server.

## Features

- **Go to Definition** - Jump to method, class, and module definitions
- **Find References** - Locate all usages of a symbol
- **Hover Documentation** - View documentation and type information
- **Document Symbols** - Browse all symbols in a file
- **Workspace Symbols** - Search symbols across the project
- **Diagnostics** - Real-time error and warning detection
- **Code Completion** - Intelligent autocompletion suggestions

## Prerequisites

Install the ruby-lsp gem:

```bash
gem install ruby-lsp
```

Verify it's in your PATH:

```bash
which ruby-lsp
```

## Installation

### From Opendate Marketplace

```bash
claude /plugin install ruby-lsp@opendate-marketplace
```

### Manual Installation

1. Clone this repository
2. Run `/plugin` in Claude Code
3. Select "Install local plugin"
4. Point to this directory

## Supported File Types

| Extension | Language |
|-----------|----------|
| `.rb` | Ruby |
| `.rake` | Ruby |
| `.gemspec` | Ruby |
| `.ru` | Ruby |

## Configuration

The plugin uses sensible defaults. Ruby LSP will automatically detect your project's Ruby version via `.ruby-version` or `Gemfile`.

## Version Manager Users (rbenv, asdf, rvm)

Claude Code may not inherit your shell's PATH. If `ruby-lsp` isn't found, create a local plugin override:

1. Create `~/.claude/plugins/local/ruby-lsp/plugin.json`
2. Use the absolute path to your ruby-lsp binary:

```json
{
  "name": "ruby-lsp",
  "version": "1.0.0",
  "description": "Ruby LSP integration for Claude Code",
  "lspServers": {
    "ruby": {
      "command": "/Users/YOUR_USERNAME/.rbenv/shims/ruby-lsp",
      "args": [],
      "extensionToLanguage": {
        ".rb": "ruby",
        ".rake": "ruby",
        ".gemspec": "ruby",
        ".ru": "ruby"
      },
      "env": {
        "PATH": "/Users/YOUR_USERNAME/.rbenv/shims:/usr/local/bin:/usr/bin:/bin",
        "RBENV_ROOT": "/Users/YOUR_USERNAME/.rbenv"
      }
    }
  }
}
```

Replace `YOUR_USERNAME` with your actual username. Find your path with `which ruby-lsp`.

## Troubleshooting

### "No LSP server available"

1. Ensure `ruby-lsp` is installed: `gem install ruby-lsp`
2. Ensure it's in your PATH: `which ruby-lsp`
3. Restart Claude Code after installing the plugin
4. If using rbenv/asdf/rvm, see "Version Manager Users" section above

### LSP not starting

Check the logs:
```bash
cat ~/.claude/debug/ruby-lsp-*.log
```

### Wrong Ruby version

Ruby LSP uses your project's Ruby version. Ensure your version manager (rbenv, rvm, asdf) is configured correctly.

## License

MIT
