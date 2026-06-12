---
title: "GRUB error 2"
date: 2011-01-14
forum: Desktop Environments
---

### Post by xirix404 on 2011-01-14
Hello

I got this error this morning.
I am running ubuntu 10.4 for a while now,
its not a fresh install or an uprade.

Thanks for your help

---

### Post by xirix404 on 2011-01-14
So i am on the live cd right now

I can see mz HD in places but if click on it it tells me

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by xirix404 on 2011-01-14
i have to admit that i am not very familiar with ubuntu yet
i did fdsik

if somebody can see something please help me



Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc878

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120850   970727593+  83  Linux
/dev/sda2          120851      121601     6032407+   5  Extended
/dev/sda5          120851      121601     6032376   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by xirix404 on 2011-01-14
then i tried to mount and i get

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by xirix404 on 2011-01-14
now i am doing this

ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -v /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Group descriptors look bad... trying backup blocks...
Pass 1: Checking inodes, blocks, and sizes

---

### Post by xirix404 on 2011-01-14
Yessssssssssssss 

problem solved after running

 ~$ sudo e2fsck -C0 -f -v /dev/sda1

I am backing up my important files right now to an external drive:D

---

### Post by Rubi1200 on 2011-01-14
Well, I was going to suggest running the boot info script and then working from there.

But, you have solved this without anyone responding; very nice :)

If you still want to post the results of the script we can perhaps offer some other perspectives on the situation.

---

