---
title: "[SOLVED] Splitting root partition to make room for home"
date: 2008-03-06
forum: Desktop Environments
---

### Post by jms1989 on 2008-03-06
Hi, I'm wanting to split my root partition for ubuntu but I have two partitions behind it. How would I repartition it without removing the other two?

I want to shrink my root partition and add another after it for my /home partition. I want to shrink root to 15GB and the remaining 55GB for /home. This will ease my upgrades in the future, including upgrading feisty to gusty and eventually hardy. I currently have to backup my entire hard drive in order to upgrade or protect myself from any problems that break my os.

Attached is a screenshot of my current layout.

---

### Post by logos34 on 2008-03-06
Easy.  Just use gparted on the ubuntu live cd to shrink root (the latter can't be mounted when working on it), then create a new ext3 between it and ntfs partition.  Your new /home will be partition hda4.  Use [this guide to make a new separate /home ]("http://www.psychocats.net/ubuntu/separatehome")on hda4.

---

### Post by jms1989 on 2008-03-07
Wouldn't it cause conflicts on the partition table?

---

### Post by logos34 on 2008-03-07
no, it shouldn't.  Gparted will edit the table for you.  But you have to edit fstab.  It's all in the psychocats link I provided.

---

### Post by jms1989 on 2008-03-09
OK, I split my /home directory from my root partition and it works great. I also upgraded Ubuntu in the process.

---

### Post by logos34 on 2008-03-09
Good to hear.  Enjoy. Mark thread as 'solved'.

---

