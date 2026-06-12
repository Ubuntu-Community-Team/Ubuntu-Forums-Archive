---
title: "From Ubuntu to Xubuntu"
date: 2010-12-11
forum: Desktop Environments
---

### Post by Ogatai on 2010-12-11
Hello, i have a problem, i have an old computer (256 RAM, Pentium 4 processor), i installed in it the UBUNTU 10.10 and it was heavy, so i start to read in forums and it seems that the best thing i should do is change to Xubuntu (wich i did), but i had a problem, i got the Xubuntu package trough synaptics and installed it, in Ubuntu i had no problem reading the content of my hard drive (2 parts, one for OS and the other for storing info), but once i installed the Xubuntu package, i couldn't read that part anymore, actually, i can't see it anymore, in the ARCHIVE SYSTEM (Sistema de Archivos en español) there's only the floppy drive and the USB devices a plug in...

can i do something to get that info back? or at least see my disk?, it's like i lost my virtual part...

thanks

PS: i'm a begginer (if that's not obvious), so please help me step-by-step...

---

### Post by vangop on 2010-12-11
Hi!
Can you check if the partition is ok? Run 
$ sudo fdisk -l
And post the results.

---

### Post by Ogatai on 2010-12-11
> **vangop said:**
> Hi!
Can you check if the partition is ok? Run 
$ sudo fdisk -l
And post the results.

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xcf84cf84

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3824    30714880   83  Linux
/dev/sda2            3825        9728    47423849+   f  W95 Ext'd (LBA)
/dev/sda5            3825        9728    47423848+   7  HPFS/NTFS


if it helps, i didn't understand a single thing... :P

---

### Post by vangop on 2010-12-11
It says you have a primary Linux partition, and a logical NTFS partition.
Was your second partition (lost) NTFS?
Try to mount it
1. sudo mkdir -p /mnt/data
2. sudo ntfs-3g /dev/sda5 /mnt/data

Now open a file browser and navigate manually to /mnt/data. You should be able to see your files.

---

### Post by Ogatai on 2010-12-11
> **vangop said:**
> It says you have a primary Linux partition, and a logical NTFS partition.
Was your second partition (lost) NTFS?
Try to mount it
1. sudo mkdir -p /mnt/data
2. sudo ntfs-3g /dev/sda5 /mnt/data

Now open a file browser and navigate manually to /mnt/data. You should be able to see your files.

[I]ntfs-3g: Failed to access volume '/dev/sda5/mnt/data': No es un directorio

ntfs-3g 2010.8.8 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)[/I]

did i do something wrong?

---

### Post by vangop on 2010-12-11
Yes, there should be a space between /dev/sda5 and /mnt/data.

---

### Post by Ogatai on 2010-12-11
> **vangop said:**
> Yes, there should be a space between /dev/sda5 and /mnt/data.

thanks men its works

---

### Post by vangop on 2010-12-12
You are welcome. I made some short instructions [http://ubuntu-answers.blogspot.com/2010/11/mounting-ntfs-drives.html]("http://ubuntu-answers.blogspot.com/2010/11/mounting-ntfs-drives.html").
It also has instructions on how to make this partition mounted automatically on each boot.

---

### Post by Ogatai on 2010-12-12
> **vangop said:**
> You are welcome. I made some short instructions [http://ubuntu-answers.blogspot.com/2010/11/mounting-ntfs-drives.html](http://ubuntu-answers.blogspot.com/2010/11/mounting-ntfs-drives.html).
It also has instructions on how to make this partition mounted automatically on each boot.

thanks a million men... i guess this problem is SOLVED...

---

