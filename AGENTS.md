# AGENTS.md — uppidi-website

## What this is

Static marketing site for [Uppidi Upload](https://github.com/xpufx/uppidi-upload), a cross-platform file uploader
(Flutter/Dart, GPLv3). Sibling repo at `~/code/uppidi` (local clone).

## Key source of truth

The **uppidi source repo** (`~/code/uppidi`) has the canonical logo, screenshots, provider favicons, and BUILDING.md
content. Copy assets from there, do not recreate them.

- Logo: `assets/logo-light.png`, `assets/logo-dark.png` (500×500 PNG)
- Provider favicons: `assets/favicons/*.png`
- Screenshots: `docs/screenshots/*.jpg`
- Changelog / feature text: `README.md`, `CHANGELOG.md`, `docs/USER_MANUAL.md`

## Live site

Production: **https://uppidi.com** (GitHub Pages, custom domain).
Any push to `main` deploys immediately to production. Test via Caddy dev server first.

## Dev server

The site is served via Caddy at `http://10.20.30.24:81/`. Provide direct URLs (e.g.
`http://10.20.30.24:81/index.html`) when you want the user to click and view a page.

## Design constraints

- **No CSS/JS frameworks** — pure semantic HTML5 + minimal vanilla JS if needed
- **No CSS classes** — use element selectors only (`h1`, `p`, `ul`, `img`, etc.)
- **Water.css** is the CSS library (styles bare semantic HTML, no class selectors needed)
- **Static site** — must work on GitHub Pages or Cloudflare Pages, no build step
- **Multi-page** — `index.html`, `download.html`, `privacy.html` (+ future pages)

## Release info for download links

| Platform | Asset pattern | Example (v1.2.0+5) |
|---|---|---|
| Android (arm64) | `uppidi-upload-{version}-{hash}-android-arm64-v8a.apk` | `uppidi-upload-1.2.0+5-dfa02b8-android-arm64-v8a.apk` |
| Android (armv7) | `…-android-armeabi-v7a.apk` | |
| Android (x86_64) | `…-android-x86_64.apk` | |
| Linux (tar.gz) | `uppidi-upload-{version}-{hash}-linux.tar.gz` | |
| Linux (AppImage) | `uppidi-upload-{version}-{hash}-x86_64.AppImage` → changed to `.appimage` from v1.2.0+5 | |
| Windows (zip) | `uppidi-upload-{version}-{hash}-windows.zip` | (built by CI, upload as artifact) |

Base URL for downloads: `https://github.com/xpufx/uppidi-upload/releases/tag/v{version}`
Latest release API: `https://api.github.com/repos/xpufx/uppidi-upload/releases/latest`

**Version must be synced manually** — check `~/code/uppidi/pubspec.yaml` for current version string.

## Supported providers (9)

| ID | Display name | Favicon file |
|---|---|---|
| `catbox` | Catbox.moe | `catbox.png` |
| `fileditch` | FileDitch | `fileditch.png` |
| `frisk` | Frisk (1 day expiry) | `frisk.png` |
| `litterbox` | Litterbox (temporary) | `litterbox.png` |
| `uguu_uguu_se` | Uguu.se | `uguu_uguu_se.png` |
| `tmpfilelink` | TmpFile.link | `tmpfilelink.png` |
| `freeimage_freeimage_host` | FreeImage.host | `freeimage_freeimage_host.png` |
| `tempsh` | TempSH | `tempsh.png` |
| `httpbin` | HttpBin.org (test) | `httpbin.png` |

## Pages

| Page | Purpose |
|---|---|
| `index.html` | Hero, feature cards, screenshots, provider list, platform badges, GitHub link, footer |
| `download.html` | Per-platform download matrix with links to GitHub Releases + build-from-source |
| `privacy.html` | Privacy statement |

## Directory layout

```
assets/
├── logo-light.png
├── logo-dark.png
├── favicon.ico
├── screenshots/    (copied from ~/code/uppidi/docs/screenshots/)
└── provider-icons/ (copied from ~/code/uppidi/assets/favicons/)
```

## Content copy to extract from uppidi repo

- Feature descriptions → `README.md`, `docs/USER_MANUAL.md`
- Screenshots → copy `docs/screenshots/*.jpg`
- Provider info → `lib/core/registry.dart` (provider registry), `lib/providers/*.dart` (metadata)
- Build instructions → `BUILDING.md`
- Changelog → `CHANGELOG.md`
