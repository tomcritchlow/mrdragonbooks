# Mr. Dragon Books

Jonah Dragan's website: **https://mrdragonbooks.com/**

- `/` is the homepage, hand-written in `index.html` (plus `jonah.webp`
  and the favicons). The cover strip links to eight posts in the archive.
- `/1000/` is the archive of [@jonahdragan](https://www.instagram.com/jonahdragan/)'s
  Instagram project, 1,000 picture book reviews in 1,000 days (July 2020 –
  April 2023). It was originally generated from an Instagram data export:
  1,001 posts and 9,314 images, resized to 900px WebP. It has an image-grid
  index, an author & illustrator index, and client-side search.

Served by GitHub Pages from `main` at `/`, with the custom domain in
`CNAME` and `.nojekyll` set. DNS is on Cloudflare (DNS-only records
pointing at GitHub Pages). The site is ~955 MB against Pages' 1 GB limit,
so there's little room for more images.

## Building the archive

`data/posts.json` is the source of truth for every post (date, images,
caption, book metadata). To rebuild the archive after editing it:

    pip install Pillow
    python3 build.py

This regenerates `1000/index.html`, `1000/people.html`, `1000/posts/*.html`
and `1000/search-data.js`, and creates any missing 300px grid thumbnails
in `1000/media/thumb/`. The hand-written archive files are
`1000/style.css`, `1000/search.js` and `1000/post.js`.

`tools/extract.py` is how `data/posts.json` was first recovered from the
generated HTML; it shouldn't need running again.
