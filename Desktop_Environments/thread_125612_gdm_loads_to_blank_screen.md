---
title: "gdm loads to blank screen"
date: 2006-02-04
forum: Desktop Environments
---

### Post by revmoo on 2006-02-04
Hi all, I've been trying to sort this problem out for a while now and it's almost driven me insane, the irc channel has been no help("hurrr check your bios")

**The problem:** GDM loads to a blank screen when my computer boots. I have a cursor and nothing else, no login, nothing. 

**The Solution:**
1. CTRL+ALT+F1, login
2. killall -9 gdm
3. killall -9 Xorg
4. sh NVIDIA-Linux-x86-1.0-8178-pkg1.run
(installs driver)
5. gdm

I have to do this _every single boot_

If I try and startx without reinstalling the driver it usually locks my display and refuses to load(i can blind login to a tty and init 6). I've tried the 8178 and 8174 drivers, same problem with each. I've also tried rm'ing the kernel module, Xorg driver and related files by hand and reinstalling the driver, same problem. I've ALSO tried removing gdm and purging it, and reinstalling. Now the blank screen is black rather than the ubuntu brown but the problem remains the same.

Protip: This problem started when I attempted to get dual monitors working




PLEASE tell me someone out there knows how to fix this problem. I really dont want to have to reinstall ubuntu because of this, but with the hours that I'm spending trying to repair it I might as well spend the time setting up a new system.

---

### Post by revmoo on 2006-02-04
*** update

Found the fix. You need to remove nvidia-glx-something from /etc/rc2.d to fix this problem.

Apparently, if you have the apt-get drivers and you attempt to download and run drivers from nvidia.com it will cause these problems.

I wonder if ubuntu couldnt be fixed so that this condition doesnt occur?

---

