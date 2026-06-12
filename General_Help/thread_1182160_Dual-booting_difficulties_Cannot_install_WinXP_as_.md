---
title: "Dual-booting difficulties: Cannot install WinXP as Ubuntu boots directly."
date: 2009-06-08
forum: General Help
---

### Post by Kludgejob on 2009-06-08
Hey there - new poster here on the forums. I've recently upgraded from Ubuntu 7.04 to 8.10, and so far I've been quite happy with it. However, I miss the ability to play certain games, and I've had mixed success with WINE, so I decided to attempt a dual-boot set up. I've shrunk my linux partition to make room on my hard-drive, and was planning to install XP into the empty space, and then restore the Grub file. However, even when I choose to boot from CD, with the Win XP system cd in the drive, the computer uses the Grub loader and boots from the hard-drive. The message shown is something like "boot from hd(0,0) and then a long string of numbers. 

I apologize for the vagueness in my post - I'm still learning a lot of the relevant terminology. If someone with a little more experience could help explain things, I'd be very grateful.

KJ.

---

### Post by Shibblet on 2009-06-08
Try disabling your HD as a boot device in BIOS.  Boot from the CD, then load XP on to the HD.

---

