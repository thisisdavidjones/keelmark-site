# Keelmark website

This repository contains the public website for **Keelmark**, a small app publisher focused on practical Android apps for everyday routines.

The site is built with [Hugo](https://gohugo.io/) using the [Hextra](https://imfing.github.io/hextra/) theme, with custom content, styling, branding assets, and product pages for Keelmark apps.

## Site

Production site:

```text
https://keelmark.co.uk/
```

## Products

### Dosewise

**Dosewise** is a medication schedule tracker for Android.

It is designed to help users record medication doses, check timing, and keep a clear dose history. Dosewise is not medical advice and does not replace instructions from a clinician, pharmacist, or medicine label.

## Local development

Install Hugo Extended and Git.

Then clone the repository:

```powershell
git clone https://github.com/thisisdavidjones/<repo-name>.git
cd <repo-name>
```

Fetch the Hextra module:

```powershell
hugo mod get github.com/imfing/hextra
```

Run the local development server:

```powershell
hugo server --disableFastRender
```

The site will normally be available at:

```text
http://localhost:1313/
```

## Repository structure

```text
.
├── assets/
│   └── css/
│       └── custom.css
├── content/
│   ├── _index.md
│   ├── about.md
│   ├── contact.md
│   ├── privacy.md
│   └── products/
│       ├── _index.md
│       └── dosewise.md
├── layouts/
│   ├── _default/
│   │   ├── list.html
│   │   └── single.html
│   ├── _partials/
│   │   └── custom/
│   │       ├── footer.html
│   │       └── head-end.html
│   └── index.html
├── static/
│   ├── assets/
│   │   ├── dosewise/
│   │   └── keelmark/
│   ├── favicon.ico
│   └── site.webmanifest
├── hugo.yaml
└── go.mod
```

## Cleaning generated files

If Hugo appears to be using stale CSS, images, or generated resources, clear the generated output and restart the server:

```powershell
Remove-Item -Recurse -Force public, resources/_gen -ErrorAction SilentlyContinue
hugo server --disableFastRender
```

On macOS or Linux:

```bash
rm -rf public resources/_gen
hugo server --disableFastRender
```

## Configuration notes

The site uses `hugo.yaml`.

Important settings include:

```yaml
baseURL: "https://keelmark.co.uk/"
languageCode: "en-gb"
title: "Keelmark"

module:
  imports:
    - path: github.com/imfing/hextra

markup:
  goldmark:
    renderer:
      unsafe: true
```

Raw HTML is used inside some Markdown content pages to support the custom landing-page layout, so `markup.goldmark.renderer.unsafe` must remain enabled.

## Branding

Keelmark assets are stored under:

```text
static/assets/keelmark/
```

Dosewise assets are stored under:

```text
static/assets/dosewise/
```

The site uses Keelmark as the parent brand and Dosewise as the product brand.

## Custom styling

Most custom visual behaviour is handled in:

```text
assets/css/custom.css
```

This includes the homepage hero, responsive navigation, mobile menu behaviour, light/dark theme toggle styling, product cards, footer styling, Dosewise image sizing, and interior page layout.

## Deployment

The site is intended to be deployed as a static Hugo site through GitHub Pages.

A typical build command is:

```bash
hugo --minify
```

The generated site is written to:

```text
public/
```

Do not edit files in `public/` directly. They are generated output.

## Domain

The production domain is:

```text
keelmark.co.uk
```

If using GitHub Pages, keep the repository/domain configuration aligned with the `baseURL` value in `hugo.yaml`.

## License

Copyright © Keelmark.

All brand assets, logos, product names, and site content are owned by Keelmark unless otherwise stated.
::: 
