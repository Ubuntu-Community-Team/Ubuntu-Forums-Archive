---
title: "[SOLVED] Unable to install 8.04"
date: 2008-11-28
forum: Desktop Environments
---

### Post by Captain_tux on 2008-11-28
Hello!

Upon trying to install 8.04 (to dual boot with XP) and getting to Step 4 of 7, I dont see a "Guided - resize the partition and use the freed space" option. I see a "Guided - use entire disk." I want to install Ubuntu on my desktop, but I do not want to lose the information stored on XP.

When I choose Manual, it doesnt give me the option to create a new partition on the disk, rather, gives me the option to create a "New Partition Table" on the current disk - meaning that all the data currently on the partition will be lost.

My question is this: At what stage during the installation process will I receive the option to dual boot, that is, when I can I resize the current partition to create partitions for 8.04?

FYI - When using GParted on the Ubuntu LiveCD, a yellow caution icon is displayed next to the primary drive... using GParted on the "SystemRescue CD" gives me that same yellow caution icon. I think that is somehow what's keeping me from being able to partition... am I correct?

Thanks for the help!

---

### Post by taurus on 2008-11-28
Maybe this link helps but ALWAYS backup your personal files in windows first before you play around with resizing.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Captain_tux on 2008-11-28
> **taurus said:**
> Maybe this link helps but ALWAYS backup your personal files in windows first before you play around with resizing.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Taurus - Thanks for the link (very useful!)... and also for the heads up on backing up my info! 

I think the hard drive on my HP desktop is somehow jacked up (as indicated by the yellow caution icon) and not letting me partition it. I'm gonna run  QtParted from Knoppix and see what happens.

I'll report back.

---

### Post by taurus on 2008-11-28
Maybe it's a good idea to boot into windows and defrag the harddrive a couple of times before you try to resize it with gparted.

---

### Post by Captain_tux on 2008-11-29
> **taurus said:**
> Maybe it's a good idea to boot into windows and defrag the harddrive a couple of times before you try to resize it with gparted.

Yet another good tip, Taurus! I ran a defrag yesterday... I'll run another one tonight and see what happens.

Thanks!

---

### Post by falcon61102 on 2008-11-29
When you go through the install process, if you select Guided: Use entire Hard Disk, Ubuntu will erase everything currently on your HD and replace it with Ubuntu.  There should be another option for the guided install that will seperate the drive and allow you to do a dual boot system.

Also, make sure that your drive is not mounted when you attempt to partition/resize it, that may be the cause of the caution icon.

---

### Post by Captain_tux on 2008-11-30
YAY! 

I did it! Well, with the help of Taurus & Falcon (as they both gave me great pointers and made me think of other ideas). :KS

After a series of **defragments**, **chkdsk**, **chkdsk /f** and a ton of reboots on XP, I "fixed" my hard drive to the point where I was able to install Ubuntu. I used **Knoppix 5.1** (QtParted) to create the initial partition, then used **SystemRescueCD** (GParted) to further partition the Linux partition into **/**, **swap** and **/home** (I mention the different distros because there were things I was able to do with **Knoppix** that I wasn't able to do with **SystemRescueCD** and vice versa).

After playing around with the Live CDs of Ubuntu & Kubuntu 8.10, I settled with the special edition of Ubuntu 8.04 from Linux Format magazine [LXF 107 - July 2008] because of the extra packages they included.

I must say, I'm really impressed with how far Ubuntu has come since 2005. The initial installation can still be tricky for the newest of converts, but with features such as Wubi, the migration of settings and documents from Windows (and a ton of others that I can't think of at the moment because it's way past midnight on the east coast and I'm absolutely tired!)... the sky is the limit!

But, yes... I can finally say I'm officially a member of the Ubuntu Community!

:popcorn:     :guitar:

*(And in my best Elvis impersonation... thank you, thank you very much!)* :lolflag:

---

