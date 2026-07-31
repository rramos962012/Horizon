[README (1).md](https://github.com/user-attachments/files/30599026/README.1.md)
# Horizon — Goal &amp; Roadmap System

A single-file, capture-first roadmap for everything you want to build, earn, or achieve. Dump a goal in seconds; it stays **inactive** in the Inbox until you give it a **horizon** — then it joins your roadmap.

No accounts, no server, no build step. It's one `index.html` file that runs in any browser.

---

## The idea in one line

**Capture first, schedule later.** You should be able to offload a cert, project, or business idea the moment it occurs to you — without deciding *when* right then. Horizon keeps those two acts separate.

- **Capture** → the goal lands in the **Inbox**, marked `INACTIVE`. It's saved, but not on your roadmap yet.
- **Activate** → tap a horizon (`Now`, `6 mo`, `3 yr`, `Later`) and it moves onto the roadmap. Assigning a horizon *is* the act of scheduling it.

---

## Daily use

1. **Dump a goal.** Type into the box at the top and press Enter (or "Add to Inbox"). Do this freely — it all goes to the Inbox as inactive.
2. **Activate when ready.** On any Inbox item, tap `Now / 6mo / 3yr / Later` to put it on the roadmap. Change your mind anytime by tapping a different horizon.
3. **Add detail.** Click a goal to open it. Set its **type** (Cert / Project / Business / Skill / Habit / Goal), write **notes**, break it into **milestones**, and optionally add **start / target dates**.
4. **Track progress.** Check milestones off — the progress bar, the counts, and the big gauge all update. A goal with every milestone done turns green.
5. **See the schedule.** Any goal with both a start and target date plots on the **Timeline** at the top, with a live "today" line.

### Finding things in a big pile
- **Search** filters by title, notes, or type.
- **Type chips** (All / Cert / Project / …) narrow the view to one kind of goal.

---

## Your data &amp; backups

Horizon saves everything to **this browser** automatically (using `localStorage`). Close the tab and come back — it's still here.

Two things follow from that:

- Your data is **private to this browser on this device**. It does not sync on its own.
- **Export early, export often.** The **Export** button downloads your whole roadmap as a `.json` file. That file is your backup *and* the way you move a roadmap to another device (via **Import**). If you only do one thing after a big dump session, export a backup.

`Sample` reloads the demo set; `Blank` wipes everything to start clean (export first if you want to keep it).

---

## Put it online (GitHub Pages)

1. Create a repository and **Add file → Upload files** → drop in `index.html`.
2. **Add file → Create new file** → name it exactly `.nojekyll` → leave it empty → commit. *(This stops GitHub from running its blog builder over your plain HTML.)*
3. **Settings → Pages → Build and deployment** → Source: **Deploy from a branch** → Branch: `main`, Folder: `/ (root)` → **Save**.

A minute later your roadmap is live at `https://YOUR-USERNAME.github.io/YOUR-REPO/`, ready to bookmark on your phone. Because the file is named `index.html`, it loads at that address with nothing extra to type.

---

## Using it on more than one device

Out of the box, each browser keeps its own copy, so use **Export / Import** to move between your laptop and phone.

For *automatic* sync across devices, Horizon has **Supabase cloud sync built in** — it's just switched off until you add your keys. When configured, you sign in with the same email on your laptop and phone and your roadmap follows you everywhere, still on GitHub Pages, still one file. It's a ~10-minute one-time setup: see **`SUPABASE-SETUP.md`**. Until then, the "Cloud Sync" panel reads `LOCAL ONLY` and everything works exactly as described above.

---

## Make it yours (and learn from it)

It's one readable file — HTML for structure, CSS for looks, and plain JavaScript for behavior. Good first edits:

- **Change the sample goals:** edit the `DEFAULT_DATA` block near the top of the `<script>`.
- **Rename or recolor the horizons:** the `HORIZONS` array.
- **Add goal types:** the `TYPES` and `TYPECOLOR` entries.
- **Restyle it:** the color and font variables at the top of the `<style>` block (`--ink`, `--paper`, etc.).

The whole app runs one simple loop: your data is the single source of truth, a `render()` function paints the screen from it, and every click or keystroke changes the data and repaints. Once that clicks, it's the same idea every web framework is built on.

---

## Files

- `index.html` — the entire app.
- `.nojekyll` — empty file that tells GitHub Pages to serve the HTML as-is.
