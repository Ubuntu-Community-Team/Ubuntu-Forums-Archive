---
title: "Kubuntu starts forever"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Owdy on 2005-08-03
It takes minutes to boot, 5-8 minutes. Is this normal? It jams in to places; 'Starting ubuntu' and Starting RAID devices'.

---

### Post by jasmuz on 2005-08-03
What hardware specifications are you using?

---

### Post by Owdy on 2005-08-03
Well, its old pc, Duron 1,2. RAM 512. Motherboard Asustek A7V133-C

---

### Post by Owdy on 2005-08-04
[QUOTE=jasmuz]What hardware specifications are you using?[/QUOTE]
 [http://koti.mbnet.fi/oskunoma/valokuva2.png](http://koti.mbnet.fi/oskunoma/valokuva2.png)

Could this be related. What are those mysteroius drives? I have to hard drives in this pc.

---

### Post by jasmuz on 2005-08-05
I dont understand how many mountable partitions you have and how they got there...but they arent slowing you down, how fast is the clocking speed on your machine?

---

### Post by Owdy on 2005-08-05
[QUOTE=jasmuz]I dont understand how many mountable partitions you have and how they got there...but they arent slowing you down, how fast is the clocking speed on your machine?[/QUOTE]
 Hod do i check that?

---

### Post by Owdy on 2005-08-05
Does this help?


>> sudo fdisk -l /dev/hda 


***
Levy /dev/hda: 20.5 Gt, 20547841536 tavua
255 päätä, 63 sektoria/ura, 2498 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit
    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/hda1   *           1        1021     8201151    7  HPFS/NTFS
/dev/hda2            1997        2498     4032315    f  W95 Laaj (LBA)
/dev/hda3            1022        1996     7831687+  83  Linux
/dev/hda5            2043        2498     3662788+   7  HPFS/NTFS
/dev/hda6            1997        2042      369432   82  Linux swap / Solaris

Osiotaulumerkinnät eivät ole levyjärjestyksessä
***

 /etc/fstab

***
 # /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 /dev/hda3       /               ext3    defaults,errors=remount-ro 0
    1
 /dev/hda6       none            swap    sw              0       0
 /dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
 /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

***

---

### Post by Owdy on 2005-08-05
Btw, i dont have any RAID devices, so why its starts them? How do i stop that?

---

