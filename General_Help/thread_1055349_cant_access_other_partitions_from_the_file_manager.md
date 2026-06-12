---
title: "cant access other partitions from the file manager"
date: 2009-01-30
forum: General Help
---

### Post by richardy on 2009-01-30
Hi,
Cant seem to access other partitions from the file manager (thunar) in xubuntu 8.10. I have xubuntu dual booted with windows. However i can access these partitions if i use applications like abiword/totem which seems a bit odd to me. I checked the preferences in thunar and volume management is turned on. 

The following is the result of sudo fisk -l:
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        3019    22298220    c  W95 FAT32 (LBA)
/dev/sda3            3020        4864    14819962+   5  Extended
/dev/sda5            4077        4744     5365678+  83  Linux
/dev/sda6            4745        4864      963868+  82  Linux swap / Solaris
/dev/sda7            3020        4024     8072599+  83  Linux
/dev/sda8            4025        4076      417658+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b26b7

the following is from fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=5d55b254-7c82-4ff5-a8f1-e136b3d48524 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=1a615024-1c1b-4247-851a-30601734f932 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

the following is from mtab:
/dev/sda7 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0


Any help would be much appreciated.

Cheers.

---

### Post by Ziggy72 on 2009-01-30
I usually access ntfs files on other file partitions from within ubuntu, so what I suggest may not work.

That said, let us suppose you want to mount files on /dev/sda5 at every boot.

```

sudo cd /media
mkdir sda5 

```

add a line to /etc/fstab:
> 
# /dev/sda5
/dev/sda5	/media/sda5	ext3    defaults	 0       1


Check that this works with
```
sudo mount -a
```

If that doesn't work, it may be that the word "defaults" should be replaced with "relatime,errors=remount-ro" as in your your fstab file for /dev/sda7.

If mounting works, the drive or partition will be visible on your desktop at each reboot.

Give this a try - nothing to lose. If it works ok you'll be able to extend this to access any other disks or partitions you want to explore. For each disk or partition you want to mount and enter in fstab, you'll need to have an appropriate mount point entry in /media.

I'm no expert, but I hope this helps...

---

