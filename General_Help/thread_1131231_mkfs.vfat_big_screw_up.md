---
title: "mkfs.vfat big screw up"
date: 2009-04-20
forum: General Help
---

### Post by dElo on 2009-04-20
Hey,

I did the most dumb thing Ive ever imagine Id do.
Until about an hour ago I had a 500GB SATAII disk divided on 3 partitions:
Ext3(UBU8.10), NTFS (XP), NTFS (W7).

For some reason I cannot even understand I was trying to change my USB drive to FAT32 to make it bootable and run mkfs.vfat /dev/sda.

When I realized what I had done it was too late and it had alredy finished.

Now my NTFS (XP) partition appears as blank and there is information there I need to recover (449.1GB partition).

I dont even know where to start. Can I get some help?

---

### Post by dElo on 2009-04-20
I read a bit about it and with testdisk I seem to have changed something back:

>   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54603   438598566    7  HPFS/NTFS
/dev/sda2           54604       57153    20482875    7  HPFS/NTFS

Furthermore, the 20gb W7 partition appears fine. But the 450gb partition is still showing as empty.

---

### Post by dElo on 2009-04-20
Bump?

My testdisk looks like this, Im really lost: [http://img15.imageshack.us/img15/4379/screenshotsbr.png](http://img15.imageshack.us/img15/4379/screenshotsbr.png)

---

