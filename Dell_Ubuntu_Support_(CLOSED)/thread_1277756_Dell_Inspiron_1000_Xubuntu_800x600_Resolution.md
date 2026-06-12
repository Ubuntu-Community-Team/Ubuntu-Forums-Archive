---
title: "Dell Inspiron 1000 Xubuntu 800x600 Resolution"
date: 2009-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by edoss on 2009-09-28
I am new to Ubuntu and Linux - when this notebook crashed under WinXp Home - I decided it was time to see if the grass was really greener.  I have been able to get everything that I need to work including my wireless adapter.  The one thing that I am having troubel with is getting my screen resolution to 1024 x 768 - right now I am stuck at 800 x 600.  I will nto be needing or using 3D or any gaming.

I read so many threads yesterday that my head hurt, there were so many variations.  I have the SiS 650 chip set (which is working fine at 800 x 600).  I found the an updated Linux driver on the SIS website and down loaded it to my Desktop, but the Hardware Driver app does not find it.  I have not tried to hand modify my xconf file, becuase at this point I am not sure what to change.

 *-display UNCLAIMED
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 cap_list
                configuration: latency=0

Any help would be appreciated.

---

### Post by edoss on 2009-10-04
Well I finally solved this problem.  It was really simple!!  I tried manually changing my display settings, no luck.  Finally after reading another archived post, I changed my driver in the xorg.conf file to "SiS" from Vesa, rebooted and here we are.

BTW - I have been a Ubuntu user for a little less than 2 weeks and I really like this OS.

:P

---

### Post by murderslastcrow on 2009-10-05
Good to hear you solved it already. I almost thought the days of changing your X configuration were over, but I guess there are still these rare cases. Enjoy your stay! :3 Plenty of great stuff in Ubuntu-land.

---

