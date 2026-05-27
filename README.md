# Cambridge Analytica Vault â€” Quartz Site

This repo builds and deploys the public Cambridge Analytica research vault as a navigable website with graph view, full-text search, and wikilink resolution.

- **Content source:** [`terry1818/cambridge-analytica-vault`](https://github.com/terry1818/cambridge-analytica-vault) (added as a git submodule at `content/`)
- **Static-site generator:** [Quartz v5](https://quartz.jzhao.xyz/)
- **Deployment:** GitHub Pages via Actions on every push to `main`
- **Live site:** https://terry1818.github.io/cambridge-analytica-vault-site/

## How it works

1. `content/` is a git submodule pointing at the vault repo
2. On push to `main`, GitHub Actions checks out with submodules, installs Node + Quartz plugins, builds the static site, and deploys to GitHub Pages
3. To pick up new vault commits: bump the submodule pointer here, push

```bash
# Update content to latest vault commit
git submodule update --remote content
git add content
git commit -m "Update vault content to latest"
git push
```

## Local development

Local builds on Windows have known PATH-inheritance issues. CI is the reliable build path. If you want to try local:

```bash
npm install --ignore-scripts
npx quartz plugin install
npx quartz build --serve
```

## Configuration

`quartz.config.yaml` is the customized config. See `quartz.config.default.yaml` for the full defaults to inherit from.

## License

Site framework: MIT (Quartz). Vault content: CC BY-SA 4.0 (see vault repo).