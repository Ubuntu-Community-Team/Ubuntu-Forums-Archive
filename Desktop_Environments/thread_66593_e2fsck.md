---
title: "e2fsck"
date: 2005-09-17
forum: Desktop Environments
---

### Post by vincentb on 2005-09-17
All,

when I boot my PC (laptop DELL 510m) I got during the boot a message similar to the following one:

root@ubuntu:/home/ubuntu # e2fsck /dev/hda9
[B]e2fsck 1.35 (28-Feb-2004)
e2fsck: Filesystem has unsupported feature(s) (/home1)
e2fsck: Veuillez obtenir une version plus récente de e2fsck![/B]

The boot it stopped until I push *<ctrl - d>* where everything boots fine.
I am sure the e2fsck is the last version.

my /etc/fstab looks like this :

[INDENT]root@ubuntu:/home/vincent # more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       /home           ext3    defaults        0       2
/dev/hda10      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0[/INDENT]

and my disk is partitioned as follows:

Disque /dev/hda: 60.0 Go, 60011642880 octets
255 têtes, 63 secteurs/piste, 7296 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

[INDENT]Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1               1         261     2096451   de  Dell Utility
/dev/hda2   *         262        1217     7679070    7  HPFS/NTFS
/dev/hda3            1218        7296    48829567+   f  W95 Etendu (LBA)
/dev/hda5            1218        1409     1542208+   7  HPFS/NTFS
/dev/hda6            1410        3322    15366141    7  HPFS/NTFS
/dev/hda7            3323        4151     6658911    7  HPFS/NTFS
/dev/hda8            4152        4980     6658911   83  Linux
/dev/hda9            4981        7147    17406396   83  Linux
/dev/hda10           7148        7274     1020096   82  Linux swap / Solaris[/INDENT]


I am very newbie with Ubuntu. Can you help?

Thanks in advance,

Vincent

---

### Post by scottish_harry on 2005-09-18
I've the same error while booting. After booting with the Live CD i've give the command e2fsck /dev/hdb1 (mine boot drive) and I've got the message clean. So nothing seems to be corrupt.
I've check also my data drive (/dev/hda1) and everything passed ok.

Everyting seems to be ok but I don't like the error and I don't like that I must do Ctrl-D before I can boot.

---

### Post by vincentb on 2005-09-19
I also do not like at all having this message in the middle of the boot and seriously think to get rid of Ubuntu if I can not solve this (and reinstall FC4).

So please any suggestion is more than welcome.

Thanks in advance,

Vincent

---

### Post by alainhenry on 2005-09-19
I had the same problem some time ago.  It is discussed in thread 
[http://www.ubuntuforums.org/showthread.php?t=40197](http://www.ubuntuforums.org/showthread.php?t=40197)

A solution for the problem of E2fsck can be found at :

(see message #6 of the thread)  

[http://www.mail-archive.com/trilug@...g/msg26479.html](http://www.mail-archive.com/trilug@...g/msg26479.html)

Alain

---

