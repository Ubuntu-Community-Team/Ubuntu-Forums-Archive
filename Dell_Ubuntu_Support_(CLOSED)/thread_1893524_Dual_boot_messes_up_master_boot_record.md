---
title: "Dual boot messes up master boot record"
date: 2011-12-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bleutyler on 2011-12-10
Hello Everyone,

I have a Dell Inspiron 1750 Laptop. I came with Win 7 installed. I installed Ubuntu 10.04 64bit with a dual boot and Ubuntu works like a charm. I love it, and this community.

However, with my work sometimes I need to go into Windows. I did it this weekend to use GoTo Meeting, and when I rebooted the box to go back into Ubuntu. I got this error right away before Grub even came up:

"No module name found"

I can reinsert the Ubuntu 10.04 install CD, re-install Ubuntu and I'm back, but I have a new partition. Merging partitions, that is not a problem, I can do that. But I don't want to have to reinstall Ubuntu each time I need to use GoTo Meeting in Windows.

The master boot record is obviously getting played around with, but I can reboot in Ubuntu and I don't get this error. It happens after I boot into Windows. Is there a way to protect it, so that a dual boot machine is possible?

Thank you everyone!!

---

### Post by Rubi1200 on 2011-12-10
Hi,
see post # 11 here:
[http://ubuntuforums.org/showthread.php?t=1343851](http://ubuntuforums.org/showthread.php?t=1343851)

Make sure you have full backups before jumping into anything and ask first if unsure.

---

### Post by bleutyler on 2011-12-17
Thank you very much.  

I followed the link and it solved my problem.

I removed Dell Support Center, and Dell Backup Recovery applications, then when I was in Ubuntu I retinstalled grub 2.

---

### Post by Rubi1200 on 2011-12-17
Excellent! I am glad the solution worked for you.

Enjoy :)

---

