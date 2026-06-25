# BPM Curriculum Review Tool

**University of Sydney — School of Project Management**
2026 Curriculum Review

A self-contained interactive HTML tool for mapping Bachelor of Project Management (BPM) units across Knowledge Hubs, analysing Program Learning Outcome (PLO) coverage, and proposing curriculum changes collaboratively.

---

## Live Tool

The tool is available at:

```
https://usydsopm.github.io/knowledge-hubs/BPM_Curriculum_Review_Tool.html
```

---

## What the Tool Does

### 🪣 Hub Map
Displays all BPM units organised into five Knowledge Hub "buckets":

- Project Foundations, Planning, Delivery & Controls
- Leadership, Stakeholders & Governance
- Finance, Procurement, Risk & Analytics / Systems Thinking
- Innovation & Sustainability
- Professional Practice & Capstone

Each unit card shows its level (1000/2000/3000), type (Core/Elective), semester availability, and which Program Learning Outcomes (PLOs) it addresses — colour-coded by assessment type (open vs secured).

**Filters** let you show/hide by unit type, semester, level, PLO, and assessment type.

**Propose a hub change** — click the button, select your name, then drag and drop a unit card into a different bucket. Proposals are saved to `proposals.json` in this repository and visible to all users in real time.

### 🎯 PLO Coverage
Shows how the program collectively addresses each of the 8 Program Learning Outcomes. A heat-map gradient bar indicates coverage strength. Toggle Core/Elective and Open/Secured assessment filters to explore different views.

### ⚗️ Scenario Planner
Simulate curriculum changes — remove units, add hypothetical new ones — and see the live impact on PLO coverage. A side-by-side comparison chart shows current vs proposed coverage with heat-map gradient bars. Export a snapshot as an image for sharing.

---

## Files in This Repository

| File | Purpose |
|------|---------|
| `BPM_Curriculum_Review_Tool.html` | The entire tool — a single self-contained HTML file |
| `proposals.json` | Stores all hub change proposals submitted by academics. Do not delete. |
| `README.md` | This file |

---

## How to Update the Tool

Whenever a new version of the HTML file is provided:

1. Go to the repository on GitHub
2. Click on `BPM_Curriculum_Review_Tool.html`
3. Click the **pencil (edit) icon**
4. Select all the existing content and replace it with the new file contents
5. Click **Commit changes**

GitHub Pages will automatically redeploy within about 60 seconds. The `proposals.json` file is unaffected by HTML updates.

---

## GitHub Sync — How It Works

Hub change proposals are saved to `proposals.json` in this repository using the GitHub Contents API. This means:

- All users see the same proposals in real time
- Every save creates a git commit — there is a full history of every proposal ever made
- No external services or accounts are needed beyond GitHub

### Configuration

The connection credentials are baked directly into the HTML file. Near the top of the `<script>` section:

```js
const GH_OWNER  = 'usydsopm';
const GH_REPO   = 'knowledge-hubs';
const GH_TOKEN  = 'github_pat_...';
```

**The token** is a GitHub Fine-Grained Personal Access Token with **Contents: Read and write** permission scoped to this repository only. It cannot access anything else on GitHub.

### Token Expiry

Tokens can be set to expire. If the tool stops saving proposals, the token may have expired. To renew:

1. Go to **github.com → Settings → Developer settings → Personal access tokens → Fine-grained tokens**
2. Generate a new token with the same settings
3. Update the `GH_TOKEN` constant in the HTML file and re-upload it

---

## Fonts

The tool uses two licensed University of Sydney fonts:

- **Apercu Pro** — body text
- **Lyon Display** — headings

These fonts are declared in the CSS but require the actual font files to render. To activate them:

1. Obtain the `.woff2` font files from USyd Brand Assets (contact the University's Marketing and Communications team)
2. Create a `/fonts/` folder in this repository
3. Upload the font files
4. Open `BPM_Curriculum_Review_Tool.html`, find the `@font-face` comment block near the top, and uncomment it

Until the fonts are added, the tool falls back to Helvetica Neue (body) and Georgia (headings).

---

## Contact

For questions about this tool, contact the School of Project Management:
**project.management@sydney.edu.au**
