---
title: "Impossible to mount USB + Authentificaiton is required to unmount USB"
date: 2014-03-30
forum: Desktop Environments
---

### Post by Julien_Drouin-Bouf on 2014-03-30
Hello

I'm not sure if I'm in the good section... I'm beginner

I have a bug with all my external harddrives (USB). It seems to I'm not anymore the owner-manager of those. When I insert one, I receive the following message :

> Impossible to mount JULIEN
Device /dev/sdb1 is already mounted at `/media/usb0'


I can read my usb key and copy documents from my key to my laptop, but I can't add anything to my key, modify or delete. In others words, I lost my rights on my usb keys

When I look at the proprieties of my key, under *Permissions*, it is written "root" under *Owner* and *Group*. In the botton of the window, it is written :

>  You are not owner of this element, you can't change permissions


When I eject it, I receive :

> Authentificaiton is required to unmount Patriot Memory (/dev/sdb1) mounted by another user

And I have to give my password

Sudo fdisk -l gives me (I hope you will understand french ! I can translate if needed) :
```
julien@Voyageur:~$ sudo fdisk -l
[sudo] password for julien: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x0001067e

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Étendue
/dev/sda5          501760   976771071   488134656   8e  LVM Linux

Disk /dev/mapper/ubuntu--vg-root: 496.6 GB, 496597204992 bytes
255 têtes, 63 secteurs/piste, 60374 cylindres, total 969916416 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x00000000

Le disque /dev/mapper/ubuntu--vg-root ne contient pas une table de partitions valable

Disque /dev/mapper/ubuntu--vg-swap_1 : 3200 Mo, 3200253952 octets
255 têtes, 63 secteurs/piste, 389 cylindres, total 6250496 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x00000000

Le disque /dev/mapper/ubuntu--vg-swap_1 ne contient pas une table de partitions valable

Disk /dev/sdb: 31.0 GB, 31029460992 bytes
55 têtes, 55 secteurs/piste, 20034 cylindres, total 60604416 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0xc3072e18

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sdb1            8064    60604415    30298176    c  W95 FAT32 (LBA)

```

In /etc/fstab, it is written :
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/dm-0 :
UUID=5e20e7cd-46f9-41fe-84e4-8d542ceda440    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=c4287d64-95ac-4b88-9ad6-dc6be2db0f27    /boot    ext2    defaults    0    2
#Entry for /dev/dm-1 :
UUID=a84f58e7-0793-471d-929e-a0dce08cd5f8    none    swap    sw    0    0

lsusb gives me :```

julien@Voyageur:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 17ef:1003 Lenovo Integrated Smart Card Reader
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 13fe:4100 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. BCM2045B (BDC-2) [Bluetooth Controller]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

By the way, my USB mouse works normally

I don't really know what I could have done to disturb my system... the only thing that comes to my mind, it was 2 months ago, when the bug approximately appears, I played in the terminal and change settings about the group vbox of my Virtual Machine... but I'm not sure about it and it's foggy

I'm on Saucy 13.10
My laptop is a Thinkpad Lenovo T61p

uname -a gives me :```

julien@Voyageur:~$ uname -a
Linux Voyageur 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Thank you for your help !

Julien

---

### Post by coffeecat on 2014-04-27
I have only just come across this 3-week old unanswered thread and I see that you have not logged in since posting, but in the hope that you do see this post, I probably have the answer.

This:

> **Julien_Drouin-Bouf said:**
> ```
impossible to mount JULIEN
Device /dev/sdb1 is already mounted at `/media/usb0' 
```

Tells me that you have probably installed the app usbmount, which will have broken the USB automounting functionality built into the system. If you have, uninstall usbmount and you will probably find that your problem goes away. The app usbmount is designed for GUI-less systems - mostly servers. Don't try to use it with desktop installations. You will run into exactly these problems.

---

### Post by Julien_Drouin-Bouf on 2014-04-27
Oh gosh ! It works :)
I've simply delete usbmount with terminal and now my usb key works properly

Thank you very much for your help coffeecat ! I was going to transfer my 100 gig of data through a LAN cable to another cable and then make a fresh install of 14.04... much simpler now

---

### Post by coffeecat on 2014-04-28
I'm glad that helped. 

Good luck!

---

