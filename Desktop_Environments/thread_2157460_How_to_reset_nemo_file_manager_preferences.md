---
title: "How to reset nemo file manager preferences ?"
date: 2013-06-25
forum: Desktop Environments
---

### Post by xtrailrunner on 2013-06-25
I found some strange behaviour when setting the default zoom level in the preferences of Nemo file manager.
That's why I would like to reset them to the default but cannot find the location.
Any help is appreciated.
Kind regards
Juergen

---

### Post by dino99 on 2013-06-25
glance inside your /home, you might find something like .nemo, or inside .local, .gconf, .gnome2, .config

---

### Post by xtrailrunner on 2013-06-25
Thanks, I've looked through all these directories. I can set the preferences also using gconf-editor.
The strange thing is that in list view I get different zoom levels for different folders, i.e. sometimes the rows are very large, sometimes quite small.
I would like to set the zoom level in list view for all folders the same. I can change the zoom level for individual folders but changes are not persistent.
So it looks like the zoom level is derived dynamically.

---

### Post by xtrailrunner on 2013-06-26
For me it looks like a bug. The content of each folder is displayed with a different zoom factor. It's not possible
- to set a default zoom factor for all folders
- to persist a zoom factor for a specific folder.

---

