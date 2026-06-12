---
title: "Invisible partitions!"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Pjotr123 on 2006-09-24
Two ext3-partitions are invisible to Ubuntu!
What happened is this:

Recently I made an image of the Ubuntu partition and of the Windows partition, both on DVD+R's. Then I deleted all partitions on the hard disk using the Gparted Live CD (Gnome Partition Editor), and created a series of new partitions. This new series differs from the old one.

Then I put the images of Ubuntu and Windows back on their respective partitions. In Ubuntu I manually changed the list in /etc/fstab, in order to fit the new situation. Now everything runs smoothly, except for one thing: Ubuntu doesn't recognize two ext3-partitions!

I fear there must be an error in fstab. The lines in my fstab are as follows (hda1 is Windows, hda8 is Ubuntu, the invisible partitions are hda9 and hda10):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda9     ext2    defaults,errors=remount-ro 0       1
/dev/hda10      /media/hda10    ext2    defaults,errors=remount-ro 0       1
/dev/hda11      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


What can I do to make hda9 and hda10 visible in Ubuntu?

Greeting, Pjotr.

---

