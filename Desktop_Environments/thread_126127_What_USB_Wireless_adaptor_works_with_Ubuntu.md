---
title: "What USB Wireless adaptor works with Ubuntu"
date: 2006-02-05
forum: Desktop Environments
---

### Post by ade234uk on 2006-02-05
I already have Ubuntu running on my Main machine, I now want to run it on my laptop. I want to go wireless with it.

In your own experience what USB wireless adaptor do you use and works with Ubuntu. 

Hopefully its just a case of then installing the NDIS Wrapper and getting .inf file from the Windows driver and then I can ditch Windows on the Laptop.

---

### Post by atoponce on 2006-02-05
Wireless is scratchy at best in Ubuntu.  I hear the DLink and Proxim cards work best.  Recently, a specific Broadcom chipset driver was just reversed engineered, so a Linksys card might work.

However, I am really not of much help, as I have yet to get wireless working functionally under any Linux distro.

Good luck, though!

---

### Post by az on 2006-02-05
Actually, more of them work, than not.

If it does not work out-of-the-box (with native linux drivers) if usually will work with ndiswrapper, which uses the windows driver -  it wraps around it to use it).  There are only a small number of cards that do not work with ndiswrapper.

---

