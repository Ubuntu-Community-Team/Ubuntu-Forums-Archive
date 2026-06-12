---
title: "Dell Wireless 1505 - only 32-bit compatible?"
date: 2009-08-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by recluce on 2009-08-27
Yesterday I installed yet another Dell Latitude notebook under Ubuntu. This one is a Dell D630 with Core2Duo CPU, Nvidia Graphics and a Dell Wireless 1505 (identified as Broadcom and using "Broadcom STA" wireless driver under Ubuntu).

As the system is 64bit capable, I installed Jaunty AMD_64 version from the live CD. With this version installed, try what I might, wireless was not working and all tricks on this website didn't work. The system partially "saw" the wireless, but never to a point were it could actually connect.

After I was ready to give up, I installed Dell's 32-bit Ubuntu Jaunty DVD and the wireless works right away. Going back to a 32 bit system is not a big deal in this case, but the hassle to get Ubuntu working on this machine was just anoying.

Has anybody else found the Broadcom STA driver to be incompatible with 64 bit Ubuntu versions?

P.S.: if you buy a Dell notebook, try to get an Intel wireless module, they seem to cause no problems whatsoever.

---

### Post by recluce on 2009-09-04
/bump

Nobody with comments on the Broadcom STA driver under _X64?

---

### Post by jml on 2009-09-04
I don't have any direct experience with that driver and 64 bit Ubuntu, but in general Broadcom wireless drivers are proprietary and Broacom is not willing to make either open source drivers or the internal specifications of their cards available to developers.  I can think of two possible reasons for your results.  First, Linux developers may not have a solid driver for 64 bit linux yet.  Second, it's possible that Dell may have been able to get proprietary drivers from Broadcom and the Dell version of Ubuntu is a custom build.

Joe

---

