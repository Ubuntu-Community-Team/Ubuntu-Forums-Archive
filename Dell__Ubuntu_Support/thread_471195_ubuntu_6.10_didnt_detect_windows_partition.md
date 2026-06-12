---
title: "ubuntu 6.10 didnt detect windows partition"
date: 2007-06-11
forum: Dell  Ubuntu Support
---

### Post by light-angel on 2007-06-11
hi! I'm new in the linux world and i recently installed ubuntu linux 6.10 and i had no problems doing it, but when i finished the installation it didn't detect the windows partition (ntfs) at all.

it doesn't even appear on the media folder as unmount :confused:

---

### Post by hasimir44 on 2007-06-12
I installed automatix2, then used that to install the ntfs read/write support - super easy..

or you could follow this guide:  

[http://www.arsgeek.com/?p=675](http://www.arsgeek.com/?p=675)

first thing I'd do though is to make sure that the partition at least shows up in an fdisk list:

```
sudo fdisk -l
```

---

### Post by light-angel on 2007-06-13
this is what i get when i insert the code on:

light-angel@Sunrise:~$ sudo fdisk
Password:
Sorry, try again.
Password:

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
light-angel@Sunrise:~$


i cant identify which hard drive is  wich :S

---

### Post by camarojones on 2007-06-13
I know that Fiesty shows my windows partition as "disk" under the file browser. I just double-click it to mount.

as far as a command, you need to use SUDO PARTED, or GPARTED (which is a GUI) to see the other partitions.

---

### Post by rscott5 on 2007-06-13
> **light-angel said:**
> this is what i get when i insert the code on:

light-angel@Sunrise:~$ sudo fdisk
Password:
Sorry, try again.
Password:

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
light-angel@Sunrise:~$


i cant identify which hard drive is  wich :S

You made a mistake in what you typed in above. It should have been this, which will then show you all of the drives and partitions:

```
sudo fdisk -l
```

You just missed the -l part which will list them all.

---

### Post by light-angel on 2007-06-15
light-angel@Sunrise:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        6886    55271632+   7  HPFS/NTFS
/dev/sda3            6887        9300    19390455    f  W95 Ext'd (LBA)
/dev/sda4            9301        9726     3421845   83  Linux
/dev/sda5            6887        8798    15358108+  83  Linux
/dev/sda6            8799        9181     3076416   83  Linux
/dev/sda7            9182        9300      955836   82  Linux swap / Solaris
-----------------------------------------------------------------------------------------------
this is what i get when i put the command you ask me for.

another thing is that i cant really see the hard drive in the media folder like some of the guys told me, because it doesn't appear.

is there some rare commad i can use to detect the ntfs partition ?

---

### Post by light-angel on 2007-07-13
thanx for the tutorial!

it helped a lot. Although it detects the window partition i have to mount it every time i login, is there any way to make an automount or something?

---

