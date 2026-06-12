---
title: "[SOLVED] grub 18 on inspiron 6000"
date: 2008-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sdp0et on 2008-11-03
xp died again for me, so while reinstalling I figured I'd set up to dual-boot with ubuntu 8.10.  After partitioning and installing both OS's, I get a grub 18 error.  

The only advice I can seem to find suggests changing the BIOS setting on HDD detection, but the the 6000 does not seem to have that option.

I've been searching the web for a couple hours trying various suggestions and non work.  Tomorrow I will try rearrainging the partitions to see if settin a smaller one as the first and having grub use that might helpe, but thought I would post tonight and see if anyone can provide some help.  I would appreciate any help or advice.

Thanks,

paul

---

### Post by caljohnsmith on 2008-11-03
Grub error 18 typically means that Grub and/or Ubuntu's boot files are out of the range that your BIOS can access, and that limit is either 8.5 GB or more commonly 137 GB. The best solution usually is to just create a ~200 MB partition at the beginning of your HDD, and then when you install Ubuntu, set that partition with a /boot mount point so all your boot files go there. You can use Ubuntu's partition editor (System > Admin > Partition Editor) to shrink your first partition at the beginning and create a ~200 MB partition for /boot at the beginning of the HDD. Give that shot and let me know how it goes. :)

---

### Post by sdp0et on 2008-11-03
that did the trick, thanks!  I did create a separate boot partition, I just forgot that it had to be closer to the start of the drive.  I've been away from linux from a very long time.

Thanks again,

paul

---

### Post by caljohnsmith on 2008-11-03
Glad that worked OK for you. Cheers and have fun with Ubuntu. :)

---

