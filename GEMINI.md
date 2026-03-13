# Gemini CLI Project Context: Academic Portfolio Website

This project is a personal academic and portfolio website built using **Jekyll** and the **AcademicPages** theme (a fork of **Minimal Mistakes**). It is designed to showcase publications, talks, teaching experience, and blog posts.

## 🚀 Purpose
To provide a structured, static website that hosts academic professional information, including:
- **Publications:** Research papers and articles.
- **Talks:** Presentations and tutorials.
- **Teaching:** Course information and materials.
- **CV/Resume:** Professional background.
- **Blog:** Personal or research-related updates.

## 🛠️ Technical Stack
- **Static Site Generator:** Jekyll (Ruby)
- **Templating:** Liquid
- **Styling:** SASS (compiled from `_sass/`)
- **Scripting:** Python & Jupyter Notebooks (for content generation)
- **Deployment:** Typically hosted via GitHub Pages.

## 📁 Key Project Structure

### Content & Data
- `_publications/`: Markdown files for individual research papers.
- `_talks/`: Markdown files for presentations and tutorials.
- `_teaching/`: Markdown files for courses taught.
- `_posts/`: Markdown files for blog posts.
- `_pages/`: Static Markdown/HTML pages (e.g., `about.md`, `cv.md`, `publications.md`).
- `_data/`: Configuration data:
    - `navigation.yml`: Defines the main navigation menu.
    - `authors.yml`: Author profile information.
    - `ui-text.yml`: Localized UI strings.
- `files/`: PDFs of publications and other downloadable documents.
- `images/`: Profile pictures, logos, and images for posts/pages.

### Layouts & Includes
- `_layouts/`: Page templates (e.g., `single.html`, `talk.html`, `archive.html`).
- `_includes/`: Reusable HTML fragments (e.g., `head.html`, `footer.html`, `author-profile.html`).

### Styling & Assets
- `_sass/`: SCSS source files for the site's design.
- `assets/`: Static assets including CSS, JavaScript, and fonts.

### Content Generation
- `markdown_generator/`: Contains Python scripts (`.py`) and Jupyter notebooks (`.ipynb`) that automate the creation of Markdown files in `_publications/` and `_talks/` from bibliography files (`.bib`) or TSV data (`.tsv`).
- **Conda Environment:** A minimal conda environment `academic-pages` is used to run these scripts (requires `pybtex` and `pandas`).
    - Run scripts using: `/Users/ymagen/miniconda3/envs/academic-pages/bin/python markdown_generator/pubsFromBib.py`

## ⚙️ Configuration
- `_config.yml`: **Central configuration file.** Contains site title, author details, SEO settings, and collection definitions. This is the first place to look when modifying site-wide behavior.

## 📝 Workflow for LLM Agents

### 1. Adding a Publication/Talk
- **Manual:** Create a new Markdown file in `_publications/` or `_talks/` following the existing naming convention (e.g., `YYYY-MM-DD-title-slug.md`).
- **Automated:** Use scripts in `markdown_generator/` if you have a BibTeX or TSV source.

### 2. Updating Navigation
- Modify `_data/navigation.yml` to add or remove links from the top menu.

### 3. Modifying the Author Profile
- Most author information is stored in `_config.yml` under the `author` key. Some themes might also use `_data/authors.yml`.

### 4. Running Locally
- Run `bundle exec jekyll serve` or `bundle exec jekyll liveserve` to preview changes locally.

### 5. Styling Changes
- Modify the corresponding SCSS file in `_sass/`. The entry point is `assets/css/main.scss`.

## ⚠️ Important Considerations
- **Front Matter:** Every page and collection item (post, publication, etc.) uses YAML front matter between `---` markers. Ensure this is preserved and correctly formatted.
- **Permalinks:** Permalinks are often explicitly defined in the front matter to ensure stable URLs.
- **Relative Paths:** Use `{{ site.baseurl }}` or the `relative_url` filter when linking to assets or other pages to ensure compatibility with different base URLs.
