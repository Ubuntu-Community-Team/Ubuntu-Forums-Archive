---
title: "Dell 1420N Upgrade with Modem"
date: 2008-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kdorman on 2008-10-06
I am contemplating upgrading my Dell 1420N that came installed with gutsy to hardy using the alternate CD.

I have read the instructions ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work)) for getting the modem to work in hardy, but step 2 requires updating /etc/sources.list and then contacting the internet to upgrade the linux-ubuntu-modules package.

Unfortunately, my modem is my only internet connection, so I cannot get the update before the modem is working!  Chicken, meet egg.  Egg, meet chicken.

Is it impossible to get a working, modem-connected system after cdrom upgrade?

Thanks,
Karin

---

### Post by Orion2000za on 2008-10-20
> **kdorman said:**
> I am contemplating upgrading my Dell 1420N that came installed with gutsy to hardy using the alternate CD.

I have read the instructions ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work)) for getting the modem to work in hardy, but step 2 requires updating /etc/sources.list and then contacting the internet to upgrade the linux-ubuntu-modules package.

Unfortunately, my modem is my only internet connection, so I cannot get the update before the modem is working!  Chicken, meet egg.  Egg, meet chicken.

Is it impossible to get a working, modem-connected system after cdrom upgrade?

Thanks,
Karin
You could go to [www.linuxant.com](www.linuxant.com) and download their hsf-modem driver. Likely it will hose your sound but once you have followed the wiki steps you can then remove it and install the Dell version.
Note that the free linuxant driver is limited to 16k speed

---

