---
title: "Gnome Wayland Lock-up"
date: 2017-06-09
forum: Desktop Environments
---

### Post by BarryD9545 on 2017-06-09
I was trying the new variations of Ubuntu 17.04 (Gnome Flashback (matacity & Compiz) vs. Gnome) and after logging out of a well function Gnome session I tried to login in using Gnome Wayland and all that came up was a blank screen with a blinking cursor.

Not a terminal, just a blinking cursor that had no response to any keypress.

Anyone have any ideas?

Thanks.

---

### Post by deadflowr on 2017-06-09
Known issue when running (er, trying to run) wayland sessions with Ubuntu and it's default display manager, lightdm.
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1680496]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1680496")
Suggested to try installing gdm (gdm3, really), change the display manager to gdm and then try logging into the wayland session.


Also
Moved to *Desktop Environments*

---

