---
title: "Size of the desktop"
date: 2009-10-21
forum: Desktop Environments
---

### Post by virushark on 2009-10-21
Hey guys, I'm running gnome at 1280x768 (jaunty). For some reason everything seems to take so much space on screen; this is mostly because of the padding in buttons (or pictures inside the buttons making them bigger) and such. I think it's something to do with the theme I'm using but I digress. I tried changing the dpi settings - it helped a little but various desktop elements still take too much space. Is there anything else I can do?

---

### Post by mcduck on 2009-10-21
Install a more compact theme. And set the system fonts to use smaller sizes. You might also want to set the toolbars to "icons only" to save more space.

There's also a gconf key that makes toolbars slightly more compact (open gconf-editor and set desktop/gnome/interface/toolbar_icon_size" to "small-toolbar"), although the difference is quite small compared to what using a compact GTK2 theme would do.

Edit: Just search for the word "compact" in gnome-look.org and you'll find quite many themes designed to be compact for use with small-resolution displays.

---

### Post by virushark on 2009-10-21
Thanks a lot, I'll try that. Hopefully I'll find an ok looking compact theme. :)

---

