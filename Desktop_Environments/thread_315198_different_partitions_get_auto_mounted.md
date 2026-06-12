---
title: "different partitions get auto mounted"
date: 2006-12-08
forum: Desktop Environments
---

### Post by BenWhitey on 2006-12-08
I'm new to linux/ubuntu, so bear with me and sorry about posting in the wrong section first. I didn't see a button to delete it, so i just edited....

Anyway, I'm trying to figure out why this happens and how to prevent it from happening. When I boot up into ubuntu only a few of my hard drive partitions are mounted.

Hard drives:

200GB WD ATA100
--Windows partition (ntfs)
--Files partition (ntfs)
--files partition (ntfs)
--ubuntu partition
--swap

120GB Seagate ATA100
--files partition (ntfs)

300GB Seagate SATA
--files partition (ntfs)

When I boot up into knoppix, all of my partitions are mounted. I've tried using guides i've found via these forums but they haven't helped.

Here is some stuff I thought you might find helpful.

whitey@ubuntu:~$ mount
/dev/hda8 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda5 on /media/hda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda6 on /media/hda6 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
whitey@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
16 heads, 63 sectors/track, 581421 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/sda2 * 2 581421 293035680 5 Extended
/dev/sda5 2 581421 293035648+ 7 HPFS/NTFS

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1275 10241406 7 HPFS/NTFS
/dev/hda2 1276 22868 173445772+ 5 Extended
/dev/hda5 1276 12975 93980218+ 7 HPFS/NTFS
/dev/hda6 19574 22868 26467056 7 HPFS/NTFS
/dev/hda7 19041 19301 2096451 82 Linux swap / Solaris
/dev/hda8 * 12976 18790 46708956 83 Linux
/dev/hda9 18791 19040 2008093+ 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
16 heads, 63 sectors/track, 232581 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/hdb2 * 2 232581 117220320 5 Extended
/dev/hdb5 2 232581 117220288+ 7 HPFS/NTFS

Thanks

---

