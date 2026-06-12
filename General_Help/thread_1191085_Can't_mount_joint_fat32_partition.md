---
title: "Can't mount joint fat32 partition"
date: 2009-06-18
forum: General Help
---

### Post by Cloggsy on 2009-06-18
The short version is that I cannot mount a fat32 partition on Jaunty.

The long version is that I have a computer running Win XP which started off with a single 40GB hard drive. Having already configured my laptop to dual boot to Windows and Ubuntu ***and share a fat32 partition so that files can be accessed from both operating systems*** I wanted to replicate this on my desktop. A second 160GB hard drive was fitted to provide a home for Ubuntu and the shared partition. Jaunty now up and running OK in its own partition but Windows can now access the shared partition but Ubuntu cannot.

I followed the thread shown at:

[URL="http://ubuntuforums.org/showthread.php?t=1188343&highlight=mount"]

but something hasn't worked!

The shared partition on the second hard drive is known as sdb6. Having followed the thread I can access to read/write something known as sdb6 except it doesn't show files saved from Windows or vice versa. Another puzzle is that, although I know the partition is 101GB (confirmed in both Windows and GParted), the size of sdb6 as shown in media/ is 41GB - suspiciously the same size as it reports sdb5 which I know to be 1GB as it's the swapfile.

Any ideas?

---

### Post by MyR on 2009-06-18
can you post the output of
```
sudo fdisk -l
```

peace

---

### Post by Cloggsy on 2009-06-18
Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8f4c8f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5005    40202631    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb850b850

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6079    48829536   83  Linux
/dev/sdb2            6080       19457   107458785    5  Extended
/dev/sdb5            6080        6201      979933+  82  Linux swap / Solaris
/dev/sdb6            6202       19457   106478788+   b  W95 FAT32

---

### Post by swerdna on 2009-06-19
Make a place to mount the drive, perhaps a directory called win_drive loacted at /home/john/win_drive. Then open a console and enter this command:
```
mount -t vfat -o uid=john,gid=users,utf8=true /dev/sdb6 /home/john/win_drive
```
Of course, change john to your username.

Alternatively, if you want to mount it permanently, put this line in fstab:
```
/dev/sdb6 /home/john/win_drive   vfat   uid=john,gid=users,utf8=true 0 0
```

FFI reference: [HowTo mount FAT32 (VFAT) partitions with read-write access]("http://opensuse.swerdna.org/susefat32.html")

---

### Post by Cloggsy on 2009-06-22
Bingo! Worked ok - and I've been able to place permanent links to the partition on the desktops of the other users.

Thanks.

---

### Post by Cloggsy on 2009-06-22
Bingo! Worked ok - and I've been able to place permanent links to the partition on the desktops of the other users.

Thanks. (again!)

---

### Post by swerdna on 2009-06-22
> **Cloggsy said:**
> Bingo! Worked ok - and I've been able to place permanent links to the partition on the desktops of the other users.

Thanks.

Glad to hear -- especially the "bingo!". :popcorn:

---

