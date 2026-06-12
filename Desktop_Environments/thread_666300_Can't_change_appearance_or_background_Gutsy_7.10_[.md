---
title: "Can't change appearance or background Gutsy 7.10 [Solved]"
date: 2008-01-13
forum: Desktop Environments
---

### Post by hal8000 on 2008-01-13
Im using Ubutuntu Gutsy 7,10 and had lost the ability to change desktop background and appearance properties.
Starting gnome-appearance-properties in a terminal, revealed two messages about Wx-Widgets, then I found the following bug report on launchpad.

[https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/138726](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/138726)

A Right click from gnome 2.20.1 desktop brought up appearance properties but tabs were visible and could not be clicked (no effect),

The solution was also to uninstall gtk-gt-themes.

I think the reason my desktop behaved in this way is that I set the desktop background to point a jpg in my /home folder. I deleted the jpg, the desktop then  displayed a solid color, and this is when I lost the ability to change appearance and properties.

Not sure if the bug has been fixed yet, so hope this helps someone else.

---

