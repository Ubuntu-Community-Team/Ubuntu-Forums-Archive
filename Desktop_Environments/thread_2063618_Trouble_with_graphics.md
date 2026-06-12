---
title: "Trouble with graphics"
date: 2012-09-27
forum: Desktop Environments
---

### Post by Fudgey05 on 2012-09-27
Hi Guys,

I'm having some trouble with my graphics in Ubuntu 12.04.

I installed a fresh copy of ubuntu. afterwards my graphics were really poor. I checked the syslog and it said I should add acpi=force to grub, so I did. Now if I try to boot, it shows a purple screen then dies, with the screen showing "signal frequency out of range". I have tried uncommenting the grub GRUB_GFX_MODE line from the grub file, but to no avail. Also, I can't get Xorg -configure to work, since if I use either the recovery mode or remove the acpi=force, the graphics adapter isn't detected and the Xorg.conf file is generated incorrectly. 

The computer is a SBC from NEC, using a Intel 915GM graphics card. The monitor is a NEC MultiSync P401.

Any help would be most appreciated.

---

