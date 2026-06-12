---
title: "Problem installing Ubuntu 7.10 on my Pentium 4 3.0 Ghz (Graphics corrupts)"
date: 2008-04-09
forum: Desktop Environments
---

### Post by pj.vancoller on 2008-04-09
Hi.

I am having a problem installing Ubuntu on my P4 3Ghz with 1024MB ram and a Geforce 4MX 440.

When I boot from the CD, I can see the Ubuntu progress bar for a few seconds, and then my graphics corrupts, and the install hangs.

I was able to load the Live version once, but the other times it fails.

I ran the cd check, and it was successful, as well as the memory check. Windows is currently running 
fine on the same system.

I hope someone can help me.

Thanks

Paul.

---

### Post by tamoneya on 2008-04-09
Graphics corrupting has very little to do with the CPU model and is primarily a function of the graphics card.  What happens why you use the safe graphics mode option from the CD?  Have you attempted to use the alternate CD?

---

### Post by warp99 on 2008-04-10
You may have to set some boot options before the install:

[https://help.ubuntu.com/community/BootOptions#head-fd6993472b20e64d715ae8f44a496dc2cf9f7cbd](https://help.ubuntu.com/community/BootOptions#head-fd6993472b20e64d715ae8f44a496dc2cf9f7cbd)

You should try 'noacpi' and 'irqpoll' and possibly 'vga=xxx' to set the vesa resolution prior to installation.

---

