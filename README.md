# https://remarkable.guide
A guide for hacking your reMarkable tablet.

### Can I make changes?
Pull Requests and Issues are welcome! The site is built with [Sphinx](https://www.sphinx-doc.org) and images are generated with
[TikZ](https://www.overleaf.com/learn/latex/TikZ_package).

### How do I build the site?
You will need the following installed:
- build-essential
- graphviz
- libgraphviz-dev
- librsvg2-bin
- pdf2svg
- pipenv
- python
- texlive-base
- texlive-latex-extra

At which point in time you can build the site with `make`.

If you would like to have the site automatically update as you change files in [src](src), you can run `make dev`. This will open the build
of the site in your browser, and auto update the page when you make changes. If you would like to automatically update
[src/_static/images](src/_static/images) as you make changes to [images](images), you can run `make dev-images`.

### How do I add a page to the site?
Create a new `*.rst` file in [src](src).

### How do I add a link to a page to the sidebar?
Add it's name to [src/sitemap.rst](src/sitemap.rst).

### How do I add a picture to the site?
Adding an image to the site can be done by adding a `*.png.tex` or `*.svg.tex` file in [images](images), or adding the image itself to
[src/_static](src/_static). Please don't add them directly to [src/_static/images](src/_static/images) as this will be replaced
by images generated by [images](images) as part of the build process.

### Can I change the text in a header?
Yes, but you'll need to add a label using the previous text so that old hyperlinks will continue to work: `.. _previous-text:`. Make sure to test this as well.

### Can I rename a page?
Yes, you usually will want to accomplish this by just changing the first header on a page, but if you ever need to change the filename of the page, you will need to recreate the old page and have it redirect to the new page. This way links will continue to work.

```rst
This page has been moved to :doc:`new-page-name`.

.. raw:: html

  <noscript>
    <meta http-equiv="refresh" content="0; url=/new-page-name.html"/>
  </noscript>
  <script>
    location.pathname = "/new-page-name.html";
  </script>
```

### How to I add a warning to a page?
```rst
.. raw:: html

    <div class="warning">
        ⚠️ Warning title. ⚠️

Warning text.

.. raw:: html

    </div>
```

### How do I add screenshots to a page?
```rst
.. raw:: html

  <div class="gallery">
    <img src="/_static/path/to/file-1.png" alt="First screenshot" class="screenshot">
    <img src="/_static/path/to/file-2.png" alt="Second screenshot" class="screenshot">
  </div>
```

### How do I mark a page as a stub that needs further content written?
Ideally you don't add stub pages, but sometimes it's better to just add a page and throw a couple links on it for future completion.
```rst
.. raw:: html

    <div class="warning">
        ⚠️ FIXME. ⚠️

This page is just a stub that needs to be completed. You can `open a PR on the repo <https://github.com/Eeems-Org/remarkable.guide>`_ to add more content to the page.

.. raw:: html

    </div>
  ```
