---
title: "Yakuake on a single Workspace"
date: 2010-01-13
forum: Desktop Environments
---

### Post by NiGhtMarEs0nWax on 2010-01-13
Does anyone know how to set yakuake to appear on one workspace only?

Using GNOME 2.28.1
Ubuntu Karmic.

---

### Post by Zorael on 2010-01-13
You would probably have to tell your window manager (Compiz) to limit it to that workspace, then. It's probably in something like Window Rules in ccsm, though I'm far from sure, as I run KWin.

---

### Post by NiGhtMarEs0nWax on 2010-01-13
hmm i think you are onto something there, can someone enlighten me please?

---

### Post by benerivo on 2010-01-13
In compizconfig-settings-mananger (ccsm) you need to enable the 'Place Windows' plugin. In this plugin's options, go to the 'Fixed Window Placement' tab. Click on 'New' in the 'Windows with fixed viewport' section. Then click on the '+' icon and click 'Grab'. Then click inside the yakuake window (to tell it that you want this setting to affect yakuake). Then you can set your preferred 'viewport'.

---

### Post by NiGhtMarEs0nWax on 2010-01-14
Thanks! im sorry, maybe I should have been more specific. What I am trying to achieve is to get the said window to appear in the workspace its _opened in_ only.

That method you stated just changes to the specified workspace but the shell still opens up on all 4 workspaces.

Thanks!

---

### Post by NiGhtMarEs0nWax on 2010-01-15
bump

---

