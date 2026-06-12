---
title: "Places, (un)mountable volumes, missing CDROM"
date: 2010-01-30
forum: Desktop Environments
---

### Post by kalherak on 2010-01-30
Hi,
I'm using Ubuntu 9.10 with Gnome.
In "Places" menu, there are various disk volumes that are not user mountable,
are not mentioned in /etc/fstab and do not belong to Ubuntu installation, also there is a "Floppy" item although there is none in the computer.
On the other hand there is no "CD-ROM" item that would enable me to mount/umount the CD.

How can I get rid of the useless items in the Places?
How can I add there the CD-ROM?
Is there any user-friendly alternative how to mount/umount & eject CD-ROM (not automounting)?

The "mount /dev/cdrom0 /media/cdrom0"  works fine, the mounted CD appears in places and
disapears when unmounted.

/etc/fstab:
  /dev/cdrom0  /media/cdrom0  udf,iso9660  ro,user,noauto

Regards

---

