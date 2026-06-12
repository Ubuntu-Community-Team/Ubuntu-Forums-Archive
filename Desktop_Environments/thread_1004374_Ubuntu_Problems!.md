---
title: "Ubuntu Problems!"
date: 2008-12-07
forum: Desktop Environments
---

### Post by deagle on 2008-12-07
Hi, ive decided to come back to ubuntu after a year absents. I love it..

But! im having problems with my graphics drivers. I had the same card working fine last year.

ATI Technologies Inc RV530 [Radeon X1600]

so.. after a clean install. everything it fine. but the visual effects are all off. so i turn them on, and it downloads and installs a driver. but still doesnt work after a reboot. and the driver its installed has messed everything up. video playback is very skippy and jaggid, and flash videos within the browser is also.

ive installed the latest driver from the ATI website, its the same, with no compiz. and ive installed a driver using envy. same. and the driver in Synaptic. ive activated/deactivated the drivers... same.

So now im at a loss, ive read through the forum trying different things. but still the same issue. 

Can anyone help me out?

Thanks

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV530 [Radeon X1600]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect fglrx driver version in use. 

```

---

