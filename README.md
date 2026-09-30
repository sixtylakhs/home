# SixtyLakhs home

Single-page site for SixtyLakhs, served by GitHub Pages at `sixtylakhs.ink`.

Plain HTML and CSS. No build step, no JavaScript, no web fonts, no external requests.

## Files

| Path | What it is |
|------|------------|
| `index.html` | The page. All copy lives here. |
| `styles.css` | All styling. Palette is in the `:root` custom properties. |
| `assets/logo.svg` | Logo mark (satellite tile, one yellow parcel, red marker). Used as favicon, nav and footer. |
| `404.html` | Page GitHub Pages serves for unknown paths. Uses root-absolute paths so it works at any depth. |
| `CNAME` | Custom domain for GitHub Pages (`sixtylakhs.ink`). |
| `robots.txt` | Allows all crawlers. |

## Preview locally

```sh
cd home
python3 -m http.server 8000
```

Open http://localhost:8000. Opening `index.html` directly from disk also works; `404.html` needs the server because it uses root-absolute paths.

## Deploy on GitHub Pages

1. Push to `main` on `github.com/sixtylakhs/home`.
2. On GitHub: repository **Settings → Pages**.
3. Under "Build and deployment", set **Source** to **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. Under "Custom domain", enter `sixtylakhs.ink` and **Save**. The `CNAME` file in this repo already holds the same value.

Docs: [Configuring a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## DNS for sixtylakhs.ink

Add the custom domain in Pages settings (step 4 above) **before** changing DNS. GitHub recommends [verifying the domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages) for the `sixtylakhs` organisation first, to prevent takeover.

At the registrar, remove any default records for the apex, then add:

| Type | Name | Value |
|------|------|-------|
| `A` | `@` | `185.199.108.153` |
| `A` | `@` | `185.199.109.153` |
| `A` | `@` | `185.199.110.153` |
| `A` | `@` | `185.199.111.153` |
| `AAAA` | `@` | `2606:50c0:8000::153` |
| `AAAA` | `@` | `2606:50c0:8001::153` |
| `AAAA` | `@` | `2606:50c0:8002::153` |
| `AAAA` | `@` | `2606:50c0:8003::153` |
| `CNAME` | `www` | `sixtylakhs.github.io` |

With both apex and `www` set, GitHub redirects `www.sixtylakhs.ink` to `sixtylakhs.ink`. Do not add wildcard (`*`) records.

Values checked against [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) on 2026-09-30. Re-check that page if anything fails.

Confirm propagation (can take up to 24 hours):

```sh
dig sixtylakhs.ink +noall +answer -t A
dig sixtylakhs.ink +noall +answer -t AAAA
dig www.sixtylakhs.ink +nostats +nocomments +nocmd
```

## HTTPS

Once DNS resolves, go back to **Settings → Pages** and tick **Enforce HTTPS**. The option can take up to 24 hours to become available after the domain is added.

## Contact

provider@sixtylakhs.ink · https://github.com/sixtylakhs
