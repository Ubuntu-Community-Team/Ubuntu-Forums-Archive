---
title: "Intel Graphics Driver Installation Help"
date: 2007-05-14
forum: Desktop Environments
---

### Post by docta13 on 2007-05-14
Hello,

I just installed 6.06 and everything is running smoothly except for my screen resolution is very low.  I traced back to the hardware I'm running and my graphics controller is an Intel 82845G.

I downloaded the appropriate driver and tried installing from the terminal but all I get is this:

> Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


Keep in mind I'm relatively new to Linux.  Please help on what I can do to install this driver and improve my screen resolution.  Thank you very much!

---

### Post by Kobalt on 2007-05-14
All you are required to do in order to install the drivers for your graphic card is ```

sudo apt-get install xserver-xorg-video-intel
```
Did you try this ? Is the error you get comming from this command line ?

---

