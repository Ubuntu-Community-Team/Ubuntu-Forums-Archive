---
title: "inspiron 1420"
date: 2008-03-05
forum: Dell  Ubuntu Support
---

### Post by grossaffe on 2008-03-05
I'm trying to install Ubuntu 7.10 Gutsy Gibbon 64-bit onto my dell Inspiron 1420 (not N) and i want to tri-boot it with XP and Vista.  right now i'm dual-booting Vista/XP using Vista Boot Pro, and last i had heard, that was not compatible with grub.  anyways, here's my problem: I already installed the OS, but i can't start it up in normal mode, it'll just give me a blank screen.  problem #2, as stated previously, i heard Vista Boot Pro was not Compatible with grub, and now i am experiencing it.  so basically, right now, i have 3 operating systems on my computer, none of which are useable (i could restore my xp/vista boot-loader if i so pleased, but i'd rather figure out how to get Ubuntu working first.  so, any suggestions?

edit:
this is weird, It turns out that Ubuntu Loads up just fine, but under Grub, i can't select the Ubuntu boot to boot it, i have to try to boot the "Windows Vista/Longhorn" which will load the Vista/XP boot menu.  from there, if I try to boot to XP, i get an error, and if i try to boot to Vista, i boot Ubuntu.

---

### Post by natehall on 2008-03-05
By default Dell preloads 32 bit Ubuntu on the 1420n. If the issue is because of 64 bit software[ this thread here]("http://ubuntuforums.org/showthread.php?t=368607") should help

---

### Post by grossaffe on 2008-03-06
> **natehall said:**
> By default Dell preloads 32 bit Ubuntu on the 1420n. If the issue is because of 64 bit software[ this thread here]("http://ubuntuforums.org/showthread.php?t=368607") should help

nah, that's not the problem.  after a bit of playing around, i was able to get everything working.  I got ubuntu on grub, and vista/XP together on the Vista bootloader (and then there's plain XP also on grub that doesn't work).  doesn't matter, though, i have all my OSes working now.

---

### Post by sefs on 2008-03-11
Please write a how to on what you did. 

Thanks.

---

