---
title: "Just broke X [Stupidity alert]"
date: 2009-07-16
forum: Desktop Environments
---

### Post by dangerjunkie2002 on 2009-07-16
Hi,

I just did something I would have advised anyone else not to do (ran a script to find out what it did whilst I was root.) :oops: Yes, I know I'm a complete idiot but I was in a hurry and it seemed like a good idea at the time.

I was playing with xrdp and ran /etc/xrdp/startwm.sh (which just calls /etc/X11/Xsession) as root. Now when I restart the machine the GUI fails to start with the error:

(EE) intel(0): no valid modes
(EE) Screens found but none have a usable configuration

I've tried the options of taking the default config or reconfiguring and neither help. I even tried removing xorg.conf altogether. If I accept a startup in "low graphics mode" it says that there appears to already be an X session on display :0 and asks if I want to choose a new number. Saying "no" dumps me back at the same question. Saying "yes" gets me a usable desktop on session 1.

I tried a *dpkg-reconfigure -phigh xserver-xorg* today and that didn't produce any improvement either.

This is probably something really simple but I can't work it out.What do I need to do to restore sanity please?

Thanks,
Paul.

---

### Post by Student Driver on 2009-07-16
Can you post your xorg.conf file?  I used to work with this file a lot, but having been out of Linux for a while and looking at it now, I see that there must be another area to hold metadata.  Mine reads as follows:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by iponeverything on 2009-07-16
> **Student Driver said:**
> Can you post your xorg.conf file?  I used to work with this file a lot, but having been out of Linux for a while and looking at it now, I see that there must be another area to hold metadata.  Mine reads as follows:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I too remember having to create my own xconfig, the lastest xorg is much smarter.. There is no meta-data file, it figures it out on the fly.

---

