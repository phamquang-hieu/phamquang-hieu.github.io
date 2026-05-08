# phamquang-hieu.github.io

Personal site built with [Hugo](https://gohugo.io/) and the `enchanted-lowkey` theme. Deployed to GitHub Pages via `.github/workflows/hugo.yaml`.

## Prerequisites

Versions match the GitHub Actions deploy workflow:

- Hugo extended **0.110.0**
- Dart Sass **1.x**
- Node.js **22.x** + npm

### macOS install

```sh
# Dart Sass via Homebrew
brew install dart-sass

# Node.js 22 (skip if already installed)
brew install node@22

# Hugo extended 0.110.0 (Homebrew only ships latest, so download the pinned binary)
mkdir -p ~/.local/bin
curl -sL https://github.com/gohugoio/hugo/releases/download/v0.110.0/hugo_extended_0.110.0_darwin-universal.tar.gz \
  | tar -xz -C ~/.local/bin hugo
chmod +x ~/.local/bin/hugo

# Make sure ~/.local/bin is on your PATH
export PATH="$HOME/.local/bin:$PATH"
hugo version  # should print v0.110.0+extended
```

For Linux, swap the Hugo download URL to `hugo_extended_0.110.0_linux-amd64.tar.gz` (or the matching arch).

### Install Node dependencies

```sh
npm ci
```

## Local development

Run the dev server with live reload:

```sh
hugo server
```

Then open http://localhost:1313.

## Production build

```sh
hugo --gc --minify
```

Output goes to `./public`. CI runs the same command with `--baseURL` set to the Pages URL.

## Project layout

- `content/` — site content (posts, CV, taxonomies)
- `config/_default/` — Hugo config (`hugo.toml`, `menus.toml`, `params.toml`)
- `themes/enchanted-lowkey/` — vendored theme
- `static/` — files served as-is
- `.github/workflows/hugo.yaml` — GitHub Pages deploy
