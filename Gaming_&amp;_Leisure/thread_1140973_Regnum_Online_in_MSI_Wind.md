---
title: "Regnum Online in MSI Wind"
date: 2009-04-28
forum: Gaming &amp; Leisure
---

### Post by tofiluk on 2009-04-28
hi! i installed regnum online in my MSI Wind however, it says unsupported video card.

using "sudo lshw -C display" in terminal yields:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GME Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

is there really an incompatibility?

thanks!!!

---

### Post by maheshjr2000 on 2009-04-28
why do you have two display listings?

---

### Post by compiledkernel on 2009-04-28
Yes, there is. I dont think the Intel cards are specifically supported by the Regnum devs. You can ask them, but I had the same problem running the game on a EEE, and an Acer Aspire One, both whom have the 945 class Intel based video card.

---

### Post by wolfyking2 on 2009-04-28
It's weird...I had this same problem, but regnum online worked a while ago, now its giving me unsupported video card error

---

