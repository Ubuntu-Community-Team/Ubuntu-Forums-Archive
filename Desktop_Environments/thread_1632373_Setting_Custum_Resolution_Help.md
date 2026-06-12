---
title: "Setting Custum Resolution Help"
date: 2010-11-27
forum: Desktop Environments
---

### Post by vze4p6c2 on 2010-11-27
Hi there.  I tried to research for solution but could not find any, or at least it didn't help.

First Specs:

Ubuntu 10.04 (Latest as of Nov. 20, 2010); ATI driver enabled (default ubuntu driver);

ATI Radeon HD 3870 - two ports - one connected to monitor (primary) other connected to projector (not used with linux at all, only on WinXP);

/etc/X11/xorg.conf:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection
```

Problem:

I need custom resolution for my monitor which is: 1366 by 768;
System>Preferences>Monitor does not have correct selection for my monitor;

I'm sorry if I missed something important; If so, please ask!  Thanks much!

---

