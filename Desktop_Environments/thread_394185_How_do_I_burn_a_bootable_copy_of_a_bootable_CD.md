---
title: "How do I burn a bootable copy of a bootable CD?"
date: 2007-03-26
forum: Desktop Environments
---

### Post by Patb on 2007-03-26
Hi.  How can I burn a bootable copy of a bootable CD (Dapper live-CD)?  I can copy the files easily but this just creates a data CD, not a bootable one.  I'm using the "CD/DVD creator" feature in Nautilus in Dapper.  Also looked at GnomeBaker.  I have both a CD read/write drive and a DVD read/write drive.  Apologies for such a basic question but I have searched the forum.  Any help appreciated.  

Cheers, Pat.

---

### Post by Arby on 2007-03-26
Gnomebaker should be able to what you need although I don't use it myself. Basically you need to burn the disk as an iso image. This guide [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) explains how to do it. As a general bit of advice, try and burn the disk at a low speed around 4x. People commonly have problems with defective disks from burning at too high a speed.

---

### Post by mcduck on 2007-03-27
Do not copy files from one cd to other, instead you should just 'copy CD'.

In GnomeBaker, go to Tools/Copy Data CD.

---

### Post by Patb on 2007-03-27
Thank you Arby and thank you Mcduck.  

The problem was that I was not burning the disk as an iso image but copying the files.  The "CD/DVD creator" feature in Nautilus does not appear to enable me to create an iso image of the entire bootable disk - the files on it yes, but not the disk.  Nor does it have a facility to "copy CD".

No problem however, GnomeBaker Tools/Copy Data CD worked fine.  It also has a feature to create an image of a data CD.  Thanks again.  

Cheers, Pat.

---

