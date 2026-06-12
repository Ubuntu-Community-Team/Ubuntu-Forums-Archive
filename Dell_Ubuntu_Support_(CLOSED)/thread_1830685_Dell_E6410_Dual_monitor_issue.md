---
title: "Dell E6410 Dual monitor issue"
date: 2011-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Azazel79 on 2011-08-22
Hi forum,

I have a Dell E6410 running Ubuntu 11.04 64bit.

I have been able to run nvidia X server settings, and I can now see in both monitors the ubuntu background.

Also I can move my mouse between the two monitors. What I am not able to do is move apps windows from one to the other!!

I have gone into the nvidia X server settings, using "gksudo /usr/bin/nvidia-settings", and tried to set the twinview, but I get the following error:

*Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1920x1080 +1440+0, DFP-3: nvidia-auto-select @1440x900 +0+0' (Mode 3360x1080, id: 50) on X screen 0*

Can anybody help me out?

Regards

---

### Post by frogotronic on 2011-08-26
> **Azazel79 said:**
> Hi forum,

I have a Dell E6410 running Ubuntu 11.04 64bit.

I have been able to run nvidia X server settings, and I can now see in both monitors the ubuntu background.

Also I can move my mouse between the two monitors. What I am not able to do is move apps windows from one to the other!!

I have gone into the nvidia X server settings, using "gksudo /usr/bin/nvidia-settings", and tried to set the twinview, but I get the following error:

*Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1920x1080 +1440+0, DFP-3: nvidia-auto-select @1440x900 +0+0' (Mode 3360x1080, id: 50) on X screen 0*

Can anybody help me out?

Regards

Did you initialise the nVIDIA settings?

Can you post your xorg.conf file?

Mine's attached, for a DELL e6420 laptop.

- CH

---

