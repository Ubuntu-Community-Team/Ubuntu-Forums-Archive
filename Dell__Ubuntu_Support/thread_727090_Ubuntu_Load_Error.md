---
title: "Ubuntu Load Error"
date: 2008-03-17
forum: Dell  Ubuntu Support
---

### Post by jhaber on 2008-03-17
Hi, I'm running Ubuntu 7.10 on a Dell Inspiron 8600, with a partioned drive for Windows.
The computer has been running well for a few months; however, now when I try to turn it on, I recieve:

Grub loading stage1.5
Grub loading please wait...
Error 2

I was able to use the live CD to recover my Windows files, but am unable to mount the Ubuntu portion.  I need to at least be able to recover the files from Ubuntu.  I can't reinstall until I am able to do so.  Any ideas?  Thank you,
Jordan

---

### Post by Tomatz on 2008-03-17
T

---

### Post by Tomatz on 2008-03-17
Try this its a gparted live cd:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Download and burn the .iso to disc then you will be able to fix your disc errors from a nice gui :)

Ps Dont worry im sure its just minor disc errors

---

### Post by jhaber on 2008-03-17
Thanks for the fast reply, I'll look into it when I get home.

---

### Post by jhaber on 2008-03-17
Ok, so I ran the CD and checked/repaired the partition.
I'm now running the live CD and am able to access my Ubuntu partition.
The problem is, I still can't fix the Grub loader.  I tried running the grub commands to reinstall, but it can't find /boot/grub/stage1.
I'm thinking that the /boot partition is missing, as it can't find /boot either.  Any suggestions?  I really don't want to have to reinstall...
Thank you,
Jordan

---

### Post by Tomatz on 2008-03-18
you are right it sounds like the boot sector/grub is damaged beyond repair.  But you can download a super grub boot cd to reinstall grub. This boot cd will also enable you to boot xp and ubuntu straight from the cd before writing grub to your disc. So that you can test all is good beforehand :)

Get it here:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

