---
title: "how to install fglrx-installer-experimental-13 graphic driver on ubuntu 14.04 lts ???"
date: 2016-05-05
forum: Gaming &amp; Leisure
---

### Post by beetlejayce on 2016-05-05
Hi!       I m trying to use steam on ubuntu 14.04 and looking to change the graphic driver from xorg to fglrx-installer-experimental-13 (recommanded by steam for AMD/ATI Graphics).   my graphic card: Mobility Radeon HD 5650   I know this driver is for Ubuntu 12.04 Precise, but is it possible to install it on 14.04?    the problem actually is impossible to launch an installed game with steam.

---

### Post by oldrocker99 on 2016-05-05
You **should** be able to install fglrx on 14.04. The fglrx drivers definitely **do not** work on 16.04. Here's how to install them:[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) 

The radeon drivers should work fine with Steam games, though. They've been developed with a lot of help from ATI; ATI "legacies" a lot of their older graphics chips (for all systems, not just Linux) and make the inner workings of their chips available to the radeon team. I used the radeon drivers in 2009-2011 and they improved greatly over that period. I've seen posts on Steam from ATI users who praised the radeon drivers over fglrx.

Good luck!

---

