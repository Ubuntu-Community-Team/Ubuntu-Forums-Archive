---
title: "Where is the trash bin?"
date: 2009-03-18
forum: General Help
---

### Post by horax on 2009-03-18
I'd love to put a trash icon on my desktop, but I cannot find it.

Any help locating it will be rewarded with cheese and popcorn.

hx

---

### Post by blackened on 2009-03-18
Press alt+f2, type **gconf-editor** and press enter.

In the gconf-editor window's left-hand pane select apps->nautilus->desktop and make sure the box is checked for trash_icon_visible.

---

### Post by iaculallad on 2009-03-18
Press Alt+F2, then input **gconf-editor**. Navigate apps->nautilus->desktop, and on the right-pane window, place a check mark for  **trash_icon_visible**.

---

### Post by sideaway on 2009-03-18
>alt+f2, type gconf-editor press run.

on left-hand pane select apps>nautilus>desktop and tick the box for trash_icon_visible.

---

