---
title: "[SOLVED] XP install after Ubuntu."
date: 2008-05-12
forum: Desktop Environments
---

### Post by Barriehie on 2008-05-12
Okay, so I do need XP to run a few programs that just will not work any other way.  At this point I'm Ubuntu only on here so I have two options.  Resize Ubuntu and install XP and then repair GRUB or back up my Ubuntu install, install XP, install Ubuntu, and finally restore Ubuntu.  Which option is the most foolproof in regards to lessening the chance for operator error?  I really like Ubuntu and have spent a couple of months customizing it, would hate to start over!

Thank You for any replies.
Barrie

dual boot; grub; xp

---

### Post by zenwalker on 2008-05-12
Just install Xp on a seperate partition and then restore Ubuntu's grub on MBR. U need not to install Ubuntu once again. Repartition or split Ubuntu drive using Gparted .

---

### Post by Barriehie on 2008-05-12
So I can boot from the gparted live CD and shrink my Ubuntu partition without losing anything and then the rest is reading, right? :)

Barrie

---

### Post by corevette on 2008-05-12
you could always try installing [virtualbox]("http://www.virtualbox.org/") to run windows xp inside your ubuntu partition

---

### Post by Barriehie on 2008-05-12
> **corevette said:**
> you could always try installing [virtualbox]("http://www.virtualbox.org/") to run windows xp inside your ubuntu partition

I think I'll try that, after I backup to a seperate device!

Barrie

---

### Post by Alien.col on 2008-05-12
Here is a good guide you can use for that: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Barriehie on 2008-05-12
> **Alien.col said:**
> Here is a good guide you can use for that: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Thank you, looks like I better try this on the weekend!
Barrie

---

### Post by meganox on 2008-05-12
I highly recommend making a supergrub / puppy linux / gparted / clonezilla live cd as detailed here: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

The whole site is very helpful although some of the information may be out of date, but you get all the tools you need to troubleshoot and recover dual boot systems on one live cd, with the bonus of a full working *fast* OS for when you just need to get stuff done.

---

### Post by Barriehie on 2008-05-12
> **meganox said:**
> I highly recommend making a supergrub / puppy linux / gparted / clonezilla live cd as detailed here: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

The whole site is very helpful although some of the information may be out of date, but you get all the tools you need to troubleshoot and recover dual boot systems on one live cd, with the bonus of a full working *fast* OS for when you just need to get stuff done.


This looks very good!  I will go this route.  What I was imagining to take hours looks like it won't be any issue at all. 

Thank You for the prompt replies and awsome link Meganox, thank you again.
Barrie

---

