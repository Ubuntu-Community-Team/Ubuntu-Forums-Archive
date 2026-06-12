---
title: "Just a little advice"
date: 2005-10-15
forum: Desktop Environments
---

### Post by mrmcctt on 2005-10-15
I'm waiting for my Breezey cds to arrive in the mail.  When they do, I want to do a clean install off the cd.  (Just feel better that way)

The one thing I didn't do during the rc install is make a separate /home directory.  I would like to do that with the new install.  

I have a 60GB hdd in my laptop.  I freed up about 20GB for the Ubuntu partition and had Ubuntu automatically set the "/" and swap files.  This is what my current fdisk -l looks like. 

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4685    37632231    7  HPFS/NTFS
/dev/hda2            4686        7185    20081250   83  Linux
/dev/hda3            7186        7296      891607+   5  Extended
/dev/hda5            7186        7296      891576   82  Linux swap / Solaris

```

My questions are
     1. How difficult will it be to partition the Ubuntu partition to, say, 10GB for "/", 913Mb for Swap (which is what Ubuntu set it to by default) and the rest to /home?
     2.  What /dev/hdxx number should I use for /home or does Ubuntu do this for me?
     3.  Are there any additional steps I need to take to get Ubuntu to recognize /home when the install is done?

I've seen how-to's on making a /home partition after the install has been done and the basic how-to for installation which only shows "/" and swap.  I haven't seen anything that seems to match what I want to do.

---

### Post by zekolas on 2005-10-15
When you are installing ubuntu choose the option to manually partition the disk. Then simply create a partition with a mount point of "/" and a partition with a mount point of "/home", and it should reconize the prevouse swap partition.

---

### Post by mrmcctt on 2005-10-15
Thank you for the reply.  Just want to clearly understand a couple of things.

I assume (you know what that means:rolleyes: ) that when I do these partitions that Ubuntu's partition manager will assign the /dev/hdxx number automatically?

Will is also mount that partition or will I have to do some tweaking at first boot up to see it?

---

### Post by mrmcctt on 2005-10-15
Ok.  I started an install just to see what the partition manager looked like again.

What I intend to do in the new install is delete the "/" and swap partitions.

I then want to manually create a "/" partition using 50% of the existing freespace and make it a primary partition.

I will add a "swap" partition of 913Mb (which is what Ubuntu does if I "automatically" configure partitions) and make it a logical partition.

I then want to make a "/home" partition using "max" for the size input (which by my understanding will use the rest of the available free space).  I am not sure whether to set that partition as "Logical" or "Primary".

I will then make sure the windows partition contains the boot flag.

Is this correct and what should I set the "/home" partition to, primary or logical?

Thanks

---

### Post by mrmcctt on 2005-10-15
Bump

Just to see if I can find out how to add the /home folder.  Logical or primary, I'll work the rest.

Thanks

---

### Post by mcduck on 2005-10-15
You should check this site about installing ubuntu with windows, I don't think it could be explained better: [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by mrmcctt on 2005-10-15
Thank You for your reply.

This does not ansewr the question I have, though.  I have done the install with the "Automatically Set Partitions" entry.

What I want to do is take my 60GB hdd, give 20GB to Ubuntu and do a kind of "custom" partition.

I would like the following:

"/" = 10 GB
"Swap" = 913 Mb (Ubuntu default for my system with 384Mb RAM)
"/home" = Remaining Free space on drive

The "/" should be a Logical Partition (Per the "Automatically Set Partitions" entry)

The "Swap" should be an "Extended Partition" (Per the "Automatically Set Partitions" entry)

What I don't know is:

     1.  Do I set the "/home" partition as a Logical or Extended Partition?
     2.  Will I have to do some tweaking to get Ubuntu to recognize the "/home" partition?
     3.  Does the "NTFS" Partition keep the boot flag?

---

### Post by mcduck on 2005-10-15
1: I don't think it matters whatever you choose. Only thing is that the number of primary partitions is limited to 4, but there can be as many logical partitions as you ever wish to have. If you aren't going to make more partitions to that disk then you can make it a primary one.

2. During install you can set that partitions mont point to be /home. Nothing else is needed.

3. Yes, if you don't change it yourself. I suppose it's best to keep the NTFS partition bootable, as it's the first partition on your disk and it's easiest to keep MBR in the beginning of the disk.

---

### Post by mrmcctt on 2005-10-15
[QUOTE=mcduck]1: I don't think it matters whatever you choose. Only thing is that the number of primary partitions is limited to 4, but there can be as many logical partitions as you ever wish to have. If you aren't going to make more partitions to that disk then you can make it a primary one.

2. During install you can set that partitions mont point to be /home. Nothing else is needed.

3. Yes, if you don't change it yourself. I suppose it's best to keep the NTFS partition bootable, as it's the first partition on your disk and it's easiest to keep MBR in the beginning of the disk.[/QUOTE]

Thanks.  That's whatI was looking for.  You've been a great help.

---

### Post by mcduck on 2005-10-15
No problem, glad I could help :)

---

