---
title: "Removing Resolutions"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Inhumane on 2006-09-12
How can I remove certain resoltuions so my computer won't think I have more than 1024x768? I tried going to xorg.conf but it lists only up to 1024x768, yet the Screen Resolution program built into Gnome lets me go higher

---

### Post by orb9220 on 2006-09-12
In a term if you run

sudo dpkg-reconfigure xserver-xorg

Will let you select and unselct using spacebar and then rewrite the xorg.conf file.

Be sure to backup xorg.conf file when modyifing.

---

