---
title: "Pen drive not detecting in ubuntu working in windows"
date: 2009-05-18
forum: General Help
---

### Post by gauravforyouall on 2009-05-18
Hi... i am facing strange problem my pen drive is not being detected in Ubuntu 9.04, although it is working fine with windows , this is happening with third pen drive in a row with me... i tried to reboot in windows and umount it safely as i read it might casue problem but again it didnt help.... what can i do....
i tried
dmesg|tail and output is
[116511.062662] sd 13:0:0:0: [sdc] Write Protect is off
[116511.062666] sd 13:0:0:0: [sdc] Mode Sense: 23 00 00 00
[116511.062670] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[116511.064801] sd 13:0:0:0: [sdc] 7856128 512-byte hardware sectors: (4.02 GB/3.74 GiB)
[116511.065682] sd 13:0:0:0: [sdc] Write Protect is off
[116511.065692] sd 13:0:0:0: [sdc] Mode Sense: 23 00 00 00
[116511.065701] sd 13:0:0:0: [sdc] Assuming drive cache: write through
[116511.065723]  sdc: sdc1
[116511.300406] sd 13:0:0:0: [sdc] Attached SCSI removable disk
[116511.300544] sd 13:0:0:0: Attached scsi generic sg3 type 0


output of sudo fdisk -l is
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sda2            2433        9729    58613152+   f  W95 Ext'd (LBA)
/dev/sda5            2433        4864    19535008+   b  W95 FAT32
/dev/sda6            4865        4889      200781    6  FAT16
/dev/sda7            4890        6929    16386268+   7  HPFS/NTFS
/dev/sda8            7085        7286     1622533+  82  Linux swap / Solaris
/dev/sda9            7287        9729    19623366   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36273626

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sdb2            4865       19457   117218272+   f  W95 Ext'd (LBA)
/dev/sdb5            4865        9728    39070048+   b  W95 FAT32
/dev/sdb6            9729       14592    39070048+   b  W95 FAT32
/dev/sdb7           14593       19457    39078081    b  W95 FAT32


i am not able to find/figure out whats wrong please help

---

### Post by gauravforyouall on 2009-05-18
any help please!!!

---

### Post by Legace on 2009-05-18
Try to reformat the drive with GParted (backup drive files on Windows first).

---

### Post by gauravforyouall on 2009-05-18
this is happeneing with all pen drives and not the only one. :(

---

### Post by gauravforyouall on 2009-05-18
also gparted is not listing my pen drive

---

### Post by Legace on 2009-05-18
> **gauravforyouall said:**
> this is happeneing with all pen drives and not the only one. :(

Plug in a memory stick and see if it mounts with the following code:

```
sudo mkdir /media/pendrive
sudo mount /dev/sdc1 /media/pendrive
```

If it doesn't work, do (to remove the useless directory):
```
sudo rmdir /media/pendrive
```

---

### Post by gauravforyouall on 2009-05-18
/$ sudo mount /dev/sdc1 /media/pendrive
mount: special device /dev/sdc1 does not exist
also it is not even connecting my mobile with data cable or my digi cam none is being deteced rather shown....

---

### Post by gauravforyouall on 2009-05-18
if i am not wrong i never experienced this problem in intrepid, this is probably happeneing after i moved on jaunty (couple of days back only)

---

### Post by emili01234 on 2009-06-17
> **gauravforyouall said:**
> if i am not wrong i never experienced this problem in intrepid, this is probably happeneing after i moved on jaunty (couple of days back only)

I have the same problem, after upgrade from 8.10 my mp3 player Philips Sa1115 is not recognized anymore. But works fine in windows.
when I run 'lsusb' the device is listed but not in 'fdisk -l' nor '/proc/partitions' and can't be mounted manually.
I think that is a kernel issue, because when I start ubuntu with the old kernel (2.6.27-11), the device is recognized and I can mount it manually.
The problem of booting with the old kernel, is that gnome don't start because the proprietary display driver is not recognized. And I'm so lazy to make it work.
Try booting with the old kernel and see what happens.
I hope that somebody can fix this problem.

---

