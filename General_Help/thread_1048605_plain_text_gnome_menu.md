---
title: "plain text gnome menu"
date: 2009-01-23
forum: General Help
---

### Post by fuuf on 2009-01-23
I'm setting up a laptop with a low resolution, In ubuntu, is there a way to get rid of the icons in the gnome menu?

---

### Post by mcduck on 2009-01-24
Press Alt-F2 and run "gconf-editor". Then use it to browse to desktop/gnome/interface and disable the "menus_have_icons"-key.

This will remove icons from all menus in all GTK programs, not only the panel menu. I'm not sure if there's some way to only remove panel menu icons.


(Since you are doing this because you're running on low resolution, I suggest at the same time changing value of the "toolbar_icon_style" from "large-toolbar" to "small-toolbar". This will make toolbars slightly more compact to save even more screen space.

---

### Post by fuuf on 2009-01-25
Thank you very much, worked like a charm :D

---

