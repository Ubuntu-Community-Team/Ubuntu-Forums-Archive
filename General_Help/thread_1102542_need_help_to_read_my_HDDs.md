---
title: "need help to read my HDDs"
date: 2009-03-21
forum: General Help
---

### Post by mikelpsk8 on 2009-03-21
hi.
something happend to my pc today. actualy my windows are broken so i decided to completly switch to uduntu, but before formating i want to transfer some of my data via ubuntu live CD (or my already installed ubuntu)to my second HDD wich is NTFS without OS
but i cannot open it.
also i cannot open my windows disk.
i am not able to log in in windows to make a normal shut down cuz they stuck at loading screen.
any external ways to open those HDDs?
please help me.

ps. 
this is my first post in this forum ;P

---

### Post by taurus on 2009-03-21
While in Ubuntu LiveCD, open a terminal and post the output of these commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by mikelpsk8 on 2009-03-21
so. i typed it and i got this msg 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13d713d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       44560   357928168+   7  HPFS/NTFS
/dev/sda2           44561       48641    32780632+   f  W95 Ext'd (LBA)
/dev/sda5           44561       47110    20482843+  83  Linux
/dev/sda6           47111       47366     2056288+  82  Linux swap / Solaris
/dev/sda7           47367       48641    10241406   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0222

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281    7  HPFS/NTFS
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1005M  2.4M 1003M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1005M  2.4M 1003M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1005M     0 1005M   0% /lib/init/rw
varrun               1005M  100K 1005M   1% /var/run
varlock              1005M     0 1005M   0% /var/lock
udev                 1005M  2.8M 1002M   1% /dev
tmpfs                1005M  104K 1005M   1% /dev/shm
rootfs               1005M   35M  971M   4% /
/dev/scd0             700M  700M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                1005M  




and i still cannot open my HDDs :(:(
any other idea?

---

### Post by taurus on 2009-03-21
Mount the three partitions from your first harddrive, /dev/sda, and the second harddrive, /dev/sdb, as

```
sudo mkdir /media/sda1 /media/sda5 /media/sda7 /media/sdb1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
sudo mount -t ext3 /dev/sda5 /media/sda5
sudo mount -t ext3 /dev/sda7 /media/sda7
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by mikelpsk8 on 2009-03-21
thx for help.
i kinda followed your steps and i also tried a command 

sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

and suddenly everything started to work :)

---

### Post by sandyd on 2009-03-21
> **mikelpsk8 said:**
> thx for help.
i kinda followed your steps and i also tried a command 

sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

and suddenly everything started to work :)
A note :

When NTFS partitions are shutdown improperly (computer crashed or something) you will HAVE to force it to load by manually typing in the mount commands via terminal. Ubuntu, by default does not mount improperly shutdown NTFS partitions.

---

### Post by mikelpsk8 on 2009-03-22
thank you for help guys.
you realy saved.
now i hope to find and setup all drivers properly

---

