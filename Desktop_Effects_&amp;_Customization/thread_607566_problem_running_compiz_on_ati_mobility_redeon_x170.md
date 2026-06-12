---
title: "problem running compiz on ati mobility redeon x1700"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by blwizard on 2007-11-09
Hi there.

I've followed some guide somewhere to set up graphic driver. I'm using fglrx and it's loaded successfully according to the Restricted  Drivers Manager, and normal display is perfectly fine. This is what I get by running fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6473 (8.37.6)

```

But I just can't start compiz. When I run:
```

compiz --replace

```

I get the following, could someone help me figure out what went wrong? Thanks heaps!
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71d5 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Forlong on 2007-11-09
What Ubuntu version do you use?
You need to install Xgl.

---

### Post by blwizard on 2007-11-09
Thanks buddy! Im using ubuntu 7.10. I just didn't know the relationship between compiz and xgl. Now i have the cube desktop, haha

---

