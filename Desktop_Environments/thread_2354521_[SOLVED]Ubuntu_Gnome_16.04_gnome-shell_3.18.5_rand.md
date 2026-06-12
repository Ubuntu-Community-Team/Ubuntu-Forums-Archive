---
title: "[SOLVED]Ubuntu Gnome 16.04 gnome-shell 3.18.5 random stop loading after login"
date: 2017-03-03
forum: Desktop Environments
---

### Post by alessandroalb2 on 2017-03-03
Hi,
I use Ubuntu 16.04 Gnome with gnome-shell 3.18.5, standard version on Ubuntu gnome 16.04.
Sometine, random, not every time, i keep this situation :
1. power on pc
2. see login screen (gdm)
3. enter username and password
4. screen empty (green) with arrow pointer free to move, but no icons, no bar, nothing other
5. if i try to reboot from console (tty) going to with - for ex.- ctrl+alt+F6, arrow pointer disappears and screen freeze 

Help for me and other, i mean.
Alessandro

---

### Post by alessandroalb2 on 2017-03-03
Installed gnome 3.20.4, to test if problem exist in too.
Reboot 25 time and no one time keep anomal login.
This version hasn't this problem.
Now ? Report an issue to who, to investigate what needs backporting ?

---

### Post by alessandroalb2 on 2017-03-08
Use driver Intel on Sandybridge Graphics.
I update driver with "Intel Graphics Update Tool v.2.0.2".
Updating solved problem.
Old driver have random bug, with gnome-shell.
Ty for attention.

---

