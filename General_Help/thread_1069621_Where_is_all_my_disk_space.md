---
title: "Where is all my disk space?"
date: 2009-02-14
forum: General Help
---

### Post by yossyrian on 2009-02-14
I am not an experienced user, so sorry if this is a no brainer. I installed ubuntu over mandrake a week ago. The HD has about 40 gigs, but after a week I'm being told the HD is full, and when I look ubuntu seems to only be using 3 gigs. I realise this has something to do with the partitions, but I recall allocating the whole disk to ubuntu when I install over mandrake. I tried to download gparted but there is no room so the install failed.  What's the easiest way to bet ubuntu to use the whole HD?

---

### Post by geirha on 2009-02-14
What's the output of this command, run in a terminal?```
df -h
```

There's also a graphical way to view disk usage; Applications -> Accessories -> Disk Usage Analyzer

---

### Post by x33a on 2009-02-14
afaik gparted comes installed with ubuntu.

post the output of
```
sudo fdisk -l
``` apart from what geirha said

---

### Post by SeanTater on 2009-02-14
After df, try these two commands.. They may give a hint to the missing space:
```
sudo du -hs /var/log
```
```
du -h ~/.xsession-errors
```

---

### Post by geirha on 2009-02-14
> **x33a said:**
> afaik gparted comes installed with ubuntu.
The live CD session has gparted installed, but it doesn't get installed to ubuntu by default.

---

### Post by 73ckn797 on 2009-02-14
If you are not familiar with using terminal and want to see the drive. Boot from the Live CD. It has "gparted" and you can "look" at the partition info from there.

It will be under: System/Administration/Partition Editor

---

### Post by yossyrian on 2009-02-15
> **geirha said:**
> What's the output of this command, run in a terminal?```
df -h
```

There's also a graphical way to view disk usage; Applications -> Accessories -> Disk Usage Analyzer

michael@michael-linux:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             2.9G  2.9G     0 100% /
tmpfs                 120M     0  120M   0% /lib/init/rw
varrun                120M  212K  120M   1% /var/run
varlock               120M     0  120M   0% /var/lock
udev                  120M  2.7M  118M   3% /dev
tmpfs                 120M  244K  120M   1% /dev/shm
lrm                   120M  2.0M  118M   2% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   32K  992K   4% /tmp

---

### Post by yossyrian on 2009-02-15
> **x33a said:**
> afaik gparted comes installed with ubuntu.

post the output of
```
sudo fdisk -l
``` apart from what geirha said

michael@michael-linux:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45894588

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         384     3084448+  83  Linux
/dev/sda2             385        4864    35985600    5  Extended
/dev/sda5            4776        4864      714861   82  Linux swap / Solaris
/dev/sda6             410        4686    34354939+  83  Linux
/dev/sda7            4687        4775      714861   82  Linux swap / Solaris
/dev/sda8             385         409      200749+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by yossyrian on 2009-02-15
> **SeanTater said:**
> After df, try these two commands.. They may give a hint to the missing space:
```
sudo du -hs /var/log
```
```
du -h ~/.xsession-errors
```

michael@michael-linux:~$ sudo du -hs /var/log
4.7M	/var/log

---

### Post by yossyrian on 2009-02-15
Thanks for your suggestions so far. It looks like sda6 has all my HD space. I just noticed if I restart, it lists 'other operating systems' as being on sda6. I started that operating system and it failed ('kernel panic'). Basically, I want to destroy other partitions and only use my HD space for ubuntu.I though I'd wiped out everything and made a fresh install, but I guess not.

---

### Post by indeterminate on 2009-02-15
:popcorn:

---

### Post by yossyrian on 2009-02-15
I was able to take away 30 gigs from sda6, so now that is unallocated, but I can't give it to the main partition where ubuntu runs from, gparted won't let me. I'm happy to wipe the HD clean and start over again, if that's the most straightforward way. Would appreciate any suggestions.

---

### Post by yossyrian on 2009-02-15
> **yossyrian said:**
> Thanks for your suggestions so far. It looks like sda6 has all my HD space. I just noticed if I restart, it lists 'other operating systems' as being on sda6. I started that operating system and it failed ('kernel panic'). Basically, I want to destroy other partitions and only use my HD space for ubuntu.I though I'd wiped out everything and made a fresh install, but I guess not.

michael@michael-linux:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45894588

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         384     3084448+  83  Linux
/dev/sda2             385        4864    35985600    5  Extended
/dev/sda5            4776        4864      714861   82  Linux swap / Solaris
/dev/sda6             410         755     2779213+  83  Linux
/dev/sda7            4687        4775      714861   82  Linux swap / Solaris
/dev/sda8             385         409      200749+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by x33a on 2009-02-15
why have you got 3 swap partitions? 

and only 1 is a primary partition, rest are extended. in my opinion, you should reformat.

if you want all space for ubuntu, just make one primary partition for ubuntu, and reserve some space for swap.

---

### Post by geirha on 2009-02-15
There's a nice guide on partitioning at the wiki [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by linux_tech on 2009-02-15
gparted works best for me to manage partitions

---

