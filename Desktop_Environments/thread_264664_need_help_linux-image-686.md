---
title: "need help: linux-image-686"
date: 2006-09-25
forum: Desktop Environments
---

### Post by chajuram on 2006-09-25
Hi,

I recently installed linux-image-686 (for inotify in beagle) and restarted my computer. 

> ritwik@sinha:~$ uname -a
Linux sinha 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Then the computer booted to a 686 kernel and X did not start. I back tracked and have now removed the linux-image-686 and also have commented out the 686 kernels in boot/grub/menu.lst

However now my PS2 mouse does not work any more. 

Any help will be appreciated.

Chajuram.

---

### Post by chajuram on 2006-09-25
The problem solved itself. one of those eternal mysteries....:)

---

