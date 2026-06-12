---
title: "Configuring a Panel"
date: 2009-06-22
forum: Desktop Environments
---

### Post by biomedtek on 2009-06-22
When a panel is set to autohide, a small portion of it is still visible at the edge of the screen. Is there a way to configure how much of the panel remains visible? I would like to have a very narrow portion showing, or perhaps none at all.

---

### Post by cogier on 2009-06-24
This value can be changed. Press **Alt-f2** to get "Run Apllication" and type in **gconf-editor** followed by OK. Work your way down to **apps/panels/toplevels** there you will see the 2 panels there. Select the panel you want and change the value of **auto_hide_size** from 6 to 0. The panel will now not show.

---

