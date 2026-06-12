---
title: "Ubuntu freezes @ Splash"
date: 2006-01-01
forum: General Help
---

### Post by SoAxVampyre on 2006-01-01
Hi, I am very new to Linux and decided to try Ubuntu.

The install went smoothly, the program loads, and I can even log on.  However, when the splash screen shows after logging on, the computer hangs and the sound breaks up and repeats over and over again.

I am running Ubuntu AMD64 on:

AMD Athlon64 X2 3800+

ATI Radeon AIW X600

20GB IDE Maxtor drive (Windows)
120GB IDE Seagate drive (Linux)
200GB SATA Maxtor drive (NTFS formatted)

1 gig DDRAM



I have tried editing xorg.conf by doing the following:

Load Ubuntu in Recovery Mode.

at #, type in "sudo nano /etc/x11/xorg.conf"
edit to read "option         noaccel"
save by pressing Ctrl-X

The problem is, when I hit ctrl-x to save, and select save, it gives me a error which basically says "this file/directory does not exist"

I could very well be doing something wrong, any help would be greatly appreciated.

---

