---
title: "windows and grub"
date: 2006-06-23
forum: Desktop Environments
---

### Post by owl on 2006-06-23
Hi guys,
my problem is the following: I have 4 hard disks in my pc. 3 sata and one ata.
a few months ago i had installed breezy on the ata disk, with all the 3 other disks unpluged, windows being already installed on the sata 74 GO.
Then i installed dapper recently, again with all other 3 disks unpluged.
Now i want to add windows in the grub boot menu of dapper, but i tried a lot of different combinations but there is always a mistake, error 12, file system unknown above all. could it be that grub has got problems to handle my 3 sata and my ata disk in the "right" order ? here is the result of fdisk:


Disque /dev/sda: 250.0 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        4377    35158221   83  Linux
/dev/sda2            4378       13252    71288437+   5  Extended
/dev/sda3           13253       15164    15358140    b  W95 FAT32
/dev/sda4           15165       30401   122391202+  83  Linux
/dev/sda5            4378       12887    68356543+  83  Linux
/dev/sda6           12888       13252     2931831   82  Linux swap / Solaris

Disque /dev/sdb: 74.3 Go, 74355769344 octets
255 têtes, 63 secteurs/piste, 9039 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/sdb2            2933        6119    25599577+   7  HPFS/NTFS
/dev/sdb3            6120        9039    23454900    7  HPFS/NTFS

Disque /dev/sdc: 164.6 Go, 164696555520 octets
255 têtes, 63 secteurs/piste, 20023 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système

Disque /dev/hdb: 164.6 Go, 164696555520 octets
255 têtes, 63 secteurs/piste, 20023 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1            4039        4416     3036285    5  Extended
/dev/hdb2   *        4417        6848    19535040   83  Linux
/dev/hdb3            6849        9887    24410767+  83  Linux
/dev/hdb4            9888       20023    81417420   83  Linux
/dev/hdb5            4039        4416     3036253+  82  Linux swap / Solaris
root@grandhibou:/home/grandhibou#

and here is my last try in menu.list (i tried a lot of other combinations already)

title             Windows
  map (hd0) (hd1)
  map (hd1) (hd0)
  root              (hd1,0)
  makeactive
  chainloader        +1

i have heard that windows won't boot if it the hard disk is not recognized as master, and so somebody gave me this advice. But i still can't boot windows from grub because of  errors:
error 12 = invalid device requested
and "file system unkown"

any idea of the problem anybody? :p

---

### Post by Ocxic on 2006-06-23
> could it be that grub has got problems to handle my 3 sata and my ata disk in the "right" order ?

I have found grub does have a problem with this, the only way I have found to fix it, is to set my IDE disk the first disk in ahead of my SATA's in the bios. This works for me regardless of the actual hardwired position of my drives.
Then i don't have a problem.

Also i see that you have an hdb drive but no hda, do you know of a reason for this??

---

### Post by owl on 2006-06-23
well, good question about the fact that i have an hdb disk but no hda! well, i didn't pay any attention on this until now! I did some changes between my hard disks recently, one of the 4 that are pluged in is not even formated by now, but was a windows storage disk a few days ago yet. 
The fact that there isn't any hda anymore might be a possible reason of my problem booting windows from grub.
Your solution is nice, but if i put my ata disk on number 1 position in the bios, it means for me that it will boot on my breezy badger which is installed on that disk!  i would like to boot from the sata disk where my dapper drake is installed, and from the grub menu, being then able to launch windows xp as well (which is installed on another sata disk)

---

### Post by owl on 2006-06-24
I found it out!
the problem was just that i had my dvd burner set as master, so in the 2 lines map (hd0) (hd1
map (hd1) (hd0)
 I changed hd1 by hd2,and also in root (hd1,0) 
it's booting windows from grub now, everything's all right. Hope it can help somebody else as well.

---

