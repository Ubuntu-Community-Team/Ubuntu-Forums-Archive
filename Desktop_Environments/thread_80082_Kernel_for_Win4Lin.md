---
title: "Kernel for Win4Lin?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by dgermann on 2005-10-21
Hi--

Have just successfully installed Win4Lin9x on my Ubuntu 5.10 machine.

It uses a kernel a couple versions older than what is in Badger.

Has anyone compiled a kernel that matches the latest in Breezy that you are willing to share?

Thanks!

---

### Post by GrumpyBob on 2005-10-21
I'd be interested in this as well...

Robert

---

### Post by sandyeggoboy on 2005-10-22
Yeah i just installed it too. now i cant get my system to boot up at all. 

Is there a way to "re-do" to ubuntu boot so i can get it to work again?

---

### Post by dgermann on 2005-10-22
sandyeggoboy--

If you have grub, when you boot up hit esc immediately after (it only gives you 3 seconds to do that by default--you can change that in the grub script) the computer manufacturer's bootup screen; that will bring up a list of your installed kernels and you can choose to bootup using a kernel other than win4lin.

I did not have that particular problem, but did have to reboot in the middle of the install process, twice I think, which was part of what it requires. So you might want to rerun the win4lin-install app to see if it still has some steps to complete.

---

### Post by isitututu on 2005-12-04
Would also be interested in a win4lin kernel for 5.10.

Carlos

---

### Post by GrumpyBob on 2005-12-04
[QUOTE=isitututu]Would also be interested in a win4lin kernel for 5.10.

Carlos[/QUOTE]

qemu works very well for me on my Breezy laptop.  It can be installed via synaptic, and there's an excellent how-to on the forum somewhere...
[http://www.ubuntuforums.org/showthread.php?p=200357#post200357](http://www.ubuntuforums.org/showthread.php?p=200357#post200357)
I'm using it for Win98SE.  No kernel patching needed. No USB support, but Win4Lin9X doesn't support USB either.  Apparently the CVS version of qemu does support USB, or so I've heard.

Robert

---

