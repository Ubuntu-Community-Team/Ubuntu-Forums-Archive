---
title: "Ghosting Dell D510 Ubuntu 8.10 GRUB GRUB GRUB"
date: 2008-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MyTer on 2008-11-10
Hi

I have installed Ubuntu 8.10 on Dell Latitude D510. Everything works excellent. Since we haveabout 20 more of these I would like to use partimage or Clonezilla to clone it.

It seemed to be working at first, I could boot the first cloned laptop, but the second didn't work. I just get 
GRUB GRUB GRUB GRUB GRUB GRUB forever.

The difference between the first and the second was that the first had previously had Ubuntu 8.10 installed on it.

I have searched for solutions, and tried to reinstall grub, but so far without success. 

For a while I thought that it could have something to do with filesystem format (ext2 - ext3) but I don't think that it's the problem (not sure though).

Please, if anyone can hint me in a new direction :confused::confused::confused::confused:

regards

---

### Post by Coreigh on 2008-11-10
Two key points:
1. This will work best if all the laptops are *identical*
2. You will need to make sure you are cloning the entire drive, number of partitions and order. Otherwise Grub _will_ get confused.

Other than that I have done things like this with success. In my case I was using Norton Ghost.

---

### Post by meierfra. on 2008-11-10
Check out this thread:

[http://ubuntuforums.org/showthread.php?p=4875763]("http://ubuntuforums.org/showthread.php?p=4875763")

---

### Post by MyTer on 2008-11-11
> **Coreigh said:**
> Two key points:
1. This will work best if all the laptops are *identical*
2. You will need to make sure you are cloning the entire drive, number of partitions and order. Otherwise Grub _will_ get confused.

Other than that I have done things like this with success. In my case I was using Norton Ghost.

Thank you for your hints.

I was beginning to wonder if they were identical, even though they are the same model.

I have succeeded with Dell GX240 with the same thing, except I was cloning Windows.

In both cases I used :
dd if=/dev/sda of=/mnt/backup/d510.mbr bs=512 count=1
sfdisk -d /dev/sda > /mnt/backup/d510.sd

to back up mbr and structure

and

dd of=/dev/sda if=/mnt/backup/d510.mbr bs=512 count=1
sfdisk  /dev/sda < /mnt/backup/d510.sd

to restore

and then 

partimage restore /dev/sda1 /mnt/backup/d510.000

It worked perfectly with windows, but not with Ubuntu:(

I'm still trying to convince my collegues that Ubuntu is great, but they are beginning to doubt me:oops:

---

