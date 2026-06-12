---
title: "Grub repair not working"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Enigmatic on 2006-06-14
I messed up my partition table with a partitioning software I installed in my XP partition, and had to fixmbr to get XP to boot again. But, I lost grub at the same time.

I ran the command that I found here, but it fails:

setup (hd0,2) 

It gives me this error message - embed /boot/grub/e2fs_stage_1_5 (hd0,2) failed.


What can I do now? I am sure that this is the correct partition as I ran find /boot/grub/stage1/ and that's what it found.

---

### Post by yager on 2006-06-15
You may want to review the info at this link.  It gives all the details for installing GRUB.  [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)

Based on the command you are issuing, you are not putting GRUB in the boot sector which is (hdx,0).  This is most likely the issue as you are trying to put it inside the second partition of the 1st drive.

Even if you were successful, I don't believe the BIOS would ever find it as it can only look for a boot loader in the boot sector of each hard drive.

---

### Post by Enigmatic on 2006-06-15
I managed to get it to work by using (hd0) instead of 0,2.

---

