---
title: "Ubuntu Graphical Problems at Startup"
date: 2008-02-06
forum: Desktop Environments
---

### Post by Ederico on 2008-02-06
Hello,

I'm having problems loading Ubuntu on my desktop. Strange thing is that I don't know what is causing. Apart from setting up a wireless router I don't know what could have caused this.

Basically the loading of Ubuntu is unstable. After I select Ubuntu from GRUB I 'm taken to the login screen, before this didn't even show (gave me a blank screen), occasionally it works fine, now I'm getting a sort of corrupt login screen (it is as if the login page image is loaded only partially).

I cannot understand what can cause this, even worse I don't know how to fix this. I even removed and reinstalled gdm as an attempt, to no avail.

Hope someone could help.

Ederico.

---

### Post by TornadoWarning40422 on 2008-02-07
You might try booting into Ubuntu recovery mode from GRUB, and run fsck. This was a similar problem for me, and running fsck fixed it. If, after going into recovery mode, there is an automatic disk scan, just try, after finishing that, rebooting and see if that fixes it already. If all else fails, say mean things to your computer, then eat something. That always makes me feel better ;)

---

### Post by Ederico on 2008-02-07
That actually seems to have worsened things up, now Ubuntu doesn't load at all and I get a GRUB error 17. Luckily I can access the Windows partitions directly using Super Grub Disk.

---

### Post by PmDematagoda on 2008-02-07
If you can access your Ubuntu disk either through WIndows or the Ubuntu Live CD, can you post the contents of the menu.lst file found in /boot/grub.

---

### Post by Ederico on 2008-02-07
No, I cannot.

Anyways, I reinstalled everything. Luckily I had no important data on the previous Linux partitions (hadn't been long since I had reinstalled it anyways).

---

