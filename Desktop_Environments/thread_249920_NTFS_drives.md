---
title: "NTFS drives"
date: 2006-09-03
forum: Desktop Environments
---

### Post by RobsterUK on 2006-09-03
Hi,

I have just installed Ubuntu on my machine, but I can't get access to my NTFS drives. They appear in the file browser but when I click on them it says "unable to mount the selected volume"

error: device /dev/hdc1 is not removable

error: could not execute pmount

any ideas what the problem could be?

---

### Post by goatflyer on 2006-09-03
Please post the output of the following commands:
 cat /etc/fstab
 fdisk -l /dev/hda
 fdisk -l /dev/hdc

---

### Post by RobsterUK on 2006-09-03
output as follows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
rob@rob-desktop:~$ fdisk -l /dev/hda
Cannot open /dev/hda
rob@rob-desktop:~$ fdisk -l /dev/hdc
Cannot open /dev/hdc

---

### Post by ciscosurfer on 2006-09-03
Post the entire output of fdisk like this```
sudo fdisk -l
```if you only want to see hda or hdc, then you can add it like this```
sudo fdisk -l /dev/hda
sudo fdisk -l /dev/hdc
```

---

### Post by RobsterUK on 2006-09-03
OK thanks

Disk /dev/hda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3139    25213986    7  HPFS/NTFS
/dev/hda2            3140        3708     4570492+  83  Linux
/dev/hda3            3709        3737      232942+   5  Extended
/dev/hda5            3709        3737      232911   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241    7  HPFS/NTFS

---

### Post by goatflyer on 2006-09-03
Yes, sorry I forgot to mention sudo in front of those commands.

sudo fdisk -l /dev/hda

and so on.

I already see you don't have an fstab entry for your windows partition.  You will find this howto very helpful:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by ajgreeny on 2006-09-03
If you want to auto mount windows at boot up add the following line to your /etc/fstab file:-
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

If you want to mount it only when needed, use the following command in a terminal:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I have also added an alias in my .bashrc file in home which means I only type "win" in a terminal and windows is mounted.  A real time saver.  Alias can be used for many long but commonly used commands such as these mounting commands, and I've set up quite a few to speed up some actions.

---

### Post by RobsterUK on 2006-09-03
Thanks goatflyer, I followed the howto and got it sorted

---

### Post by Rhapsody on 2006-09-03
> **RobsterUK said:**
> Hi,

I have just installed Ubuntu on my machine, but I can't get access to my NTFS drives. They appear in the file browser but when I click on them it says "unable to mount the selected volume"

error: device /dev/hdc1 is not removable

error: could not execute pmount

any ideas what the problem could be?
I've been having exactly the same problem trying to a mount partitions (two ext3, one FAT32, one NTFS) using a live CD. How would I go about doing this?

---

### Post by ciscosurfer on 2006-09-03
It is important to remember that you need to first create a directory before trying to mount the device, i.e., [COLOR=DarkRed]sudo mkdir *whatever*[/COLOR] is necessary before proceeding with the following commands.

ajgreeny's advice is completely sound (modify /dev/hda with the name the partition you want to mount; modify /media/windows to wherever you've created your mount point): To mount NFTS partitions, on the command-line, use```
 sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```To mount FAT partitions use ```
sudo mount /dev/hda1 /media/windows -t vfat -o iocharset=utf8,umask=0000
```To mount an EXT3 file system, use```
sudo mount /dev/hda1 /media/linux -t ext3 -o defaults
```Often times, your EXT3 file system will be mounted in your /etc/fstab file to your root directory like this:```
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
```This link will explain everything and is very helpful: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

The man page for mount is also extremely helpful:```
man mount
```

---

