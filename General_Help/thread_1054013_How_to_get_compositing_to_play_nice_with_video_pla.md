---
title: "How to get compositing to play nice with video playback and 3d programs?"
date: 2009-01-29
forum: General Help
---

### Post by Lemegeton on 2009-01-29
I'm wondering how to get compositing to play nice with video playback and 3d programs. More specifically, KDE desktop effects with Dragon Player and World of Warcraft.

Right now I'm using KDE 4.2. Desktop effects on their own work fine and much better than they did in 4.1. Video playback and 3d programs on their own work fine. But if I try to use desktop effects and either video playback or a 3d program it doesn't work properly.

I'd describe what is happening as a fight for the screen. Video playback flickers a bit when not full screen and if I open up something 3d like World of Warcraft it also flickers. If I use the desktop cube effect then the viewport for World of Warcraft stays in place on the screen rather than moving properly with the cube.

I've seen videos of World of Warcraft and Compiz working properly together on Youtube so I would assume that it's also possible with KDE desktop effects.

For a video card I use ATI Radeon HD 4670 1GB/GDDR3 with the proprietary driver. I hope that's not the problem.

---

### Post by Lemegeton on 2009-01-31
I managed to get desktop effects working nicely with xine and Kaffeine. I've got both playing the same file at the same time now and they're both working perfectly with desktop effects.

I've had no luck with Dragon Player or World of Warcraft yet.

Found something useful here: [http://forums.opensuse.org/applications/386618-desktop-effects-interfers-video-playback.html](http://forums.opensuse.org/applications/386618-desktop-effects-interfers-video-playback.html)

What I did was:
-run `xine`
-Right click anywhere on the window to get a popup menu
-Go to "Settings"
-Go to "Setup..."
-In the current tab (gui) the second box down (Configuration experience level) change value from "Beginner" to "Master of the known universe"
-Click "Apply" down at the middle bottom
-Click the "video" tab
-In the first box down (video driver to use) pick "xshm"

I have no idea how or why this works, but suspect it has something to do with no longer rendering directly to the screen thus allowing the desktop effects to be applied.

---

### Post by Lemegeton on 2009-01-31
I've figured out what I want to get World of Warcraft working is DRI2.

---

