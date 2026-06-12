---
title: "can't able to boot my laptop"
date: 2011-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spkanu on 2011-10-12
i have encounter
problem that when i boot my
computer it will show the blank
screen n in that
grub rescue>
this command promt will appear. so i
couldn't get to access my syatem
could u please help me out

---

### Post by Smooth Operator on 2011-10-12
are you dual booting?...
 
try super grub!!!
 
or your original windows7 disc
boot to disc
run system repair tools
open cmd
type
in following commands
 
bootrec /fixboot
bootrec /fixmbr

---

### Post by garvinrick4 on 2011-10-12
Do you have both Windows and Ubuntu on this machine?
Put in a live cd (install cd using Try Ubuntu) and open a terminal
put in this code and post results. 
```
sudo fdisk -l
``` Lower case L

---

### Post by spkanu on 2011-10-12
no i have only ubuntu in my system but can't open.
when i start the computer the command window appears and say that there is 
no such partition and 
grub rescue>
i will try it with live cd but it will show only demo of ubuntu....:confused:

---

### Post by garvinrick4 on 2011-10-12
> i will try it with live cd but it will show only demo of ubuntu.That is not a demo we can fix your boot from there most of time. It is for repairing
your install. 
Open terminal with the live cd and run the code in previous post. I am trying to fix you up.

---

### Post by spkanu on 2011-10-12
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069115

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            5738       30401   198113549+   f  W95 Ext'd (LBA)
/dev/sda2   *           1        5737    46081024   83  Linux
/dev/sda5            5738       18485   102398278+   7  HPFS/NTFS
/dev/sda6           18486       30401    95715238+   7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by garvinrick4 on 2011-10-12
Put in your live cd again  and open a terminal again and copy and paste these:
```
sudo mount /dev/sda2 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
```
```
sudo umount /mnt
```
```
sudo reboot
```
Boot into Ubuntu
```
sudo update-grub
```
Should be booting now.

---

### Post by spkanu on 2011-10-12
i do as u said...
the boot problem is sovled  thanks...
but it will not showing my drive.. means D and E
what can i do for use that drive

---

### Post by garvinrick4 on 2011-10-12
> i do as u said...
the boot problem is sovled  thanks...
That is good.
> but it will not showing my drive.. means D and E
what can i do for use that drive 	 
If you open a window to show you your documents or Downloads or Picutures
you will see on left side of that Nautilus Window your other partitions on that drive. You have Linux on one partition and 3 other partitions on that one drive.
## If using Gnome will be under the Places drop down menu.

---

### Post by The Sorrow on 2011-10-12
you may have lost the partition or its not mapped to a logical drive (A: B: C: etc)

---

### Post by spkanu on 2011-10-12
it will not showing on the nautilus window. but i will find it in my drive on a folder named as windows and dos.
but doesn't seem like the partition!!!!

---

