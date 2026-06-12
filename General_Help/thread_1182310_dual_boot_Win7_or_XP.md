---
title: "dual boot Win7 or XP"
date: 2009-06-08
forum: General Help
---

### Post by Joshinator on 2009-06-08
Hey, I was wondering if it is possible to dual boot Win7 or XP without having to wipe my current ubuntu 9.04 installation. I am just wondering incase I ever want to do it. Thanks.

---

### Post by keplerspeed on 2009-06-08
yes you can. Firstly you need to have a partition to install xp/win7 onto. You can do this via live cd if you dont already have a spare partition.

Next, go for it and install win onto that partition. Be VERY careful to ensure you have the right partition. You wouldnt want to install over ubuntu!

Then follow this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
To get GRUB back in action so you can boot ubuntu again.

---

### Post by philcamlin on 2009-06-08
i know you can go from xp and dual ubuntu but not from ubuntu to xp i wanna do that :D

windows 7 looks tempting buyt i like my virus free machine :popcorn:

---

### Post by benerivo on 2009-06-08
For any boot up / grub problems, i would use super grub disk to restore grub to the hard drive's MBR.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I've used it myself, and it restored my grub in less than a minute.

---

### Post by keplerspeed on 2009-06-08
Yes thats right YOU CAN have ubuntu installed then install win, and still dual boot. See the link in my post above, or alternatively use supergrub, as benerivo has mentioned. Supergrub may be easier too!

---

