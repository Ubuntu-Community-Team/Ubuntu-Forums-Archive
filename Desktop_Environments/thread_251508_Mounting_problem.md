---
title: "Mounting problem"
date: 2006-09-05
forum: Desktop Environments
---

### Post by bobmario on 2006-09-05
Hello everybody!!!!:confused: 

I have a little problem with a windows partition mounting. I don't know if it's solvable, but i hope so.

I have two partitions in Windows. In the first one there is "Windows" OS and the file system is FAT, and in the second one there are some other files and programs and the file System is NTFS.

We can see the partition table below by using the command "fdisk /dev/hda" :

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         713     5727141    c  W95 FAT32 (LBA)
/dev/hda2            2744        7296    36571972+   f  W95 Ext'd (LBA)
/dev/hda3             714        2743    16305975   83  Linux
/dev/hda5            2835        7296    35840983+   7  HPFS/NTFS
/dev/hda6            2744        2834      730894+  82  Linux swap / Solaris

So i mounted successfully the first one with the command

sudo mount -t vfat /dev/hda1 /mnt/Windows

But i wasn't able to mount the second partition, the NTFS one. In fact by editing

sudo mount -t ntfs /dev/hda2 /mnt/Programs

the following error message appeares:

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


It seems that it doesn't recognise the file system type, but i'm sure that it's NTFS. I tried also by putting vfat again, but the same error message is returned (but this time the error message is right).
If i try to don't specify the type, or to put it in autmoatic way (-t auto) it returns the error message:

mount: you must specify the filesystem type.

I hope that someone had the same problem (and solved it already), and have a nice suggestion!!!

Bye, thank you!!!

bobmario

---

### Post by taurus on 2006-09-05
Okay, you need to edit your /etc/fstab to mount both with read/write to your FAT and read to your NTFS.  Open a terminal and edit it with

```
gksudo gedit /etc/fstab
```
Scroll down at the end and add the following two lines...

```

/dev/hda1   /media/fat   vfat   defaults,umask=0000   0   0
/dev/hda5   /media/windows   ntfs   defaults,umask=0222   0   0

```
Then, create two mountpoints with

```

sudo mkdir /media/fat /media/windows
sudo mount -a <-- to mount them...

```

---

