---
title: "Raid: what if disks get mixed up?"
date: 2008-12-08
forum: General Help
---

### Post by LyhjeHylje on 2008-12-08
Couple months ago I build my first raid/lvm arrays: 2x3 raid5/lvm + unraided separate disk for OS.
Tonight I started thinking what if I move the arrays to another computer? Do I have to make careful notes about which disks goes with each another or can the raid-tools detect that?
I have been googling this for awhile now and it seems that with hardware raid there might be issues but what about software raid like mine?
The OS disk is left unsecured on purpose because I thought that when it breaks there must be at least couple newer ubuntu versions and I'd just do clean install, but maybe I should backup some raid and lvm related config files?

---

### Post by fjgaude on 2008-12-08
Well, once an array is created using **mdadm** it uses the unique UUID that is given to each drive and uses that to assemble on startup. This UUID is not the one the OS uses to identify drives. Drive names are not used by mdadm so they can get mixed without issues.

---

