---
title: "GRUB, multi-boot, and LiveCD"
date: 2006-05-16
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-05-16
Okay, first I might want to give you the specs on my HDD config. The 100GB is scheduled for reformat sometime soon.

IDE Primary Master: 20GB (Kubuntu, MBR) HDA
IDE Primary Slave: 100GB (NTFS, reformat)

Before I do this. If I install other Linux varieties on the 100GB, is the /boot/grub/menu.lst on HDA1 (ext3, Linux) the file that is edited? That is the GRUB menu, right? So I'd personally edit that one if installing other varieties (as in remove the annoying, recurring Windows XP entry), right?

Second- is it possible to add a Live CD to GRUB, to boot off of that? I have 3 CD Drives- IDE Secondary Master BenQ CD/DVD combo, IDE Secondary Slave LiteOn CD-ROM (the one I want to use in this case), and a SCSI Plextor CD drive. Would I use /dev/hdc or whatever it is for the CD drive?

---

### Post by Sef on 2006-05-16
> Before I do this. If I install other Linux varieties on the 100GB, is the /boot/grub/menu.lst on HDA1 (ext3, Linux) the file that is edited? That is the GRUB menu, right? So I'd personally edit that one if installing other varieties (as in remove the annoying, recurring Windows XP entry), right?

If you added distros, they would be added to GRUB or LILO automatically of the latest distro installed.

> Second- is it possible to add a Live CD to GRUB, to boot off of that? I have 3 CD Drives- IDE Secondary Master BenQ CD/DVD combo, IDE Secondary Slave LiteOn CD-ROM (the one I want to use in this case), and a SCSI Plextor CD drive. Would I use /dev/hdc or whatever it is for the CD drive?

Live CDs are meant to be installed.

---

