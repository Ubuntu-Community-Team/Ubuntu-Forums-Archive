---
title: "How to uninstall GNOME Do"
date: 2009-03-03
forum: General Help
---

### Post by banana jama on 2009-03-03
i have gnome do and no longer want to use it. i've look how to uninstall programs. I've used the code ```
sudo dpkg -l | grep Gnome Do
``` and it said no file directory found. so how do i uninstall gnome do? i've also used snaptic manager and click complete uninstall.

---

### Post by ubuntu27 on 2009-03-03
the name is wrong. It is "gnome**-**do" not gnome do

---

### Post by malakhi on 2009-03-04
It may already be uninstalled. To make sure, open a terminal and type the following:
```
sudo apt-get remove gnome-do
```
Once apt finishes, gnome-do will probably still be running. Bring up the gnome-do interface by pressing <super>+<space> (<super> is the Windows key on most keyboards) then click the little down arrow in the top right corner then click quit. gnome-do shouldn't bother you anymore after that.

---

### Post by banana jama on 2009-03-04
malakhi you were right thanks i feel like an idiot for not doing that before starting a thread.

---

