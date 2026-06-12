---
title: "XP on Dell mini 9?"
date: 2009-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by achefsalad on 2009-03-18
Is it possible to install Windows XP on the mini 9? Right now I have Ubuntu on my Dell mini 9. I can't partition the hard drive to make room for XP. Granted, there is only about 5GB on the disc. When i click on the part of the disc I want to partition, the resize/move option isn't available. This part of the disc is mounted, does that have anything to do with it? I tried to unmount it, but, "only root can unmout." Obviously I'm computer illiterate. Please help!

---

### Post by ugm6hr on 2009-03-18
Yes, you can install XP on the Mini 9; it is available to buy with XP.

You cannot resize the Ubuntu partition from within Ubuntu; you have to use a LiveUSB / LiveCD version (that includes GParted).

---

### Post by armandh on 2009-03-19
I dual boot XP and 8.10 Ubuntu on my mini9, 16Gb hdd
I doubt you can load it to much less than 8Gb with out drive compression or a stripped down XP

I used a live partition editor to create an 8Gb primary active partition for XP and then loaded NON dell XP. I then loaded NON dell ubuntu, selecting the guided "use largest unpartitioned space" option. Ubuntu created a home and swap partitions in an extended partition and loaded Ubuntu. Grub worked as expected.

dell restore disks wipe and copy a machine specific OS to the Hdd

---

### Post by achefsalad on 2009-03-19
> **ugm6hr said:**
> Yes, you can install XP on the Mini 9; it is available to buy with XP.

You cannot resize the Ubuntu partition from within Ubuntu; you have to use a LiveUSB / LiveCD version (that includes GParted).

I was using GParted. Believe me, I had to wait like 20 min for it to, "Scan all devices."

---

### Post by armandh on 2009-03-19
parted magic needed only a few moments on mine ????

---

### Post by notwen on 2009-03-19
> **achefsalad said:**
> I was using GParted. Believe me, I had to wait like 20 min for it to, "Scan all devices."

I believe he was saying that you will not be able to successfully use GParted to resize your SSD while using the install on said SSD.  You will need to used a bootable USB drive or external optical drive to boot a LiveCD and resize your SSD partitions within a LiveCD environment.

Check out [Unetbootin]("http://unetbootin.sourceforge.net/") in order to make a USB drive mimic a bootable LiveCD.  =]

---

