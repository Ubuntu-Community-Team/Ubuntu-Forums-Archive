---
title: "Ubuntu install hangs on PowerEdge 400SC - SATA RAID not recognized during OS setup"
date: 2007-09-24
forum: Dell  Ubuntu Support
---

### Post by ceabaird on 2007-09-24
I just bought a new Dell to use as a server. It has an SATA card (x2 160GB drives), but when I try to install Ubuntu 7.04 (Feisty Fawn), the installation wont recognize the SATA Raid setup, but insists on calling them 2 separate drives (SCSI05 and SCSI06). If I choose one drive and continue, the installation ends up hanging during the final portion of the setup, at about 85%.

The Dell is a P4 2.8 GHz with 160GB RAID.

Is it possible to install Ubuntu on one drive and then try the RAID setup later, OR should I put another IDE drive in for the OS and try to set up the RAID on both 160GB disks later?

---

### Post by phr0ze on 2007-09-25
I have installed Ubuntu Fine on these 400SC machines without the RAID, so I would stick with installing on a non-raided disk, then access the raid later.

---

### Post by ceabaird on 2007-09-30
Thanks. That's what I ended up doing - first by removing the FastTrak Raid card altogether. Now FF is installed, and now I'm in the middle of configuring it.

Google taught me that these raid cards cause a few problems when trying to install Ubuntu, related to them being a software, not hardware, RAID.

---

