---
title: "Video acceleration"
date: 2006-01-28
forum: Desktop Environments
---

### Post by meimato on 2006-01-28
I've got a Radeon 9500; some months ago I installed the fglrx drivers, and got my acceleration.
After the upgrade to kernel 2.6.12-9 and new version of fglrx the acceleration suddenly disappeared; also videos and dvds now look pixelated and doesn't run smoothly as before...
I tried reconfiguring xorg (with sudo dpkg-reconfigure xserver-xorg), but nothing...

I've got breezy, upgraded from the "old" 2004.10 and 2005.4.

---

### Post by meimato on 2006-01-28
When I run

sudo depmod -a ; sudo modprobe fglrx
(from the Ubuntu Starter Guide)

I get the following:

FATAL: Module fglrx not found.

---

