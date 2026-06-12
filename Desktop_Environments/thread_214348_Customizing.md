---
title: "Customizing"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Tagmaster on 2006-07-12
Hi, i would like to know how to change these icons :)

[IMG]http://img109.imageshack.us/img109/9046/apple1xb.png[/IMG] Music Applet Controls

[IMG]http://img109.imageshack.us/img109/8939/tray4id.png[/IMG] Tray Icons (from left to rigth): Gaim, Banshee, Compix/XGL

[IMG]http://img56.imageshack.us/img56/9690/generic8qv.png[/IMG] Generic Folders Icons (without chagning the system icon theme, just the general folder icon)

Thxn in advance :D

---

### Post by Tagmaster on 2006-07-12
Bump :-|

---

### Post by aysiu on 2006-07-12
Every icon is a .png or .svg somewhere.

If you have a locally installed theme, it's in /home/tagmaster/.icons

If it's a globally installed theme, it's in /usr/share/icons

I usually do something like this: ```
sudo updatedb
locate banshee*.png
``` The first command may take a couple minutes.

---

### Post by Tagmaster on 2006-07-12
Thxn! that was really usefull :)

---

