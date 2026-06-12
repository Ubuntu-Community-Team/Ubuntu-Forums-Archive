---
title: "Adding Windows XP to GRUB menu?"
date: 2005-12-26
forum: General Help
---

### Post by shut on 2005-12-26
Hello,

I installed Ubuntu recently on a whim and with a new HD from Christmas.  I had to install the server version and aptitude ubuntu-desktop.  For some reason during the installation, when GRUB configured itself, it did not recognize my Windows HD.  I would like to be able to choose to boot Windows if need be, and no entry exists in /boot/grub/menu.lst for it.  

The config file is a bit... esoteric, so I am going to ask that someone help me in creating the proper addition to the config file.

```

name@SSSSS:/boot/grub$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/hda2            3917       24792   167686470    7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14759   118551636   83  Linux
/dev/hdb2           14760       14946     1502077+   5  Extended
/dev/hdb5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/hde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/hdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       14946   120053713+   7  HPFS/NTFS


```

I want to boot off /dev/hda1 while maintaining GRUB's integrity (as I've read several forum posts about booting into Windows XP but then not being able to use GRUB).  

The Windows drive is the master to the Linux drive and they're both attached to an ATA/133 card.

Thank you very much.

---

### Post by RaptorRaider on 2005-12-26
Perhaps you can give us a better view of your HDD's configuration through, let's say GParted?

---

### Post by strips on 2005-12-26
Why would GParted give a better view?

I believe /dev/hda1 is your windows boot partition. That will be hd(0,0) if I'm not mistaken.

Add this to your grub config file /boot/grub/menu.lst
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

The code above is what my Ubuntu install generated automatically.

---

### Post by shut on 2005-12-26
[QUOTE=strips]Why would GParted give a better view?

I believe /dev/hda1 is your windows boot partition. That will be hd(0,0) if I'm not mistaken.

Add this to your grub config file /boot/grub/menu.lst
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

The code above is what my Ubuntu install generated automatically.[/QUOTE]

I added this and it told me error 13.  Here is my current GRUB config.

```

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

I get Error 13.  Now I think the root(hd0,0) is wrong, and I think GRUB thinks that it is installed on the first HD, so I'll try mucking around with that, but how do I tell what the root parameters should be?

---

### Post by Sutekh on 2005-12-26
root (hd0,0) isn't wrong if you can boot into Ubuntu, and from fdsik GRUB is definately on the second hard drive

What is the contents of /boot/grub/device.map?

This file tells the GRUB bootloader where each hard drive will be mapped to

This is mine
```

(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb

```
So it tells GRUB that /dev/hda, my first drive should be mapped to hd0, and so on. 

Find out where /dev/hda (your NTFS drive) is mapped to, and then you can change the menu.lst (the #) entry to match (the one strips gave you)
```
title           Microsoft Windows XP Professional
root            (hd#,0)
savedefault
makeactive
chainloader     +1
```

---

