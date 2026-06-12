---
title: "Ubuntu device naming scheme"
date: 2009-02-14
forum: General Help
---

### Post by Chris_Smith on 2009-02-14
Hi Guys,

I have just compiled a 2.6.22 vanilla kernel to run on Ubuntu v8.04, but have found that when it is booted, it reports that it can't find the root file system as it is looking for devices named hda ..., hdb ... etc, and Ubuntu uses sda ..., sdb ..., etc. The kernel has support for everthing it needs built in so there is no need for an initial file system.
Can anyone please help?
-------------
Best regards,
Chris

---

### Post by hyper_ch on 2009-02-14
you could alter it to the UUID instead. At some page the hdX for ide drives was changed generally to sdX.

I assume the problem is in your fstab, right?

---

### Post by MartyBuntu on 2009-02-14
> **hyper_ch said:**
> you could alter it to the UUID instead.

I did this and it solved a lot of problems for me. I'd recommend at least trying it.

---

### Post by Chris_Smith on 2009-02-18
Thanks for the reply. I have tried using UUID= ... in grub and fstab, but when the kernel boots, it is still looking for a root partiton hdxx (UUID= does work with the original 2.6.24 kernel generic)! The problem may be with the compulation process. I am going to re-check the prerequisites to make sure that no libraries are missing.
-------------
Best regards,
Chris

---

### Post by heindsight on 2009-02-18
what does your grub menu.lst entry for this kernel look like? Perhaps the root option there is incorrect.

---

### Post by Chris_Smith on 2009-02-19
The grub menu.lst entry is root=UUID=e16d15 ...., where e16d15 .. is the hex number that is found in /dev/drive. The original 2.6.24 generic kernel boots ok using this hex number. I don't usually use UUID, as if the partition is backed up using tar.gz from a live CD, and at a later date it is restored, then I have found that the UUID will have changed. This problem does not occur if the partition is defined hdxx, or sdxx. I have tried using hdxx in grub and fstab, and the 2.6.22 custom kernel will boot, but I then find that none of my TV apps are able to get a signal lock on any of the digital channels!

---

