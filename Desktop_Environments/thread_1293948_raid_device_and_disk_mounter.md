---
title: "raid device and disk mounter"
date: 2009-10-17
forum: Desktop Environments
---

### Post by raven on 2009-10-17
a bit of background
sda contains 4 partitions
/root
/boot
/home
/swap

sdb contains 1 partition for encrypted backup
sdb1

sdc and sdd are in a soft (mdadm) raid1 array as /dev/md0 and working fine

I use the disk mounter applet to mount my removable and my internal disks (ex: sdb)
the disk mounter applet shows the raid1 /dev/md0 with the label name I gave it,
it is perfect

but after reboot I lose it from the disk mounter, but if I invoke the command
```
mkfs.xfs /dev/md0 
```it show automatically in the disk mounter and I can mount it and it will have the label name folder created automatically in /media, when I umount it the folder dissapear.
I do not have to create a folder in /media neither do I have to enter it in fstab
the same as my other internal disks.

question is
how can I have the raid show all the time in disk mounter applet even after booting and
without entering it in fstab ?

---

