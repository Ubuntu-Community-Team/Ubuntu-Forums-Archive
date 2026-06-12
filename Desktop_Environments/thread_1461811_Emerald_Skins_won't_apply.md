---
title: "Emerald Skins won't apply"
date: 2010-04-24
forum: Desktop Environments
---

### Post by Zonda333 on 2010-04-24
So I installed emerald and compiz fusion today on lucid in a VM. However, when I select a theme in emerald, the program simply closes. After this, I have tried doing emerald --replace, but nothing happens.
I then tried doing compiz --replace, but got this error:

```
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```

Any ideas on what to do?

EDIT:
After running compiz-check, I determined the problem:

```
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         VMware SVGA II Adapter
 Driver in use:         vmware
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

Anyone know how to fix this? All results on google said to edit xorg.conf, but I don't have one.

---

### Post by lidex on 2010-04-24
Don't think it's possible to get 3D support in a VM. Maybe some experimental stuff out there, but no idea where to find it. Have you looked at the vmware site?

---

### Post by Zonda333 on 2010-04-24
> **lidex said:**
> Don't think it's possible to get 3D support in a VM. Maybe some experimental stuff out there, but no idea where to find it. Have you looked at the vmware site?

I selected the enable 3D in the settings, but this still won't work.

[http://i43.tinypic.com/2yl1yms.png](http://i43.tinypic.com/2yl1yms.png)

---

### Post by Zonda333 on 2010-04-25
bump

---

### Post by Frogs Hair on 2010-04-25
A Software Rasterizer is a rendering engine and it's in conflict with Emerald . Thats all I could find out. I installed Emerald two days ago but I use a Nvidia graphics card and the driver comes with X Server Settings panel.

---

