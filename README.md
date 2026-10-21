# HTML — ADVANCED

## 10. Advanced forms

Advanced controls express more precise constraints and relationships.

**Syntax**

```html
<fieldset>
  <legend>Delivery</legend>
  <label for="city">City</label>
  <input id="city" name="city" list="cities" minlength="2" maxlength="40" required>
  <datalist id="cities"><option value="London"></option><option value="Tokyo"></option></datalist>
  <label for="quantity">Quantity</label>
  <input id="quantity" name="quantity" type="number" min="1" max="10" step="1">
  <label for="notes">Notes</label><textarea id="notes" name="notes"></textarea>
  <label for="size">Size</label>
  <select id="size" name="size"><optgroup label="Popular"><option>M</option></optgroup></select>
  <output name="total" for="quantity">0</output>
  <meter min="0" max="100" value="70">70%</meter>
  <progress max="100" value="45">45%</progress>
</fieldset>
```

**Example:** Checkout groups delivery fields, constrains quantity, offers city suggestions, and shows progress through a multi-step process.

**Use / do not use:** Use native validation as a helpful first line, but validate again on the server. Use `autocomplete` tokens when they describe the field. Do not use `pattern` when a dedicated input type is clearer.

**Write yourself:** Build a registration form with grouped account/profile fields, a datalist, select options, constraints, a password pattern, a progress indicator, and an output value. Explain which checks must still happen on the server.

## 11. Semantic HTML properly

`header`, `nav`, `main`, `section`, `article`, `aside`, and `footer` are structural landmarks with different meanings.

**Syntax**

```html
<main>
  <article>
    <header><h1>Post title</h1></header>
    <section><h2>Background</h2><p>...</p></section>
    <aside aria-label="Related links">...</aside>
    <footer>Published by ...</footer>
  </article>
</main>
```

**Example:** A news article is an independent `article`; related content is an `aside`; a thematic group with its own heading is a `section`.

**Use / do not use:** Use `section` when there is a meaningful theme and heading. Do not choose elements based only on default styling or use multiple `main` elements in one document.

**Write yourself:** Convert a page made entirely from `div`s into semantic markup and justify each replacement.

## 12. Multimedia

Media elements expose native controls and can provide alternate sources and captions.

**Syntax**

```html
<video controls poster="poster.jpg" width="640">
  <source src="lesson.webm" type="video/webm">
  <source src="lesson.mp4" type="video/mp4">
  <track kind="captions" src="captions.vtt" srclang="en" label="English" default>
</video>
<audio controls><source src="episode.mp3" type="audio/mpeg"></audio>
```

**Example:** A course video uses a poster, captions, and two formats for browser compatibility.

**Use / do not use:** Use `muted` when autoplay is truly necessary and provide controls. Avoid unexpected autoplay, especially with sound. Never omit captions for spoken video.

**Write yourself:** Add a video with poster, two sources, captions, fallback text, and an audio player with a transcript link.

## 13. Embedding

`iframe` embeds another browsing context; `embed` and `object` are legacy-compatible embedding mechanisms for external resources.

**Syntax**

```html
<iframe
  src="https://example.com/widget"
  title="Example widget"
  sandbox="allow-scripts"
  loading="lazy"></iframe>
```

**Example:** A map is embedded only from a trusted provider and given a useful title.

**Use / do not use:** Use an iframe when isolation or a third-party document is required. Prefer `sandbox`, restrictive permissions, trusted origins, and `referrerpolicy`. Do not embed untrusted user content without a threat model.

**Write yourself:** Add a sandboxed iframe and write down which capabilities you intentionally allow and why. Do not use a real sensitive service.

## 14. Metadata

Metadata helps browsers, search engines, and social platforms interpret a document.

**Syntax**

```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="description" content="A concise description of this page.">
<link rel="icon" href="/favicon.svg">
<meta property="og:title" content="Page title">
<meta property="og:description" content="Share description">
<meta property="og:type" content="website">
<title>Page title</title>
```

**Example:** A recipe page has a unique title and description and shares a useful preview on social media.

**Use / do not use:** Use accurate descriptions and one meaningful title per page. Treat `keywords` as historical and low-value; do not stuff metadata with repeated terms. Add a canonical URL when duplicate URLs are possible.

**Write yourself:** Write metadata for a local event page, including title, description, viewport, favicon link, and Open Graph fields. Explain which values are visible to users.

## 15. Accessibility

Accessibility makes content and controls usable with different abilities, devices, and input methods.

**Syntax**

```html
<label for="search">Search articles</label>
<input id="search" aria-describedby="search-help">
<p id="search-help">Use a topic or author name.</p>
<button type="button" aria-label="Close menu">×</button>
```

**Example:** A form has a visible label and help text; a close icon has an accessible name.

**Use / do not use:** Prefer semantic HTML and keyboard-operable native controls. Use ARIA to fill a genuine semantic gap, not to repair incorrect HTML. Do not hide meaningful content with `aria-hidden="true"` or make a non-button clickable with a click handler alone.

**Write yourself:** Audit one page with keyboard-only navigation. Fix missing labels, poor focus order, ambiguous link text, and inappropriate ARIA. Record each change and its reason.

## 16. HTML entities

Entities represent reserved characters or characters that are difficult to type.

**Syntax**

```html
&lt;code&gt; &amp; &quot;quoted&quot; &copy; 2026
```

**Example:** Documentation displays `<button>` as text using `&lt;button&gt;`.

**Use / do not use:** Use entities when text would otherwise be parsed as markup or when a named entity improves clarity. Do not use entities to conceal unsafe user HTML; escaping must be handled correctly by the rendering context.

**Write yourself:** Create a cheat sheet that displays five literal HTML tags and includes copyright and quotation marks.

## 17. Global attributes

Global attributes work on many elements.

**Syntax**

```html
<html lang="en" dir="ltr">
<section id="intro" class="card" title="Introduction" data-topic="html">
  <p contenteditable="true" spellcheck="true" tabindex="0">Editable note</p>
</section>
```

**Example:** `data-product-id` lets JavaScript identify a product without changing its visible text.

**Use / do not use:** Use stable `id`s for labels and fragment links, classes for styling, `hidden` for currently unavailable content, and `data-*` for custom data. Use positive `tabindex` values almost never; prefer natural document order.

**Write yourself:** Mark up a product card using `id`, `class`, `data-*`, `lang`, `dir`, `hidden`, and `spellcheck`. Explain which attributes should not be used for styling or focus hacks.

## ADVANCED checkpoint

Before starting EXPERT, explain:

- Native validation versus server validation.
- The semantic difference between `section`, `article`, and `aside`.
- Why autoplay can harm users.
- What an iframe sandbox protects and what it does not.
- Why native controls are usually better than custom ARIA widgets.

## ADVANCED project

Build an accessible **event registration page** in `projects/advanced-event/`. Include metadata, semantic regions, a validated form with fieldsets, a schedule table, a promotional video with captions, a safe map/widget iframe, and a keyboard-accessibility audit note.
