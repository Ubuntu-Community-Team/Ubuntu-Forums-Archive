---
title: "Freezing from Desktop Effects"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by GearedForWar on 2007-10-27
Ok I have a ATI RADEON X300 (PCIE).  The Desktop Effects are WORKING, its just they always freeze the screen after I do something, such as open or close a window or switch scenes.  

For any one who can figure out the problem under this command  ** sudo lshw -C display **  here are the results:

 *-display:0             
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0

Someone plz tell me whats wrong.

---

### Post by pieisgood4589 on 2007-10-27
OK, I wanna let out my Ubuntu fury out on you. DON'T USE DESKTOP EFFECTS. They are entirely experimental, and could screw up your system, making ME MYSELF AND I have to re-install the whole @amn thing. Don't use it. If you really do, then look in the bug reports. I'm sure I found a solution somewhere...

THAT WAS FUN!!!! EVERYBODY SHOULD LET OUT THEIR UBUNTU FURY SOMETIME! :guitar: :lolflag::lolflag: :lolflag: :lolflag: :lolflag: :lolflag: :guitar:

---

### Post by GearedForWar on 2007-10-27
KK.  I thougt it was something just about everyone uses.  Well I am a 16 year old computer nerd and love graphics.  It could be I'm dual booting it with Windows or I need more physical memory but I dont feel like partitioning anything right now so I'll expiriment later.  TY.

---

### Post by Cochise on 2007-10-27
i've got the same probelm, i just disabled them, going to install the new ati driver and see if that helps, new driver means no xgl woohoo

---

### Post by daulex on 2007-10-27
disable the default ones and just overwrite them with beryl.. problem solved, bugs gone :)

---

### Post by Cochise on 2007-10-28
get the new ati driver, i did it eariler and its sweet

---

### Post by GearedForWar on 2007-10-28
> **Cochise said:**
> get the new ati driver, i did it eariler and its sweet

How much is it?  Or just because I heard you can download things to update drivers can you just download it?

---

### Post by jhenager on 2007-10-28
ATI binary X.Org driver
Video driver for ATI graphics accelerators 
Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports:
* FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400, V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128, X1-128, X1-256p
* FireMV: 2200 (Single card PCI-e configuration)
* Mobility FireGL: V5000, T2
* Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, 9800, 9600, 9550, 9500
* Radeon Xpress: 200M series, 1250 IGP, 200 series
* Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550, X300, 9800, 9700, 9600, 9550, 9500
ATI All-in-Wonder variants of the above cards/chips are also supported, but video capture is not.
This package provides 2D display drivers and hardware accelerated OpenGL.

Canonical Ltd. provides technical support and security updates for ATI binary X.Org driver


Nothing in Add/Remove has a cost associated with it.
Search in System Tools.

---

### Post by Cochise on 2007-10-28
[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

follow this guide

---

### Post by GearedForWar on 2007-10-28
ok for the xorg.conf file which is now a existing file on my comp,  how do i edit it so that "fglrx" set for the driver in the device section?  For some reason the xorg.conf file is blank and there is no device section to change.  I tried adding something that it had on the site and I think he meant remove if if it was there and I couldnt access the GUI interface and had to go to the CLI and I'm glad I knew the basics of deleting admin files and shutting down.

---

