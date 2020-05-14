<script>
  import { onMount } from "svelte";
  import marked from "marked";

  let markdown = "# Example Title\n\n- this\n- is\n- a list";

  onMount(async () => {
    let Editor = await import("@toast-ui/editor");
    const editor = new Editor.default({
      target: document.querySelector("#editor"),
      height: "500px",
      initialEditType: "markdown",
      previewStyle: "vertical"
    });
    editor.getHtml();
  });
</script>

<style>
  h1,
  figure,
  p {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  figure {
    margin: 0 0 1em 0;
  }

  img {
    width: 100%;
    max-width: 400px;
    margin: 0 0 1em 0;
  }

  p {
    margin: 1em auto;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }
</style>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>

<h1>Great success!</h1>

<figure>
  <img alt="Success Kid" src="successkid.jpg" />
  <figcaption>Have fun with Sapper!</figcaption>
</figure>
<textarea bind:value={markdown} placeholder="Enter markdown here" />
<div class="preview">
  {@html marked(markdown)}
</div>
<div id="editor">a</div>
<p>
  <strong>
    Try editing this file (src/routes/index.svelte) to test live reloading.
  </strong>
</p>
