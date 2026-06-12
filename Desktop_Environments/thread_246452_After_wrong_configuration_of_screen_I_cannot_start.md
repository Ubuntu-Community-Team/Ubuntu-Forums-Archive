---
title: "After wrong configuration of screen I cannot start Ubuntu"
date: 2006-08-29
forum: Desktop Environments
---

### Post by rodio on 2006-08-29
I have installed in my PC Ubunt 6.0.6 plus Windows XP (dual boot with GRUB). I changed my monitor from 15" CRT to 19" TFT, and run the reconfigure tool:
sudo dpkg-reconfigure xserver-xorg
so the new monitor would be detected (in order to configure 1280x1024 mode). But I did something wrong when configuring, and when restarting the monitor displays an error message (synchronization frequency out of range) and does not work.
I have learned that I have to run again de reconfigure or edit the xorg file and change the frequency values (h and v) according to my monitor specs, but I cannot start ubuntu and do it. Is there some "safe mode" boot which uses some default screen or similar (restore option in GRUB does not work either)?
Thanks in advance

---

### Post by rodio on 2006-08-29
It was my fault; I discovered in other forum that I did not use the Recovery boot correctly; booted with recovery, run again dpkg-reconfigure xserver-xorg (as root, being in recovery mode), introduced the correct frequencies and everything is OK now.

---

