---
title: "gnome-panel with xorg.conf defined resolution"
date: 2010-06-01
forum: Desktop Environments
---

### Post by huit on 2010-06-01
My screen has a broken edid (asus vw223b) but I can still define a modeline in xorg.conf to display most things properly.

Gnome panel however seems to load itself before xorg.conf is read leaving the power icon, clock, speaker, chat and mail icons aligned to what would have been the top right pixel on a smaller resolution. That is the clock etc. are about 1/4 screen left of the right hand side yet my networking icon loads correctly off to the right.

I have tried "killall gnome-panel" which seems to restart the panel (it disappears and reappears) without success.

Screenshot attached

Update: Uninstalled gnome-panel, on reinstall it actually crashed X (i think), i went back to ctrl+F1 did "sudo service gdm restart" and it brought back the same desktop seen in the screenshot. There was also an error that displayed on the gdm restart concerning the a fast user switch applet to which i just confirmed to delete it.

---

