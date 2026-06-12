---
title: "no option to boot to ubuntu"
date: 2012-01-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nighthail on 2012-01-16
Hi i'm an ubuntu newbie here..

I just created a dual boot for windows 7 and ubuntu 11.04. it has completed successfully but after the installation, there's no multi-boot option so my laptop boots directly to windows.

Here's how I partitioned my hard drive (I didn't put the exact details as I don't remember exactly)

System Reserved (NTFS)
Windows 7 (NTFS)
ext4, /boot (250MB)
swap area (2GB)
ext4, / (10GB)
ext4, /home (60GB)

I installed the boot loader I believe under dev/sda5 which is the partition i created for /boot. Sorry not sure how to explain it correctly. Hope you can help.

I tried checking several forums with related problems but I'm not sure if I got it right because it appears to have different solutions...

---

### Post by adityamagadi on 2012-01-17
when you turn on your laptop hold down the shift key or keep hitting the down arrow you should get your menu then boot into ubuntu and install the grub. or try using the ubuntu essential tools on your ubuntu DVD.

---

### Post by nighthail on 2012-01-18
> **adityamagadi said:**
> when you turn on your laptop hold down the shift key or keep hitting the down arrow you should get your menu then boot into ubuntu and install the grub. or try using the ubuntu essential tools on your ubuntu DVD.
 
 
I tried that but didn't work. Still booted up to straight to windows.

---

### Post by carl4926 on 2012-01-18
I wonder why you used a /boot
It's not necessary and especially not for new users

You should install grub to sda
That will write it to the MBR

I'd recommend you have

System Reserved (NTFS)
Windows 7 (NTFS)
swap area (2GB)
ext4, / (10GB)
ext4, /home (60GB)

Redo the install, use the partitioner to delete all the linux partitions in the extended space and recreate
swap
/
/home

---

### Post by nighthail on 2012-01-18
Oh, I did that the first time and yes, it did worked. But for some reasons, ubuntu got corrupted so i deleted the ubuntu partition. Unfortunately I wasn't able to boot to windows after that as well. I thought my MBR got deleted too that's why I created a /boot partition and reinstalled both windows and ubuntu. Anyway, if that is how it will work then I'm gonna go ahead and reinstall it that way. Thanks so much!

---

### Post by carl4926 on 2012-01-18
A /boot partition isn't a requirement
Typically Ubuntu doesn't create one.
If you do. The boot flag has to be on it and grub written to it

---

### Post by carl4926 on 2012-01-18
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg)

---

