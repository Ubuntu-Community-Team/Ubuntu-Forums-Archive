---
title: "Upgrading filesystem to ext4"
date: 2008-12-29
forum: General Help
---

### Post by pmalvr on 2008-12-29
Hi, 

My hdd configuration right now is this:
/ as ext3 (the root and also the boot partition as the same time)
/home as ext3
swap

I just noticed that it was released the kernel version 2.6.28 with ext4 final support. Now, the thing i would like to know is how can i upgrade mine partitions to ext4. Can i make it for the root partition also, will i be able to boot from it?  

Thanks in advance

---

### Post by cariboo on 2008-12-29
If you want to use ext4, you would be better off installing Jaunty as you need the latest kernel which is 2.6.28-4 and grub doesn't support booting from ext4, so you would need to install grub2. The problem is that Jaunty is pretty broken as far as graphics go as the new Xorg server doesn't support any of the restricted drivers. I'm using Jaunty,   but I have held off installing the new Xorg server until there is support for the restricted drivers.

Jim

---

### Post by albandy on 2008-12-29
or make a /boot partition with ext3 and migrate the others to ext4

---

### Post by pmalvr on 2008-12-30
> **albandy said:**
> or make a /boot partition with ext3 and migrate the others to ext4

So, what kind of hdd partition schema do you recommend me? having in mind also the sizes for each partition.
 
Note: I have a 150G hdd.

---

### Post by sdennie on 2008-12-30
To really see the best results from ext4 you'll actually need to completely reformat your machine to ext4 (excluding the /boot partition which should remain ext2 or ext3).  As stated above, you'll need a 2.6.28 kernel to get a "stable" version of ext4.  You will be able to mount your root partition as ext4 as long as you make sure that you have the ext4 module in /etc/initramfs-tools/modules but, it may not work right (See: [https://bugs.launchpad.net/bugs/309762](https://bugs.launchpad.net/bugs/309762)).  I went through this process after 2.6.28 came out and it was painful (especially on Hardy), error-prone and not something I recommend trying.  Unless your needs for ext4 are really pressing, if at all possible I'd try to wait until Ubuntu supports it natively.

---

### Post by raldz on 2009-01-14
Once we have the final Ubuntu 9.04 with full ext4 support, my question is...


How do I migrate my /home partition (currently ext3) to ext4 without losing data...


Note: I always do a clean install on my root partition with new Ubuntu releases.. which means on Ubuntu 9.04 I will be using ext4 as the default for the root partition..

---

### Post by bodhi.zazen on 2009-01-14
> **raldz said:**
> Once we have the final Ubuntu 9.04 with full ext4 support, my question is...


How do I migrate my /home partition (currently ext3) to ext4 without losing data...


Note: I always do a clean install on my root partition with new Ubuntu releases.. which means on Ubuntu 9.04 I will be using ext4 as the default for the root partition..

[http://www.ibm.com/developerworks/linux/library/l-ext4/index.html](http://www.ibm.com/developerworks/linux/library/l-ext4/index.html)

---

### Post by Aphoxema on 2009-01-15
> **raldz said:**
> Once we have the final Ubuntu 9.04 with full ext4 support, my question is...


How do I migrate my /home partition (currently ext3) to ext4 without losing data...


Note: I always do a clean install on my root partition with new Ubuntu releases.. which means on Ubuntu 9.04 I will be using ext4 as the default for the root partition..

The only way I would even consider doing it is copy everything from the partition to another one, format it and move everything back onto it. If something goes wrong with the copy, don't format. If something goes wrong with the format, you lose nothing.

---

### Post by raldz on 2009-01-16
thanks for the reply.. got it..

---

### Post by solwic on 2009-01-16
> **cariboo907 said:**
> If you want to use ext4, you would be better off installing Jaunty as you need the latest kernel which is 2.6.28-4 and grub doesn't support booting from ext4, so you would need to install grub2. The problem is that Jaunty is pretty broken as far as graphics go as the new Xorg server doesn't support any of the restricted drivers. I'm using Jaunty,   but I have held off installing the new Xorg server until there is support for the restricted drivers.

Jim

Wonder if that means they're adding the DRI2 thing to fully support ATI video?  I heard it was being introduced in Jaunty.  

Can't think of any other decent reason to mess with X.  

*crosses fingers*

---

