---
title: "[SOLVED] linux-backports-modules-intrepid meesed up system"
date: 2008-11-21
forum: Desktop Environments
---

### Post by nsilva on 2008-11-21
Hey guys I was getting random freezes with caps lock led flashing, googleing around I found a Bug Report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142)) one that suggested installing linux-backport to fix this. 

After installing and rebooting, the system starts a Device Routine check, then it reports that after 14% there was a problem reading the next block. 

It takes me to a Read only file system root command line, and says that fsck died, 
/dev/sda1: UNEXPECTED INCONSISTENCY: Run fsck MANUALLY

The manual fsck says: Error reading Block 3899472(Attempt to read block from filesystem resulted in shot read)

After rebooting many time, Ubuntu booting says "Unclean shut down cleaning again", and /dev/sda device fails again.

Since it is a read only environment I cannot run Apt-get to uninstall it.

Let me know if you have any thoughts

---

### Post by nsilva on 2008-11-21
It is solved now...just following the manual fsck, it gives errors, keep entering Yes and following all the errors from fsck..

---

