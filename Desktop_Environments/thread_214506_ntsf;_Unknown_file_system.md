---
title: "ntsf; Unknown file system"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Najand on 2006-07-12
I have just added a new hard disk to my computer at home and I made two partitions for that. 80 GB of ext3 and 80 GB of ntfs, then I tried to edit the /etc/fstab with the details of the drives and the  mount points (/dev/hdb ==> /media/HDext3 and /media/HDntsf)
however when I go to mount the ntfs partition manually I get the error:

ntfs: Unknown File System

Anyone has a clue? The Computer has just Ubuntu with NO windows on it.

---

### Post by aysiu on 2006-07-12
Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by scxtt on 2006-07-12
why use NTFS at all?

---

### Post by aysiu on 2006-07-12
> **scxtt said:**
> why use NTFS at all?
Yeah, that's a bit confusing, especially if the computer doesn't have Windows installed...

---

### Post by Najand on 2006-07-13
> **aysiu said:**
> Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

FDISK:
```

Disk /dev/hdb: 182.5 GB, 182522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7916    81945715+   7  HPFS/NTFS
/dev/hdb2            7917       16360    81937682   83  Linux
/dev/hdb5           16360       16424      522081   82  Linux swap / Solaris
/dev/hdb6           16425       16489      522081   82  Linux swap / Solaris
```

DF:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2              80G  2.1G   78G   6% /
varrun                506M   76K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  160K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile

```

FSTAB:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
devpts          /dev/pts        devpts  gid=5,mode=620  0 0
tmpfs           /dev/shm        tmpfs   defaults        0 0
proc            /proc           proc    defaults        0 0
sysfs           /sys            sysfs   defaults        0 0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/Windows          ntfs    defaults,nls=utf8,umask=007,gid=46      0 1
/dev/hdb5       none            swap    sw              0       0
/dev/hdb6       none            swap    sw              0       0
```

> why use NTFS at all?

Well, good question, becuase it seems pointless to have an ntsf drive without any windows on it. Actually I have another bootable USB hard-disk with fully installed Windows XP on it, which is not connected to the system. I use it on different computers, so being mobile is a merit for me. I want the ntsf partition for the time, I mount, boot and use the Windows XP from the USB drive, however, I don't see anything wrong with mounting NTFS partitions in Linux. I have been using them on my other Dual boot (Windows+Ubuntu) computer at university. It is even possible to mount macintosh's super secret hfs+ partitions on my other Dual Boot Computer (Mac+Ubuntu PPC), so there shouldn't be any regulations preventing you to mount better supported ntsf file types for mounting.

---

### Post by scxtt on 2006-07-13
why not just use FAT32 on that partition w/ that drive when you use XP?

---

### Post by Najand on 2006-07-13
> **scxtt said:**
> why not just use FAT32 on that partition w/ that drive when you use XP?

The problem is that I have already quite a few GB of data on it and I don't have any intention to reformat it again. Well, it is not a matter of the file types is being supported by ubuntu or not, it is a matter of the problem of mounting them in Linux, whatever they are ntfs, fat32, fat16 or whatever else.

---

### Post by RAOF on 2006-07-13
Why not format **everything** ext3 and use the Windows ext2/3 driver from fs-driver.org :)

Slightly more practically, maybe you should **sudo modprobe ntfs** before trying to mount it?  Perhaps the module isn't loaded.

---

### Post by Najand on 2006-07-13
> **RAOF said:**
> Why not format **everything** ext3 and use the Windows ext2/3 driver from fs-driver.org :)

Slightly more practically, maybe you should **sudo modprobe ntfs** before trying to mount it?  Perhaps the module isn't loaded.

Well, is it really neccessory to reformat everything?

---

### Post by scxtt on 2006-07-13
why don't you try to mount it a bit more generically? (i.e. don't use the 'nls=utf8,umask=007,gid=46' options) ... something like:

mount -t ntfs /dev/hda1 /media/Windows

---

### Post by RAOF on 2006-07-13
> **Najand said:**
> Well, is it really neccessory to reformat everything?
No, only the ntfs partition :)

---

### Post by Najand on 2006-07-13
> **scxtt said:**
> why don't you try to mount it a bit more generically? (i.e. don't use the 'nls=utf8,umask=007,gid=46' options) ... something like:

mount -t ntfs /dev/hda1 /media/Windows

Hmm, I have tried that on the terminal and got the same result. ```
nls=utf8,umask=007,gid=46
``` set  the  owner  and  group  of  the  files  in  the file system. and it is not really related to the filesystems.

---

