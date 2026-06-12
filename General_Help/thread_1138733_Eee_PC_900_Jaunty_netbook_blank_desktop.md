---
title: "Eee PC 900 Jaunty netbook blank desktop"
date: 2009-04-26
forum: General Help
---

### Post by sjöbjörn on 2009-04-26
Installed Jaunty Netbook Remix on a Eee PC 900.
Found animated icons slowed down video performance too much.
Switched to classic Ubuntu desktop and was very happy until I did a reboot and found my desktop perfectly blank.
No icons, status bar or anything. Just background wallpaper and mouse pointer.
I can get a right-click menu and a log-off dialog using ctr-alt-del.
I can change background.
I can also ctrl-alt-F1 to terminal.

Tried failsafe Gnome login without luck.
I have uninstalled and reinstalled xserver and nautilus - no change.
Looked around the forum, but no hints.

---

### Post by alan_b on 2009-04-27
There seems to be a known bug in the desktop-switcher app causing this (and a similar problem in netbook mode). See 

[https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)

The quick and dirty fix for me was to remove or rename the .gconfd directory in the user's home folder.

---

### Post by alan_b on 2009-04-27
P.S. Though I should add that that will lose any customisations you've made to Gnome!

---

