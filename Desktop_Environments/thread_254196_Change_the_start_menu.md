---
title: "Change the start menu?"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Faytz on 2006-09-09
Im trying to change the start menu instead of showing applications,ubuntu logo,system, and places to a start button (linsta 3 start svg).How do i do this?

---

### Post by aysiu on 2006-09-09
Well, first of all, you should add to the panel the *Main Menu*, **not** the *Menu Bar*.

And the icon for that is /usr/share/icons/Human/48x48/places/distributor-logo.png

If you do Alt-F2 ```
gksudo nautilus
``` you can modify the files in the /usr/share/icons directory. You may have to replace more than 48x48.

Once you're done with all your changes, do Alt-F2 ```
killall gnome-panel
``` to refresh the Gnome panel.

---

### Post by Crypto-138 on 2006-11-19
Wouldn't a better and less system-altering choice be to place start-menu.svg into the 
~/.icons/<current icon theme>/scalable/ directory instead, and rename it to 'distributor-logo.svg'?

---

