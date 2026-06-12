---
title: "/home issues"
date: 2005-10-15
forum: Desktop Environments
---

### Post by mrmcctt on 2005-10-15
I went ahead and downloaded the new Breezey (didn't take as long as I feared).  I did a clean install of the os and set a "/", "/home", and "swap" partition.

I have looked at [this how-to]("http://ubuntuforums.org/showthread.php?t=46866") and am not sure where to go with it.  This how to explains how to create a new /home partition which I did during install.  It also says that you have to edit your /etc/fstab to mount the new partition.

Here's my /etc/fstab:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

My mount (mount command in terminal)```
rlodge@ubuntu:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
/dev/hda4 on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
rlodge@ubuntu:~$

```

And my fdisk -l:```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4685    37632231    7  HPFS/NTFS
/dev/hda2            4686        5935    10040625   83  Linux
/dev/hda3            7186        7296      891607+   5  Extended
/dev/hda4            5936        7185    10040625   83  Linux
/dev/hda5            7186        7296      891576   82  Linux swap / Solaris

Partition table entries are not in disk order
rlodge@ubuntu:~$

```

---

### Post by mrmcctt on 2005-10-17
I just need to finalize this.  As you can see from above, I have done a clean install of Ubuntu and during the install I made:

     "/" = Primary partition
     "/home" = Primary Partition
     swap = Logical Partition

I checked in the [How To Move Home]("http://ubuntuforums.org/showthread.php?t=46866") how-to and asked if I needed to do this if I made a /home at mount.  I got a reply that I still had to manually move my /home/username directory to the /home partition.

Before I did this I also did a df on my /home/username directory and this is what I got: ```
rlodge@ubuntu:/$ df /home/rlodge
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda4              9882856    336200   9044628   4% /home

```

Isn't this telling me that my /home/username directory is mounted on the /home partition?  I would like to be sure before I go mucking around trying to move a directory that doesn't need to be moved and really goof something up.

Thanks

---

