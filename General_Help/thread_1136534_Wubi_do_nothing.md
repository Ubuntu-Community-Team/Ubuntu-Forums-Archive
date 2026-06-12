---
title: "Wubi do nothing"
date: 2009-04-25
forum: General Help
---

### Post by melancoholic on 2009-04-25
Hi all.

I'm trying to install **wubi **to use **Ubuntu 9.10**.  I have downloaded **wubi**, but when I double click on the exe, just do nothing.  I have even created a folder **c:\ubuntu** where I have put  the **ubuntu-9.04-desktop-i386.iso** and **wubi.exe** but just do nothing :confused:

I am using **Windows Vista Ultimate**, and I would like to try Ubuntu with wubi.  What can be wrong?

Thanks :)

---

### Post by 3rdalbum on 2009-04-25
Use the "Burn ISO image" or "Burn image to disc" setting of your CD burning software to burn the ISO file to a blank CD or DVD.

When it has finished, put the disc back into your PC and you will get an autorun menu appear, which will give you the option to install Ubuntu from within Windows.

I'd recommend doing a real dual-boot installation by booting up your computer from the CD and letting the Ubuntu installer partition your hard disk; that way if anything goes wrong with Vista down the track, you'll still be able to use Ubuntu.

---

### Post by xyzt on 2009-04-25
> **melancoholic said:**
> Hi all.

I'm trying to install **wubi **to use **Ubuntu 9.10**.  I have downloaded **wubi**, but when I double click on the exe, just do nothing.


Interesting. (That means "huh?") :)

Are you trying to run wubi on Vista (that's how it should be done) or on Ubuntu? It should be run on Windows, of course.

You don't need a CD to install via Wubi. The installation is done via a internet connection. You must have one active at the time of running Wubi.

If you install from CD, GRUB will take hold of your boot process, and it will be very hard to remove GRUB from a Vista dual boot. Wubi is meant to solve that problem by using the Windows boot management, instead of GRUB.

Also check your permissons on Vista when you run Wubi. You must run as administrator.

---

### Post by melancoholic on 2009-04-25
Thanks for the answer, but I understand that it will create a real new partition in my hard disk, and what I like from wubi is that no partition is created, wubi creates a "virtual partition" in the Windows partition.  Your answer is not like this, is it?

:)

---

### Post by melancoholic on 2009-04-25
That's what I'm trying to do, I'm executing wubi downloaded from [http://wubi-installer.org/](http://wubi-installer.org/) to avoid creating a new partition and GRUB.  But just do nothing.  I'm connected to Internet, I try to execute it as administrator, but nothing happens.

---

### Post by lisati on 2009-04-25
> **melancoholic said:**
> Thanks for the answer, but I understand that it will create a real new partition in my hard disk, and what I like from wubi is that no partition is created, wubi creates a "virtual partition" in the Windows partition.  Your answer is not like this, is it?

:)

If you burn a CD from the ISO file and then insert the CD while Windows is running you will be given a chance to use Wubi to install Ubuntu without setting up a new partition

---

### Post by kobyk on 2009-04-25
It doesn't matter whether you use the standalone Wubi installer or burn the Ubuntu CD - AutoPlay will still run Wubi.
You may have the same problem with Wubi I have, described in this bug:

[https://bugs.launchpad.net/wubi/+bug/365501](https://bugs.launchpad.net/wubi/+bug/365501)

Hopefully this issue will be resolved soon and then you can try the newer version of Wubi.

---

### Post by lisati on 2009-04-25
> **kobyk said:**
> It doesn't matter whether you use the standalone Wubi installer or burn the Ubuntu CD - AutoPlay will still run Wubi.
You may have the same problem with Wubi I have, described in this bug:

[https://bugs.launchpad.net/wubi/+bug/365501](https://bugs.launchpad.net/wubi/+bug/365501)

Hopefully this issue will be resolved soon and then you can try the newer version of Wubi.

Hope we didn't double report: [https://bugs.launchpad.net/ubuntu/+bug/366701](https://bugs.launchpad.net/ubuntu/+bug/366701)

---

