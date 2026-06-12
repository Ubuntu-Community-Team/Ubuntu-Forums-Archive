---
title: "X-server won't start"
date: 2005-12-20
forum: General Help
---

### Post by aszlej on 2005-12-20
Hi!

I was using Ubuntu since the release of version 5.04 and besides soudcard problems everything was OK.

Until few days ago, when I tried to install Ubuntu 5.10 on my new machine. For some reason, I just can't start the X server. It gives me some errors related to display (can't initialize display or something like that). I tried both 32 and 64 bit versions and none of them works.

Here are my specs:

Pentium D 820
Intel D945PSN mobo
2x512 MB DDR2 (Corsair)
3DConnect Radeon x800 GTO (PCIE) <- I think this might be a problem
WD SATA 250 GB HD
Chaintech AV-710 (on which I can't get SPDIF to work on linux :/)
[B]
Here is my log file:[/B]

[http://markowicz.info/Xorg.0.log.txt](http://markowicz.info/Xorg.0.log.txt)

Does anyone have any idea about what might be a solution to this problem?

---

### Post by aszlej on 2005-12-21
Problem solved! After an hour long battle with ATI Driver and* Xorg.conf I started GNOME :). Unfortunately, the only video mode that works is 1280*1024*24. I was quite angry because of all this problems with UBUNTU but now I see, that this is a ATI's fault :/. They used to make very good cards, but now I see that Nvidia is the best choice. Even ATI drivers for windows are IMHO poorly designed when compared to Nvidia Forceware :).

---

