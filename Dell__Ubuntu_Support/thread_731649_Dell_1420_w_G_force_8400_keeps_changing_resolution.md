---
title: "Dell 1420 w G force 8400 keeps changing resolution."
date: 2008-03-22
forum: Dell  Ubuntu Support
---

### Post by yeowzuhx3 on 2008-03-22
default is 1024 x 768. Whenever I reboot, I have to go through a sometimes useless routine of resetting the screen resolution and it's starting to pPPP me off.

---

### Post by sdennie on 2008-03-22
What utility are you using to set the resolution?  If you use the nvidia control settings utility, it won't be saved at all unless you start the tool with "sudo nvidia-settings" and explicitly save the changes.  It writes the changes to a root owned file and so will not save if you start the tool from the gnome menu.  It might be possible to save the changes via System->Preferences->Screen Resolution but, I have never actually tried that.

---

