---
title: "Where Did I Install Ubuntu"
date: 2009-06-24
forum: General Help
---

### Post by james.brantley on 2009-06-24
[SIZE=3]Alright this may be a crazy question but I just don't know how to do this yet. A few days ago I shrunk my Vista partion and created two additional. One for Ubuntu itself and (I think) one for my data.Could someone please decipher this fdisk for me and explain in plain English what it says?

1. how big is the Vista partition
2. how big is the Ubuntu partition
3. did I set this up properly 
4. is my data in a separate partition like I tried
5. do I have seven partitions for reason

I am having no system problems I just want to learn more about my machine and the volumes of new terminology there is with Linux/Ubuntu. (I'm not doing too bad) Thanks for any help!

[/SIZE]```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39d23778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19939   160153972    7  HPFS/NTFS
/dev/sda2           19939       21945    16111247    7  HPFS/NTFS
/dev/sda3           21946       29189    58183845    f  W95 Ext'd (LBA)
/dev/sda4           29189       30402     9739264    7  HPFS/NTFS
/dev/sda5           28552       29189     5120000    7  HPFS/NTFS
/dev/sda6           21946       28275    50845693+  83  Linux
/dev/sda7           28276       28551     2216938+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000


```[SIZE=3]
[/SIZE]

---

### Post by Legace on 2009-06-24
> **james.brantley said:**
> 1. how big is the Vista partition
2. how big is the Ubuntu partition
3. did I set this up properly 
4. is my data in a separate partition like I tried
5. do I have seven partitions for reason

1. and 2., open Applications -> Accessories -> Terminal, and type in **gksudo gparted** and you'll be able to see the size from there.

If it says you don't have gparted installed, type the following to install Gparted and try again:
```
sudo apt-get install gparted
```

3. There is not right way to set it up, but that looks pretty good.

4. There is no way to tell that from fdisk.

5. You should know that yourself. If you don't need 7 partitions, why do you have 7? I only have 4.


Ubuntu is installed on sda6 and Windows is most likely installed on sda1

---

### Post by Therion on 2009-06-24
> **james.brantley said:**
> 
1. how big is the Vista partition
2. how big is the Ubuntu partition
3. did I set this up properly 
4. is my data in a separate partition like I tried
5. do I have seven partitions for reason
1 & 2:  The size of the partition is the difference between the "Start" and "End" sizes.

3.  I don't know, but I don't think so.  I think you have a couple extra partitions in there, but I'm not sure.  How many partitions did you intend to wind up with, because as of now, you have seven.

4.  We can't tell what data you have where on your hard drive from "fdisk" only what partitions you have and how they were formatted. 

5.  That's a tough one to answer.  I think you want to have one Windows partition, you'll need two for Ubuntu and then it sounds like you want one more (shared?) data-partition.

By way of pure explanation...  Ubuntu sees most everything, including devices, as *folders*, very UNlike Windows.  Hence you see your partitions as if they were folders (e.g. /sda3 etc.)

SCSI disk devices are mapped to the /dev (devices) directory under /dev/sda, /dev/sdb, ... When different disk devices are present, they will be mapped to /dev/sda, /dev/sdb, etc. If, for example, a memory stick and a digital camera are plugged in, the one would be mapped to /dev/sda and the other to /dev/sdb.

/sda1 to /sda4 are Primary Partitions and /sda5 onwards are Logical Partitions inside a/the Extended Partition. You can create only one Extended Partition which could be any between /sda1 to /sda4.

Does that help, or just confuse the hell out of you?

---

### Post by pi.theta on 2009-06-24
The best solution is what Legace said to install gparted and use it´s GUI to understand which partition is what.

As far as the 7 partitions are concerned they may be more because of presence of utility partitions in most notebooks.

And if you want to calculate the size use  this formulae:

size in bytes = (END - START + 1) * 8225280

---

### Post by michy99 on 2009-06-24
sda3 is an extended partition which contains three logical partitions: sda6, sda7, and sda5.

---

### Post by james.brantley on 2009-06-24
[SIZE=2]I have no idea why I have seven partitions I only intended to create two additional for Ubuntu and data. Will the below image help make sense of the seven partitions?[/SIZE][IMG]file:///home/james/Desktop/Screenshot.png[/IMG]

---

### Post by michy99 on 2009-06-24
This is what it looks like to me:

sda1 is your windows partition.

sda4 is your recovery partition to reset your system to the way it came from the factory.

These two are fine and you don't need to do anything to them.

sda2 has the label /home, so I think you were trying to set it up as home, but it is not mounted at /home, which is good, because it is ntfs, and home needs to be ext3 (or ext4). This partition can probably be deleted. Check to see if there is any data there first.

There is a bit of unused space between sda2 and sda3.

sda3 is an extended partition containing (in order) sda6, sda7, unused space, and sda5.

sda5 is labeled 'swap' so you probably meant for it to be the linux swap partition, but it is not. It can probably be deleted.

sda6 is your Ubuntu partition.

sda7 is your linux-swap partition.

I'll give my advice on what to do in the next reply.

---

### Post by michy99 on 2009-06-24
This is what I would do.

1. Make sure there is no data in sda2 or sda5.

2. Delete sda2.

3. Expand sda3 into the free space between sda1 and sda3.

4. Delete sda5.

5. Move sda7 to the end of sda3.

6. Expand sda6 at the beginning and end to fill up the rest of the space.

This is only one possible scenario, but it would get your partitions in an order that makes sense.

---

### Post by james.brantley on 2009-06-24
> **michy99 said:**
> This is what it looks like to me:

sda1 is your windows partition.

sda4 is your recovery partition to reset your system to the way it came from the factory.

These two are fine and you don't need to do anything to them.

sda2 has the label /home, so I think you were trying to set it up as home, but it is not mounted at /home, which is good, because it is ntfs, and home needs to be ext3 (or ext4). This partition can probably be deleted. Check to see if there is any data there first.

There is a bit of unused space between sda2 and sda3.

sda3 is an extended partition containing (in order) sda6, sda7, unused space, and sda5.

sda5 is labeled 'swap' so you probably meant for it to be the linux swap partition, but it is not. It can probably be deleted.

sda6 is your Ubuntu partition.

sda7 is your linux-swap partition.

I'll give my advice on what to do in the next reply.

[SIZE=2]Thanks, that really clarifies things quite a bit for me[/SIZE]. [SIZE=2]You are exactly about the home and the swap file, I did name these two myself within Vista Disk Manager. So it appears to me that Ubuntu names the partitions as it uses them. [/SIZE]

---

