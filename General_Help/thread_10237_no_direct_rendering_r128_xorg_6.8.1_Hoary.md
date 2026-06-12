---
title: "no direct rendering r128 xorg 6.8.1 Hoary"
date: 2005-01-06
forum: General Help
---

### Post by malevolentjelly on 2005-01-06
Hi,
  I'm running Hoary/X.org 6.8.1 on a Powerbook Pismo (G3 400, 320 mb, ATi Mobility Rage M3 (rage 128 chipset)) and I've managed to get X running, DRI claims to be working, etc, but when i run glxinfo, it tells me i have no direct rendering, and I get 98 fps in glxgears. I am using the r128 driver. I'll post my xorg.conf here. Can anybody help me out? :confused:

---

### Post by chascon on 2005-01-07
You have the choice of r128 or ati driver to run the Rage 128 card.
change your XF86Config-4 and /etc/modules to reflect this and be congruent.

---

