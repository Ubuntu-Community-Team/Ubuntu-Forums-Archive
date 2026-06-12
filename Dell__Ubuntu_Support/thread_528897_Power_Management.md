---
title: "Power Management"
date: 2007-08-18
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-18
Hi,
Under power management-->Put display to sleep when inactive:

It doesn't turn off my monitor.  It will go into screensaver mode, but does not turn off monitor no matter what "minutes" I set it to.  Per my earlier posting, this is a new Dell 410N XPS Ubuntu desktop ed., nVidia GeForce 7300 video card.  Thanks.  -aw

---

### Post by Paul S on 2007-08-25
I don't have your hardware, but have some thoughts:

1. Are you sure your monitor has the power off feature.  Not all monitors do.  I'm using a 19" LCD that just goes to a black screen and the power led changes from green to yellow.  But, it does not have the power off feature.

2.  If you really have power off capability, make sure your /etc/X11/xorg.conf file has 

```
Option "DPMS"
```

in the monitor section.

Also, check /etc/default/acpi-support, and try changing the dpms support to see if it helps.  Try this first:

```
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

```

If that fails, try it this way:

```
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false
```

It may be necessary to reboot every time you change the acpi-support file to get the changes recognized.  I'm not sure.

HTH

---

### Post by arvadawest on 2007-08-25
Hi, 
Thank you.  Actually, since I posted this, I had to reinstall the OS and it located the proper drivers for my video card and it now turns off ok.  What was strange was after that, it would not reboot.  I had to power down completely and power up to run the system.  Someone told me to put a "reboot=b" somewhere in a file.  Thanks for your response.  All is well with this.

---

