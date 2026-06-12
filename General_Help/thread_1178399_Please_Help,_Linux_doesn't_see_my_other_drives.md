---
title: "Please Help, Linux doesn't see my other drives"
date: 2009-06-04
forum: General Help
---

### Post by mavaddat on 2009-06-04
Hi, everyone. I have a little problem I wonder if somebody might be able to help me with.

Although they used to be there, my Linux no longer sees my other hard drives (three) or CD-ROM drive. It sees the 'File System' drive and the floppy drive, but not the others. I cannot mount them or even see them in the GUI. I'm not sure how to get them back into Linux.

There were two changes I made before this occurred. First, I recently fixed an issue with low-graphics mode by running this code:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
```And second, I installed a *chrooted* 32-bit environment by running [this tutorial](http://ubuntuforums.org/showthread.php?t=24575).

I am running kernel 2.6.24-23-generic x86_64 GNU/Linux on XUbuntu.

---

### Post by CaptainMark on 2009-06-04
do they appear with the```
 sudo fdisk -l
```

---

### Post by mavaddat on 2009-06-04
> **CaptainMark said:**
> do they appear with the```
 sudo fdisk -l
```Yes! They do. Here's the result:```
mavaddat@mavaddat-desktop:~$  sudo fdisk -l
[sudo] password for mavaddat: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x197e0bf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sda5               2       14593   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x024002a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7475    60042906    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb92cb92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4863    39062016    7  HPFS/NTFS
/dev/sdc2            4864        9729    39086145    5  Extended
/dev/sdc5            4864        9543    37592068+  83  Linux
/dev/sdc6            9544        9729     1494013+  82  Linux swap / Solaris

```However, when I try to ```
mount /dev/sdc5
``` I get```

mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab

``` What does this mean? Is there any hope? *Why does Linux hate my other hard drives?*

---

### Post by merlinus on 2009-06-04
You have to mount a partition to a previously-created mountpoint, e.g.

mount /dev/sda1 /media/windows

---

### Post by colau on 2009-06-04
> **mavaddat said:**
> Hi, everyone. I have a little problem I wonder if somebody might be able to help me with.

Although they used to be there, my Linux no longer sees my other hard drives (three) or CD-ROM drive. It sees the 'File System' drive and the floppy drive, but not the others. I cannot mount them or even see them in the GUI. I'm not sure how to get them back into Linux.

There were two changes I made before this occurred. First, I recently fixed an issue with low-graphics mode by running this code:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
```And second, I installed a *chrooted* 32-bit environment by running [this tutorial](http://ubuntuforums.org/showthread.php?t=24575).

I am running kernel 2.6.24-23-generic x86_64 GNU/Linux on XUbuntu.

```

sudo mkdir /media/MYDRIVE
sudo mount -t vfat /dev/sda1 /media/MYDRIVE
cd /media/MYDRIVE
ls

```

---

### Post by mavaddat on 2009-06-05
> **merlinus said:**
> You have to mount a partition to a previously-created mountpoint, e.g.

mount /dev/sda1 /media/windows> **colau said:**
> ```

sudo mkdir /media/MYDRIVE
sudo mount -t vfat /dev/sda1 /media/MYDRIVE
cd /media/MYDRIVE
ls

```

*Yes!!* Thank you both! That was exactly what I needed to do.

---

### Post by colau on 2009-06-06
Welcome.

---

