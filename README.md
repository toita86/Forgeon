# Forgeon

**Forgeon** is a copier template to generate fully containerized, language-aware development environments using **Neovim** (with your choice of configuration) and language-specific tooling — all inside Docker.

> 🧠 Forgeon = Forge + On-demand dev environments

---

## Features

- 🔧 **Language Picker** – Select from multiple programming languages (Python, Go, Rust, JS/TS, etc.)
- 🧠 **Custom Neovim Config** – Use [NvChad](https://github.com/NvChad/NvChad), [LazyVim](https://github.com/LazyVim/starter), [AstroNvim](https://github.com/AstroNvim/AstroNvim), [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim), or your own config (GitHub or local path)
- 🐋 **Docker-Based** – Reproducible environments with language servers and common dev tools
- 🧩 **LSP & Plugin Autoconfig** – Auto-generate Neovim config entries for selected languages
- 🔁 **Regenerable** – Rerun the tool any time to modify your dev stack

---

## Example Workflow

```bash
copier copy gh:Toita86/Forgeon ~/path/to/your/subproject
```

You’ll be asked:

* Which languages do you want to develop in?
* Which Neovim config would you like to use?
* Do you want to mount a local workspace?
* Would you like to include extra tools (tmux)?

Forgeon then generates:

* A `Dockerfile`
* Optional `docker-compose.yml`
* Custom Neovim configuration (if needed)
* Shell scripts or volume mappings for easy startup

---

## Supported Languages (so far)

* [x] Python (with `pyright`, `black`, `ruff`)
* [x] Node.js / TypeScript (`tsserver`, `eslint`)
* [x] Go (`gopls`, `goimports`)
* [x] Rust (`rust-analyzer`, `cargo`, `clippy`)
* [ ] Java (`jdtls`, `maven`)
* [ ] C/C++ (`clangd`, `cmake`, `make`)
* [ ] Lua (for Neovim plugin dev)

---

## Project Structure

```
Forgeon/

copier.yml
    └─ Copier configuration file. Defines template variables, prompts, defaults, and conditional logic.

.devcontainer/
    └─ Development container configuration (VS Code / devcontainer CLI).  
       This can be conditionally included or excluded based on user options.

docker-compose.yml.jinja
    └─ Template for the Docker Compose file.  
       Uses variables from copier.yml to customize services, volumes, and environment.

Dockerfile.jinja
    └─ Template for the main Dockerfile.  
       Adjusts installed tools, languages, and config depending on user choices.

.gitignore.jinja
    └─ Template for `.gitignore`.  
       Generates language-specific ignores depending on selected languages.

LICENSE
    └─ Project license (MIT by default, can be customized).

pre-commit-config.yaml.jinja
    └─ Jinja-templated version of the pre-commit config for customization at generation time.

README.md.jinja
    └─ README template for generated projects — can include details based on user selections.

requirements.txt
    └─ Python dependencies for the template (if any tools/scripts require them).
```

---

## Requirements

* Python 3.8+
* Docker
* `pip install -r requirements.txt` (for `copier` and `pre-commit`, if you already have no worries fo this step)

---

## Roadmap

* [x] Template using copier
* [x] Devcontainer integration
* [ ] Podman support
* [ ] Tmux with pre-configured session management

---

## Contributing

Contributions are welcome! Open issues, suggest features, or send PRs. You can also submit starter configs for Neovim.

---

## License

MIT License

