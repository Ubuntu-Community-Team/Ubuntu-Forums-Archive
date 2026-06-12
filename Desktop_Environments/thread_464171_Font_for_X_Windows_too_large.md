---
title: "Font for X Windows too large"
date: 2007-06-04
forum: Desktop Environments
---

### Post by yohan77 on 2007-06-04
Hi;
I'm new to Ubuntu.  The font in any program that runs under X (Audacity, XMMS, etc) has a font size that is too large.  How can I reduce the font size for these programs?  The Ubuntu Font preference control doesn't affect it.

It seems to affect contextual menus, the traditional kind (file, edit, etc) as well as menu and dialog boxes.

TIA

---

### Post by pn4577 on 2007-06-05
Hi yohan77,

go to the */etc/X11/xorg.conf* file and add ```
DisplaySize  <width-in-mm> <height-in-mm>
```to the *Monitor* section. This should adapt the display size of all fonts.

Cheerio

---

