---
title: "Two New Drives"
date: 2009-04-07
forum: General Help
---

### Post by Rodney9 on 2009-04-07
I have two new sata 320Gig drives plus Ubuntu on a 160G and a old 80G with xp.

What would be the best way to use these two new 320's for backups between Ubuntu (mostly, 99% Ubuntu) and xp.
I thought to synchronize the two, but what format would be best, fat32 is old and can't use over 4G files, xp can't see ext3, is ntfs trustworthy, at least Ubuntu can read/write it.

Rodney

---

### Post by dargaud on 2009-04-07
I could never stand dual-booting, so my recommandation would be to run XP in VirtualBox in Ubuntu, where you can export the disks via SMB/CIFS, but of course it depends on your needs. For me XP is necessary because of various USB hardware not supported by Linux, and VirtualBox passes the devices transparently onto XP, even when Linux has no idea what it is. This is true genius.

---

### Post by LORD_PoLvO on 2009-04-07
ive never had any major issues with NT file system, its not as elegant as ext3 but it gets the job done, if the way your suggesting is how you wish to go about things then you should have no major issues.

but... imo i agree with the above post less stressing around

---

