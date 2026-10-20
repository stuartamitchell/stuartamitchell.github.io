# Academic website of Stuart Mitchell

A single-page site in the style of hkvinge.github.io. Plain HTML + CSS, no build step.

## Files

```
index.html      the whole page
css/main.css    styling
photo.jpg       headshot, 420×480, shown as an oval beside the name
cv.pdf          the public (website) version of the CV
papers/         (optional) PDFs you host yourself; none needed at the moment
```


## Email address and spam protection

The email in the header is assembled by a short script at the bottom of `index.html`. The page
source contains only the two halves of the address, stored backwards:

```html
<span id="email" data-u="llehctim.trauts" data-d="ua.ude.una">
```

Visitors see a normal clickable `stuart.mitchell@anu.edu.au` link. Visitors without JavaScript
see `stuart.mitchell [at] anu [dot] edu [dot] au`. There is no at-sign or mail link in the HTML
for harvesters to find.

**To change the address:** reverse the part before the `@` into `data-u` and the part after it
into `data-d` (e.g. in a terminal: `echo stuart.mitchell | rev`), and update the fallback text.

## The CV

There are two versions of the CV, built from separate LaTeX files with the `moderncv` class:

| | Professional (`Stuart_Mitchell_CV.tex`) | Website (`Stuart_Mitchell_CV_web.tex`) |
|---|---|---|
| Contact details | Home address, phones, ANU email | ANU email only |
| PhD supervisor | Listed under Referees | Shown on the PhD entry |
| Master's thesis title | — | Yes |
| Publications | Yes | Yes |
| Referees | Full contact details | Not included |
| Use for | Job applications | `cv.pdf` on this site |

Only the website version belongs in this repository. Keep the professional version, and its
referees' contact details, off the public site.

**To update `cv.pdf`:** edit `Stuart_Mitchell_CV_web.tex`, compile it (pdfLaTeX, or upload to
Overleaf), and replace `cv.pdf` here with the result, keeping the same filename. If you add a
publication, add it to both CVs and to `index.html`.

## Publishing on GitHub Pages

1. Create a **public** repository named exactly `stuartamitchell.github.io`.
2. Upload the contents of this folder (not the folder itself) to the repository root.
3. Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. After a minute the site is live at `https://stuartamitchell.github.io`.

Every later commit to `main` updates the site automatically. Filenames are case-sensitive on
GitHub Pages (`photo.jpg` and `Photo.JPG` are different files).

## Adding things

- **A paper:** copy a `<div class="pub"> … </div>` block, edit it, and put it under the right
  year heading (add a new `<h3>2027</h3>` when needed, newest year first). The 2019 journal
  paper and the 2017 FPSAC extended abstract are already listed.
- **Extra buttons** (slides, code, published version): add another
  `<a href="…" class="btn btn-default">Label</a>` inside the entry's `btn-group`.
- **Maths:** `$\mathcal{H}$`-style inline LaTeX works anywhere on the page via MathJax.
- **Teaching:** uncomment the Teaching block near the bottom of `index.html` and the matching
  sidebar link.
- **New photo:** replace `photo.jpg`, keeping the name. A head-and-shoulders crop at roughly a
  7:8 width-to-height ratio fits the oval best. Strip location metadata before uploading.
