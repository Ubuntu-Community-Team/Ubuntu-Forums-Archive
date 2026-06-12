---
title: "Lost all menus and icons in the desktop top toolbar"
date: 2005-03-29
forum: Desktop Environments
---

### Post by Yves T. on 2005-03-29
After installing the CrossOver windows emulator (I tried to test Enterprise Architect on Linux) , I lost the Applications and Computer menus along with the icons in the top toolbar!
Any idea how I can restore the desktop?
Thanks a lot
Yves

---

### Post by ubuntu_demon on 2005-03-29
[QUOTE=Yves T.]After installing the CrossOver windows emulator (I tried to test Enterprise Architect on Linux) , I lost the Applications and Computer menus along with the icons in the top toolbar!
Any idea how I can restore the desktop?
Thanks a lot
Yves[/QUOTE]
 please give us more information

If the menu's are just crashed try : "killall gnome-panel" or restart gdm by ctrl-alt-backspace

If you accidentily removed some essential package try : "sudo apt-get install ubuntu-desktop"

If you just need your crossover icons/menuitems .. here's a guide :

[http://www.ubuntuforums.org/showthread.php?t=20879](http://www.ubuntuforums.org/showthread.php?t=20879)

---

### Post by Yves T. on 2005-04-03
Thanks for your help
With your indications, I renamed all the .gconf* and .gnome* directories and then start a new gnome session. This restored a fresh new desktop. Some menu items are missing, not too bad.
Don't know which config files were broken.
Thanks again
Yves

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=Yves T.]Thanks for your help
With your indications, I renamed all the .gconf* and .gnome* directories and then start a new gnome session. This restored a fresh new desktop. Some menu items are missing, not too bad.
Don't know which config files were broken.
Thanks again
Yves[/QUOTE]
 np :)

---

