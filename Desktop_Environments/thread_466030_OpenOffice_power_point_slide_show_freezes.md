---
title: "OpenOffice: power point slide show freezes"
date: 2007-06-06
forum: Desktop Environments
---

### Post by captaintrav on 2007-06-06
I'm running a pretty fresh 7.04 install, and the latest ATI fglrx drivers, (maybe this is the culprit)

Anyhow, OO opens up any powerpoint file people have given me just fine, but when I try to run the slide show, the whole desktop just freezes.  I'm assuming this is probably because the OO process has "run away" so to speak.  Killing the X server works, but switching to a text console and killing the soffice process brings things back to life again.  I have confirmed this behavior with multiple files.  And I'm not running compiz or beryl, either, just basic Gnome. 

Any ideas/fixes?

After I post this, I'm probably going to try a different video driver for kicks,

edit: and I tried switching the video driver to the opensource ATi driver, same results.  Below is the relevant stuff from the Xorg.0.log for each driver in case someone cares about the versions.

```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
```

```
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 6.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
```

---

### Post by ronmarley1 on 2007-06-06
Sorry for the non-answer, but have you tried the OpenOffice.org forums?  They are located at [http://www.oooforum.org/](http://www.oooforum.org/)
Good luck!

---

### Post by captaintrav on 2007-06-11
I posted there, and apparently this is due to BUGS in the Ubuntu OOo packages.  I downloaded the official packages, converted them to debian packages, installed them, and all is well.

---

### Post by Hagar Delest on 2007-06-14
Right, I made a small tutorial about that here : [[Ubuntu] Installing OOo on Debian and Co.]("http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759") I hope it will be helpfull to other users finding this thread.

---

