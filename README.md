# HYPERSCAN — learn to see in four dimensions

Two tiny browser games about building 4D intuition. No build, no dependencies —
each game is one self-contained HTML file.

## FIELDWORK (`fieldwork.html`) — a Miegakure-style 4D puzzle

You're a glowing agent in an isometric voxel world — except the world is a **4D
grid**, and you only see the 3D slice at your current W. Walls, floors, and
vaults have W-coordinates too: press Q/E to step *kata/ana* along the fourth
axis, and walk straight through where a wall used to be. Eight levels: walk
around a wall, rob a hermetically sealed vault, cross a bridge that only exists
one slice over, and finish in a maze spanning four slices. Faint colored
wireframes show what exists in the adjacent slices (orange = kata, cyan = ana).

Every level is verified solvable by a BFS solver that runs against the game's
own movement code (`FW.solve` in the page).

## HYPERSCAN (`index.html`) — the scanner

A shape from a higher dimension is passing through your world, and you see one
thin slice at a time.

**Premise:** a shape from a higher dimension is passing through your world. You
can only see one thin slice of it at a time. Scrub the scanner along the hidden
axis, watch how the slices change, and identify the shape.

- **Act I · Flatland** — warm-up. You're a 2D being; 3D objects (sphere, cube,
  cone, torus…) pass through your plane.
- **Act II · Spaceland** — the real thing. 4D objects (hypersphere, tesseract,
  hypercone, spherinder, duocylinder, 5-cell) pass through your 3D space.
  Point color encodes the W coordinate.
- **Act III · Tilted** — the same hyperobjects, rotated in 4D. Slices get weird.
- **Museum** — free-play after the game: slice any hyperobject, spin it in the
  XW/YW/ZW/XY planes, or switch to shadow view (4D→3D perspective projection).

## Run it

It's a single self-contained `index.html` — no build, no dependencies.
Open the file in a browser, or serve it:

```
python3 -m http.server
```

## How it works

Every shape is a point cloud sampled on its boundary (with extra samples on
2D faces and edges so cross-sections get crisp glowing outlines). Slicing is
a band filter on one coordinate; tilting is a 4D plane rotation; the shadow
view is a perspective divide by `w`. One renderer, ~1 KLOC, canvas 2D with
additive-blended glow sprites. Rendering quality adapts to frame rate;
append `?q=1` to force full density.

Controls: drag to orbit · scroll or drag the slider to scan · keys 1–4 answer.
