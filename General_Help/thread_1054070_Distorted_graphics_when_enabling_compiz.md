---
title: "Distorted graphics when enabling compiz"
date: 2009-01-29
forum: General Help
---

### Post by casanostra on 2009-01-29
When I enable compiz graphics are distorted (see screenshot) whenever something changes (the mouse hovering over an icon, a drop down menu coming down, etc), effectively making the system unusable until switching back to metacity.

When running compiz-check, I get the following output:

```

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility X700 (PCIE)
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 1002:5653 detected.

```

Output from $compiz --replace:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

I hope I'm not double-posting - I honestly haven't been able to find anything on this elsewhere.

---

### Post by casanostra on 2009-01-29
..and my xorg.conf.

---

### Post by casanostra on 2009-01-30
It seems that I should take the warning seriously, doesn't it. I just noticed the emptiness at the end of the line
```
Detected PCI ID for VGA: 
```

Also, refresh rate was set to 50Hz in gconf, which I changed to 60. No improvement, though.

Maybe I'm just out of luck here. Anyone?

---

### Post by casanostra on 2009-02-02
I was using the proprietary driver, which didn't work. I managed to solve the problem by switching to the open source radeon driver instead, using this guide: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).

Problem solved.

---

