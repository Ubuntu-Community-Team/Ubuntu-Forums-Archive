---
title: "volume up/down speed"
date: 2009-05-15
forum: General Help
---

### Post by rock4christ on 2009-05-15
I have my volume up/down/mute keyboard shortcuts working, but is there any way to change how much it goes up/down each time?

---

### Post by kanikilu on 2009-05-15
Open a terminal (Application > Accessories > Terminal) and type ```
gconf-editor
``` In the window that opens, browse to:

apps > gnome_settings_daemon > volume_step

Increase or decrease from default as desired. Changes should take effect immediately, so just play with it until you get it how you want it, and then just close gconf-editor.

---

### Post by rock4christ on 2009-05-15
thanks! I hated going from too loud to too soft.

---

