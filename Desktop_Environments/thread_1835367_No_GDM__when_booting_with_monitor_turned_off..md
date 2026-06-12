---
title: "No GDM  when booting with monitor turned off."
date: 2011-08-29
forum: Desktop Environments
---

### Post by ninocass on 2011-08-29
Hi All

I have my Acer Revo connected to my  bose via HDMI however if the bose is turned off and I reboot the server remotely when it comes back up i have no GDM session.

The Nvidia logs report:

```
[    44.888] (--) NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0
[    44.889] (--) NVIDIA(0):     none
[    44.890] (EE) NVIDIA(0): No display devices found for this X screen.
[    45.190] (II) UnloadModule: "nvidia"
[    45.190] (II) Unloading nvidia
[    45.190] (II) UnloadModule: "wfb"
[    45.191] (II) Unloading wfb
[    45.191] (II) UnloadModule: "fb"
[    45.191] (II) Unloading fb
[    45.191] (EE) Screen(s) found, but none have a usable configuration.
[    45.191] 
Fatal server error:
[    45.191] no screens found
```

Is there a way for force nvidia to treat the monitor as connected?

many thanks

---

