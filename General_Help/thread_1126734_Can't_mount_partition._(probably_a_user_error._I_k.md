---
title: "Can't mount partition. (probably a user error. I know.)"
date: 2009-04-15
forum: General Help
---

### Post by Bushido989 on 2009-04-15
I decided to install another distro over my vista partition which, thanks to ubuntu, had gone unused for some time now. I went through with the installation, making the partitions along the way. The grub menu.lst it proposed wasn't exactly the same format as ubuntu's but I figured I'd find something on google about adding ubuntu to the menu.lst in said format. Anyways...to my surprise, when I rebooted, I was presented with the same grub menu I always get...

I boot into Ubuntu, figuring I'll just add the new distro to the current grub...I can't even mount the sucker. 

```
jason@jason-laptop:~$ sudo mount /dev/sda1 /mnt
Failed to read last sector (386347112): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

Any help would be greatly appreciated.

---

### Post by taurus on 2009-04-15
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Bushido989 on 2009-04-15
**fdisk -l**
```
jason@jason-laptop:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa913a913

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23927   192193596   83  Linux
/dev/sda2           24050       30267    49946085   83  Linux
/dev/sda3           30268       30401     1076355    5  Extended
/dev/sda4           23928       24049      979965   82  Linux swap / Solaris
/dev/sda5           30268       30401     1076323+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 4075 MB, 4075290624 bytes
7 heads, 6 sectors/track, 189513 cylinders
Units = cylinders of 42 * 512 = 21504 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             196      189514     3975680    b  W95 FAT32

```

**blkid**
```
jason@jason-laptop:~$ sudo blkid
/dev/sda1: UUID="7900E6F6356E7853" TYPE="ntfs" 
/dev/sda2: UUID="e9837c58-31ca-4c35-8d49-7814169c3830" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="9baf23df-0611-4a89-a704-ad270750c1b9" 
/dev/mmcblk0p1: UUID="3433-3236" TYPE="vfat"
```

**cat /etc/fstab**
```
jason@jason-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e9837c58-31ca-4c35-8d49-7814169c3830 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9baf23df-0611-4a89-a704-ad270750c1b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

**df -h**
```
jason@jason-laptop:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              47G  5.1G   40G  12% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M   76K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M   96K 1003M   1% /dev
tmpfs                1003M   84K 1003M   1% /dev/shm
lrm                  1003M  2.0M 1001M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/mmcblk0p1        3.8G  2.3G  1.5G  61% /media/disk

```

---

### Post by taurus on 2009-04-15
Is there anything on /dev/sda1 right now or is it an empty partition?

---

### Post by Bushido989 on 2009-04-15
> **taurus said:**
> Is there anything on /dev/sda1 right now or is it an empty partition?

I installed another distro to it...or atleast it should have. just like it SHOULD be ext4...

---

### Post by taurus on 2009-04-15
Let's see if you can mount it as ext3 filesystem.

```
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
df -h
```

Which "other" distro that you've installed on /dev/sda1?

---

### Post by Bushido989 on 2009-04-15
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

and the log confirms the lack of ext3 filesystem on sda1. 

I put arch on there. The install went fine on a virtual machine but I didn't consider dual booting or installing over an ntfs partition.

---

### Post by taurus on 2009-04-15
If you installed arch with virtual machine, it means you should already have either windows or another Linux distro running off /dev/sda1!  

Perhaps your best bet right now is to use gparted and wipe clean /dev/sda1.  Then, format it to ext3 and see if you can mount it again.

---

### Post by Bushido989 on 2009-04-16
Thanks for the help. I should have wiped the partition with gparted first. That was the problem. 

Wiping a partition to install over it, at least on an ntfs partition, doesn't work with the arch installer. The ntfs partition was perfectly intact. I wiped it, did another install (which thanks to Virtual Box I do with my eyes closed.) 

Now its just a matter of adding ubuntu to the new menu.lst that I installed with Arch, the format looks a little different but I'm sure I'll find something on the arch forums. 

You sir have been a tremendous help. Thanks again. ;)

---

