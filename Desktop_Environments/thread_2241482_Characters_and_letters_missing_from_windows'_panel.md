---
title: "Characters and letters missing from windows' panels, Desktop and menus !"
date: 2014-08-26
forum: Desktop Environments
---

### Post by smail-bechiche on 2014-08-26
After a driver upgrade with the "Intel Graphics Installer for Linux", characters often disappear in the middle of the session, a refresh or mouse hover brings them back for a couple of seconds and the next restart fixes the problem, but not permanently.
How can I fix this ?! Please help.

Using : Ubuntu 14.04 64b, Gnome 3.12.2, Gnome Flashback session, gdm.
Hard : Intel® Core™ i5 CPU M 540, Graph : Intel® Ironlake Mobile.

Please specify commands and/or log files to check (if any).

[ATTACH=CONFIG]255849[/ATTACH][ATTACH=CONFIG]255850[/ATTACH]

---

### Post by ajgreeny on 2014-08-26
Have you tried any changes in the font-rendering settings, wherever that is in Ubuntu-Gnome?  Try different Hinting or Sub-pixel-ordering, as they can make quite a difference to font display.

---

### Post by smail-bechiche on 2014-08-26
Thank you #ajgreeny for your reply , I haven't changed anything for months, but because you mentioned it, I'll try modifying some related settings, hoping to find the proper ones.

---

### Post by smail-bechiche on 2014-08-28
Nothing useful, any ideas ?

---

### Post by ajgreeny on 2014-08-28
Sounds a bit like [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1342675](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1342675)

---

### Post by smail-bechiche on 2014-09-10
Reducing the windows' font size using ubuntu-tweak solved the problem for me. Thank you.

---

