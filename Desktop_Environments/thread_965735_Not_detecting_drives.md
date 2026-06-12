---
title: "Not detecting drives"
date: 2008-10-31
forum: Desktop Environments
---

### Post by Programmerfromthehood on 2008-10-31
Okay, so today I installed the new verison of xubuntu and I can't find my other partitions, my overall question is just like [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=860391") but I have a different output. So far I have a 100gb hd(really like 88.4gb) and I set aside 40g for xubutu and xp, and 40 for overall media. With the output that sisco311 asked for, I saw this: ```
james@Ender:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
james@Ender:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         623        3668    24466995    7  HPFS/NTFS
/dev/sda2               1         622     4996183+   b  W95 FAT32
/dev/sda3            3669       12161    68220022+   5  Extended
/dev/sda5            3669        6714    24466963+  83  Linux
/dev/sda6            6715       11820    41013913+  83  Linux
/dev/sda7           11821       12161     2739051   82  Linux swap / Solaris

Partition table entries are not in disk order
james@Ender:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=01561cf2-58e8-4e04-bd03-2d2062f4cffb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=15a87fea-8242-413e-9f71-11bf3ce3954f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
So what do I exactly need to do here?



Thanks in advance!

---

### Post by adept_king on 2008-11-01
what is the output of 

sudo blkid        

?

use that command to get the uuid's of the partitions.
i reccomend following what's there and using the uuid's to edit your fstab.

sudo nano fstab #(dont change whats there, just add the partitions that arent showing up)

read this guide carefully:
[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

---

