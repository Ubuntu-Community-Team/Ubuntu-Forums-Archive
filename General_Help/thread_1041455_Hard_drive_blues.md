---
title: "Hard drive blues"
date: 2009-01-16
forum: General Help
---

### Post by birdmanJR on 2009-01-16
hey guys, ive been out of the Microsoft pocket for about six months now and i love it. There is nothing that can amount to freedom. The only problem i seem to have that i have not fixed already is my harddrive situation. I am using an HP dv8135nr which includes two physical 100gb (or so they say, its more like 95 a piece) hard drives. I can not tell if i have mounted both or if i am on seperate partitons in one drive. Recently i had to reinstall ubuntu due to ushare screwing up my system and this is sorta how my hardrive looks according to gparted. i have included a couple screen shots. Basically i would like to know how to have both hard drives in use by ubuntu to have a total disk space of 200 gb. Any help is much appreciated. 

Ubuntu Forums Rock

"Hatred Outlives the Hateful"

---

### Post by jnw222 on 2009-01-16
if wanting the terminal 

sudo fdisk -l 
(could you post that)

sudo mount 


to combine, next time u can use LVM on the alt. install cd

---

### Post by birdmanJR on 2009-01-16
sure here you go

jr@Birdman:~$ sudo fdisk -l
[sudo] password for jr: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdedc5ce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         120      963868+  83  Linux
/dev/sdb2             121       12161    96719332+   5  Extended
/dev/sdb5             121       11788    93723178+  83  Linux
/dev/sdb6           11789       12161     2996091   82  Linux swap / Solaris
jr@Birdman:~$

---

