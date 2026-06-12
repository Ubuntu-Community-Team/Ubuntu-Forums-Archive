---
title: "No Trash Can"
date: 2009-08-21
forum: Desktop Environments
---

### Post by BubbaBlues on 2009-08-21
I've just replaced artistx with Ubuntu 9.04 and I have no desktop icons. I have no trash can! Can someone tell me how to get a trash can on my desktop? Please?

---

### Post by coldReactive on 2009-08-21
ALT+F2 then run **gconf-editor** (NOT AS SUDO/ROOT)

Then, when the gconf-editor comes up go to apps \ nautilus \ desktop.

You'll see on the right side a bunch of options. Find **trash_icon_visible** and make sure it's checked.

You MAY have to logout and log back in for it to appear.

By default, ubuntu has a trash can in the far lower right corner of the screen ON A PANEL.

---

### Post by BubbaBlues on 2009-09-15
Thanks for the help:lolflag:

---

