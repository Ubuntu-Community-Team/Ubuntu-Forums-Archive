---
title: "Freezing Problem"
date: 2007-04-22
forum: Desktop Environments
---

### Post by MugenDraco on 2007-04-22
i just upgraded to version 7.04, and it freezes on my constantly.  my roommate who knows a lot more about Linux than I do seems to think that it has something to do with an ata mod.  i used the previous version of Ubuntu as well, and it froze too, but not nearly as often as the new version.  here are my specs.

I use a Toshiba Satellite P-35 laptop
It has 512MB of RAM
100GB Harddrive
Pentium 4 processor
I'm not using dual-boot

When it freezes, I'm usually running Firefox and Gaim, nothing else.

My roommate thought it was also important to include my mod output from: lsmod | grep ata

ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  2 sbp2,libata

---

