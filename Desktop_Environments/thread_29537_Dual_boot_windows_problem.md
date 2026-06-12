---
title: "Dual boot windows problem"
date: 2005-04-24
forum: Desktop Environments
---

### Post by CARGANZAR on 2005-04-24
Hi having trouble getting my system to dual boot ive tried but keep getting error messages when trying to mount. :-? 

Here is a copy.

john@john:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists

I have 2 hdd's ubuntu on main drive and trying to get windows 98FE rubish on slave to open in a window if possible or just setup wright (win xp pro disc dead xp home wont let me install a new computer to it so cant install this and not buying another copy from M$) this is the partition list table.

Disk /dev/hda: 20.0 GB, 20020396544 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2491    20008926    c  W95 FAT32 (LBA)

Unfortunatley i need windows to load games and for work.

Can anyone help.

---

### Post by nad on 2005-04-24
If you are having trouble booting into your windows operating system, please search these forums for your answer. There are several threads relating to your problem.

If you are trying to access your fat32 partition, simply double click the link on your desktop or the drop down menu Places -> Computer (Disks).

---

### Post by CARGANZAR on 2005-04-24
[QUOTE=nad]If you are having trouble booting into your windows operating system, please search these forums for your answer. There are several threads relating to your problem.

If you are trying to access your fat32 partition, simply double click the link on your desktop or the drop down menu Places -> Computer (Disks).[/QUOTE]

Unfortunatley it doesnt show up on Places -> Computer (Disks). However I can boot windows if I disable the hdd with ubuntu on it through the bios.

It will also boot windows if i swap the boot order on the bios.

Ubuntu still doesnt show the slave hdd with the windows instalation I have looked through loads of related topics on the forum and various other places as I have been trying to get this to work for a couple of days but nothing seems to work or be quite wright, could it be that I installed win98fe after ubuntu and on my slave drive?  ](*,) 

This wall is making my head sore.

---

