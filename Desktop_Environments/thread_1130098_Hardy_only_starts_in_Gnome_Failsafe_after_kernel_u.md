---
title: "Hardy only starts in Gnome Failsafe after kernel update"
date: 2009-04-19
forum: Desktop Environments
---

### Post by taecha on 2009-04-19
Hardy will not start after login. The desktop stays blank, panels will usually not load at all or if, panel applets will cause errors. All seems to have started after the latest kernel update. I can start Hardy only in Gnome Failsafe mode. Calling compiz from terminal returns

```
aborting and using fallback: /usr/bin/metacity 
```

without any additional information. Running compiz-check gives no clues, either:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         i810
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

Any ideas what's wrong and how to solve the problem?

---

### Post by PacSci on 2009-04-19
Go into GRUB and select an older kernel version when booting, then check if that fixes anything. If it doesn't, the kernel is not your problem.

---

### Post by taecha on 2009-04-20
Thanks for the tip, PacSci. Actually, it does not change anything. If it isn't the kernel, what could it be?

---

