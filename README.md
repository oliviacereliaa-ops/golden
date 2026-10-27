# Kawan Lama Manufacturing — Factory Explorer

A self-contained static webpage for GitHub Pages. No npm install, API key, backend, CDN or build step is required. The supplied logo is embedded. Open index.html in a modern browser to try it locally.

## Interactions

- Three states: 2025 & Before (early 2025 reference), Now, and 2027 Plan.
- Building selection animates the camera and fades the roof to reveal zones.
- Drag to rotate, scroll or use +/- to zoom, and reset to return to campus.
- Only Now allows Home Textile, Safety Shoe, Spring, Sofa, and Multiline to open a half-width presentation panel. Small screens use a full-width panel.
- Overview, Capabilities, Growth, and Projects panels are intentionally empty content templates.
- 2025 & Before uses a factory-wide sidebar with Capabilities, Expansion and Growth tabs. Active areas in B/C are teal; A is unused and grey, D/E are grey with historical use unspecified. Segment popups and building zoom are disabled in this view.
- 2027 is a layout comparison. Building exploration remains available, but segment panels are disabled.
- Escape closes the panel or returns to campus. Reduced-motion preference is respected.

## Publish on GitHub Pages

1. Extract this ZIP.
2. Upload index.html and .nojekyll to the root of your chosen GitHub repository. README.md is optional.
3. In the repository Settings → Pages, choose Deploy from a branch, choose your branch, and choose /(root).
4. Save. Open the Pages URL provided by GitHub once deployment completes.

This delivery has NOT been uploaded or deployed to GitHub. A repository destination and access are required to do that.

## Add content later

Open index.html and find `const SEGMENTS` near the beginning of its script. Each of the five entries contains `overview`, `capabilities`, `growth`, and `projects`. Replace null with an object such as:

    overview: { title: 'Your headline', body: 'Your presentation text.' }

Factory-wide history is rendered by `renderHistory()`. Product capabilities come from COPY OLIVE.pptx (2022–2025), stored in `CAPABILITY_HISTORY`. Annual revenue, targets, achievement and YoY growth come from the supplied historical revenue image (2021–2025). The overall +175.6% growth and 2.76× multiple are calculated from 153.5 and 423.0. The spatial map remains an early-2025 snapshot, distinct from capability additions throughout 2025.

The entry quiz asks “What is our 2027 target?” and accepts `630`. It is a client-side presentation gate only: the answer and content are inspectable in the page source, so it does not protect confidential information.

The rendering uses textContent so text is treated as text, not executable markup. More detailed charts, images and KPI layouts can be added in a subsequent version.

## Layout assumptions to resolve

- A/C labels are swapped to match the user’s correction and satellite: A = upper Home Textile / unused building, B = middle Multiline / GSSI, C = Sofa / Spring. Geometry and allocations remain in place.
- GSSI is provisionally treated as Safety Shoe. Confirm before presenting as a verified allocation.
- D = Woodworking and E = Foam Production in the 2027 view are provisional associations with the two existing small buildings. The physical footprints follow the marked satellite arrangement, not the positions of the two side boxes in the schematic.
- The 2025 & Before button represents the supplied early-2025 snapshot; it is not evidence for every prior year.
- D/E usage before the current snapshot was not supplied; both are displayed neutrally as Future use.
- Building dimensions, furniture and machinery are illustrative, not measured engineering geometry.
- Historical HT relocation and current/future zones follow the supplied plans. Performance data is sourced from the supplied chart. The chart headline references a 2027 GD–GLI target of Rp575 billion; it is not substituted for the separately requested quiz answer of 630.

## Implementation

Lightweight canvas-rendered 3D geometry with orthographic projection, animated camera and roof transparency, and accessible HTML navigation. No external runtime dependencies. This is an initial interaction prototype, not a CAD model or an exact reproduction of the concept renders.

## Validation

JavaScript syntax checked with Node. Browser checked: campus rendering, Building A zoom/X-ray, Sofa panel open/close, Growth tab, factory-wide historical Capabilities, Expansion and Growth tabs, quiz rejection and acceptance, and disabled segment controls in the 2027 view. Other segment panels use the same shared handler. Mobile layout is implemented but has not been separately device-tested.
