---
title: "How to manually set font in .gtkrc-2.0"
date: 2008-07-01
forum: Desktop Environments
---

### Post by B-Con on 2008-07-01
I'm switching away from a Gnome desktop, but I've been keeping gnome-settings-manager around so far, but I'd like to get rid of it (dependency chaining).

What all does gnome-settings-manager do? What I've been able to tell is that it effects fonts and icons. I can set the icon theme manually in my ~/.gtkrc-2.0 file, but what about fonts? How do I determine what font gnome-settings-manager is using and manually set it?

---

### Post by urukrama on 2008-07-01
Add the following lines:

> style "font"
{
font_name = "Corbel 8"
}
widget_class "*" style "font"
gtk-font-name = "Corbel 8"

Replace "Corbel 8" with whatever font name and size you'd like to use.

Gnome-settings-manager also controls you mouse cursor, and maybe a few other things :-)

---

### Post by B-Con on 2008-07-01
Thanks, got it working.

---

