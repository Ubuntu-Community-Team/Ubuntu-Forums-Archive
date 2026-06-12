---
title: "Dual Monitor Mouse Pointer Issue"
date: 2007-03-22
forum: Desktop Environments
---

### Post by cprofitt on 2007-03-22
I have just installed the ATI proprietary driver and used aticonfig to setup dual monitors. Everything worked except I get a large square block instead of a mouse pointer on the second display.

I have searched the forums but been unable to find any information that appears to apply to my situation. Does anyone have any information which might assist me?

Thanks.

---

### Post by whistl on 2007-05-01
I got the exact same thing after upgrading from Edgy to Feisty, then I downloaded and installed the latest ATI driver from [www.ati.com](www.ati.com), and the problem went away.

BTW, I had to run:

X_VERSION=x710 ./ati-driver-installer-8.36.5-x86.x86_64.run

because the ATI driver install script doesn't recognize xorg 7.2 yet.  But it works just fine.

---

