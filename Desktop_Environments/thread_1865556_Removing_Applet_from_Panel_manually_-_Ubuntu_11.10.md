---
title: "Removing Applet from Panel manually - Ubuntu 11.10"
date: 2011-10-20
forum: Desktop Environments
---

### Post by arul001 on 2011-10-20
I have upgraded to Ubuntu 11.10 from 11.04 and switched to Ubuntu Classic ( after installing gnome panel ).

I want to remove the "Window List" applet but the new panel doesn't respond to right-clicks .

( In previous panels, i can just right-click and remove the applet)

========================================
I tried manually editing the entries in :

~/.gconf/apps/panel/applets/window list

i deleted the window list directory itself . But the applet is still there
========================================

Any idea on how to do this ? 
( problem only in Ubuntu 11.10 gnome-panel )

---

### Post by crdlb on 2011-10-20
[Hold the alt key]("https://help.ubuntu.com/community/GnomeClassic#Applets_.26_Panel_Layout") when you right click.

---

### Post by arul001 on 2011-10-23
Thank you very much...

Works fine :)

---

