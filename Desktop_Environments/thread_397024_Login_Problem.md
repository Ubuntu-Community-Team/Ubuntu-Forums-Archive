---
title: "Login Problem"
date: 2007-03-30
forum: Desktop Environments
---

### Post by reb68 on 2007-03-30
All was fine in my Fiesty until 3 days ago when it would not let me finish the login. after the kubuntu logo it goes to a black screen and then the text:
--------------
[ 157.7524 ] usbdev 2.2_Ep88: Suspend 0-->2, Parent 2-1:1,2 Already 2
Bug soft Lickup detected on cpu#2
------------
This may not be a ubuntu problem but I do not know where else to turn. I can go to my WindowXP drive (where I am now) and all works well.
Please help.
Dick Barmann

---

### Post by 1/0 on 2007-03-30
I think that should be lockup and not lickup *LoL*

Anyway, have you got a single processor? If so, is SMP enbled in the kernel. If so, try disabling it and recompile.

---

### Post by reb68 on 2007-03-30
Yes I have a single processor. Can you walk we through disabling as you suggest and the recompile/reinstall?.

---

### Post by 1/0 on 2007-03-30
I just switched from Gentoo and compiling the kernel was way easier in Gentoo from the looks of it. You can start by looking in your .config file which is in /boot/ under the name config-2.6.17-11-generic (chek with /boot/grub/menu.lst). Look for CONFIG_SMP=y

If that is the case I suspect that this could cause the problem (I'm not sure). To compile the kernel in ubuntu, chek this site, It explains it better than I can. [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) 

This is another one: [http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

---

