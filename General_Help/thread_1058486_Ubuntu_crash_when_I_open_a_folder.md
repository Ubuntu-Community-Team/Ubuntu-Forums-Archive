---
title: "Ubuntu crash when I open a folder"
date: 2009-02-02
forum: General Help
---

### Post by steavy on 2009-02-02
When I try to open a file inside a directory for a NTFS partition ubuntu freezes :S I can access every other directory in my NTFS partition it just happens with one directory and all the others in it. They were working fine the last time I accessed them.

Maybe a part of my NFTS got damage, is there a way to repair it? I tried copying those files into a directory in the ext3 partition, but it fail too :(

Need some help please.

---

### Post by mgol on 2009-02-02
The best tool for repairing NTFS filesystems is... Microsoft Windows restore console. I think that if You maintain a NTFS partition, You actually have Windows...

Just enter the restore console (or what its name is) and type:
```
chkdsk /r PARTITION_LETTER:
```
then reboot to Windows at least once, and then back to Linux.

Or You don't have Windows?...

---

### Post by steavy on 2009-02-02
I dont have Windows installed but I got the CD. I just did the chkdsk and the NFTS had errors that were repaired. But I am still not able to access those files :( I cant even make a backup because I cannot copy them.

If I could I would rather convert my NTFS partition to ext3, but I cannot make a backup of the files. Any suggestion?

---

### Post by Crafty Kisses on 2009-02-02
> **steavy said:**
> When I try to open a file inside a directory for a NTFS partition ubuntu freezes :S I can access every other directory in my NTFS partition it just happens with one directory and all the others in it. They were working fine the last time I accessed them.

Maybe a part of my NFTS got damage, is there a way to repair it? I tried copying those files into a directory in the ext3 partition, but it fail too :(

Need some help please.

What are the results of this command?
```
sudo fdisk -lu
```

---

### Post by steavy on 2009-02-02
Hi codename thanks for the help. This is the result:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      144584       72261   de  Dell Utility
/dev/sda2          144585   227930219   113892817+   f  W95 Ext'd (LBA)
/dev/sda3       227930220   234436544     3253162+  db  CP/M / CTOS / ...
/dev/sda5   *    41110398   227930219    93409911    7  HPFS/NTFS
/dev/sda6          144711    39311054    19583172   83  Linux
/dev/sda7        39311118    41110334      899608+  82  Linux swap / Solaris

Partition table entries are not in disk order


/dev/sda5 is the one with the problem

---

### Post by mgol on 2009-02-02
It's somehow strange that sth like that freezes the whole system. Maybe this is a DMA issue? Try to invoke:
```
sudo hdparm -d1 /dev/sdXY
```
(X is the disk letter (a, b, c etc.) and Y is the partition number) and then try to access this folder? I don't think this is it as You have problems with the same folder all the time, but it won't harm to try...

Another guess - does the name of the directory You can't access contain some strange, not ASCII symbols?

I'm pretty sure it's advisable to run Windows once after repairing the filesystem, but as You don't have it installed, maybe try to run dosfsck? (I won't give You the guarantee it will not destroy anything as it's an open tool to repair non-open filesystem...)
```
sudo dosfsck -ar /dev/sdXY
```

---

### Post by Crafty Kisses on 2009-02-02
Do you know if the files in that folder are big? Also when it "freezes" can you move your mouse?

---

### Post by steavy on 2009-02-02
The files are not big and dont have any symbols.

I tried this:

```
sudo hdparm -d1 /dev/sdXY
```

but got this:

```
/dev/sda5:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

And also tried this:

```
sudo dosfsck -ar /dev/sda5
```

but got this:

```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 0.
```


This problem is weird :(

---

### Post by mgol on 2009-02-03
The only thing I can think of is that You could run this restore console from MS again and try to copy or move the contents of that directory into another place. But I'm not sure if their 'security' attitude allows to do such things in this console.

---

### Post by steavy on 2009-02-03
OK Ill try that, thanks again

---

### Post by Bonsanto on 2009-02-12
My ubuntu crashes too ... I have NTFS too but I don't get errors when I try this "sudo fdisk -lu" Welll I am not sure I am noob in Ubuntu.

> Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros, 156301488 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xcc468e8e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disco /dev/sdb: 80.0 GB, 80060424192 bytes
255 cabezas, 63 sectores/pista, 9733 cilindros, 156368016 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x13051305

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *          63   156344579    78172258+   7  HPFS/NTFS

Disco /dev/sdc: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros, 156250000 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x08000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *          63   156232124    78116031    7  HPFS/NTFS


If you don't believe me please watch this.

---

