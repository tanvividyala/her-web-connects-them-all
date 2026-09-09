# Her Web Connects Them All

A little tool I made for myself to help me visualize groups of people, ideas, and concepts I find interesting.

Type a bulleted outline of who (or what) connects to what, and watch it turn into a living, force-directed web you can drag, group, and label. No build step, no backend — it's a single self-contained HTML file that runs entirely in the browser.

## Why

I wanted a fast, private way to sketch out the web of relationships around a person, a project, or an idea — friends of friends, overlapping communities, related concepts — without spinning up a whiteboard tool or a graph database. This does it in one tab, saves itself locally, and never leaves your machine.

## How it works

There are two ways to build a graph, and they stay in sync:

### Outline view
Write a plain-text bulleted outline:

```
- Thing 1
  - Thing 2 (Boyfriend)
  - Thing 3 (Roommate)
- Thing 2
  - Thing 1 (Girlfriend)
  - Thing 4 (Climbing gym)

= Study crew
  - Thing 3
  - Thing 5
```

- A top-level `-` or `*` is a node — a person, idea, or place.
- Indenting a line under a node draws a connection to it.
- `Thing (Label)` names the relationship on that connection.
- `= Group name` with nodes indented underneath draws a colored region (a "hull") around them.
- **Enter** continues a bullet, **Tab** nests it deeper.

### Visual view
Build the same graph directly on the canvas:

- **+ Add node** or double-click empty canvas to drop a node.
- Drag a node's ring onto another node to connect them.
- Shift-click three or more nodes to name them as a group.
- The **Palette** and **Groups** lists let you review and manage what's on the canvas.

Both views edit the same underlying graph, so you can jot down structure as an outline and then rearrange it visually, or vice versa.

## Graph behavior

- Built with [D3.js](https://d3js.org/) force simulation — nodes repel each other, links pull connected nodes together, and everything settles into a readable layout automatically.
- Node size scales with degree (how many connections it has).
- Groups render as soft, colored hulls behind their member nodes.
- **Recenter** re-fits the whole graph to the visible canvas.
- **Export PNG** saves a snapshot of the current layout as an image.

## Saving your work

- Your outline and current graph are saved automatically to the browser's `localStorage`, so refreshing the page won't lose your work.
- The **Gallery** panel lets you save named snapshots of a graph and reload them later, so you can keep multiple webs (e.g. different friend groups, different projects) side by side.

Everything is stored locally in your browser — nothing is sent to a server.

## Running it

There's nothing to install. Open [index.html](index.html) directly in a browser, or serve the folder with any static file server:

```
python3 -m http.server
```

then visit `http://localhost:8000`.
