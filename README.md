# Rohun Agrawal — personal website

A responsive, dependency-free static research website. HTML and CSS replace the former Jekyll/al-folio theme.

## Local preview

Run from the repository root:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open http://localhost:8000. No installation or build step is needed.

## Editing

- `index.html`: biography, publications, and profile links.
- `styles.css`: layout, colors, typography, and responsive styles.
- `homepage-content.md`: original homepage content preserved before the redesign.
- `content/papers.bib`: original publication metadata, retained for reference.
- `assets/img/`: original portraits, optimized display portrait, and publication figures.
- `assets/pdf/`: retained personal PDFs.
- `assets/fonts/`: self-hosted Open Sans fonts and their Open Font License.

The HTML is the website source; Markdown and BibTeX are reference copies and are not automatically rendered. Keep them in sync when updating research content.

The workflow in `.github/workflows/pages.yml` publishes the static website to GitHub Pages on each push to `main`. It packages the HTML, CSS, robots file, and public assets; the private CV source submodule is not checked out or published.

Live site: https://rohunagrawal.github.io/

## CV source

The `cv/` Git submodule points to `rohunagrawal/Rohun-Agrawal-CV`. Initialize it after cloning this website repository:

```sh
git submodule update --init cv
```

Edit `cv/main.tex`, then rebuild the website's CV download with a local LaTeX installation:

```sh
latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=/tmp/rohun-cv-build cv/main.tex
cp /tmp/rohun-cv-build/main.pdf assets/pdf/Rohun_Agrawal_CV.pdf
```

Commit CV source changes within the submodule and update its recorded revision in this repository when saving changes to Git.
