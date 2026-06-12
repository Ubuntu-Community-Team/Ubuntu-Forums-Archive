---
title: "mounting ubuntu filesystem so i can access ubuntu files while using windows"
date: 2008-10-06
forum: Desktop Environments
---

### Post by kungfu_panda on 2008-10-06
Hi Guys,

i want to know how to mount a my ubuntu file system so i can access files while am using my windows xp, my laptop contains both (ubuntu+windows xp) and am able to access my windows from ubuntu but i don't know to mount the opposite from windows to ubuntu, can anyone advise?

---

### Post by ronnielsen1 on 2008-10-06
[http://www.fs-driver.org/](http://www.fs-driver.org/)


Above link works like a charm

---

### Post by kungfu_panda on 2008-10-13
thanks, i followed the instruction from the link but from the interface i had i saw only windows partition, nothing linux partition like ext2, my linux is installed inside windows, the option where you install ubuntu while your windows is running,is that the reason?

---

### Post by brianfreytag on 2008-10-13
So you installed Ubuntu through Wubi?

Wubi does not create a partition.  In Lehman's terms, it creates it's own little hard drive on the windows file system and installs it to that.

Think of it as something like a virtual machine that you can boot your computer from... These are not normal partition.

[http://blogs.msdn.com/virtual_pc_guy/archive/2007/06/21/mounting-linux-virtual-hard-disks-with-vhdmount.aspx](http://blogs.msdn.com/virtual_pc_guy/archive/2007/06/21/mounting-linux-virtual-hard-disks-with-vhdmount.aspx)

This is the only resource I could find to do what you want to do.  I don't know if it'll work with an wubi install.

If you plan on doing a lot of modifying of your Ubuntu file system, I would suggest dual booting.  There are tons of resources to teach you how to do that.

---

