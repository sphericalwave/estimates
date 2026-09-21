# sphericalwave estimates

Customer estimates, hosted on GitHub Pages as the `sphericalwave/estimates`
repo. Because the user site (`sphericalwave.github.io`) owns the custom domain
sphericalwave.com, this repo is served under it automatically:

`https://sphericalwave.com/estimates/<job>/`

- `<job>/index.html` — one folder per estimate, at the repo root (the repo name already supplies `/estimates/`)
- `assets/` — sphericalwave ring graphics (single, pair, triad, square–nonagon)

## Styling

Pages link the live site stylesheet (`https://sphericalwave.com/styles.css`),
Bootstrap and the site fonts, and use the site's `sw-home__*` components. A
change to the main site's CSS changes every estimate too. Only
estimate-specific pieces (cost table, schedule, print rules) live inline.

Customers can save or print a PDF with the "Save as PDF" button, which opens
the browser print dialog. Print CSS switches to black on white.

## Publish (first time)

```bash
cd sphericalwave-estimates
git init -b main && git add . && git commit -m "Bow Street deck estimate"
gh repo create sphericalwave/estimates --public --source=. --push
gh api -X POST repos/sphericalwave/estimates/pages -f "source[branch]=main" -f "source[path]=/"
```

## Privacy

Estimate pages carry `noindex`, but anyone with the link can open them, and a
public repo exposes the source. `robots.txt` here is not at the domain root, so
it has no effect under sphericalwave.com; `noindex` is what keeps pages out of
search.
