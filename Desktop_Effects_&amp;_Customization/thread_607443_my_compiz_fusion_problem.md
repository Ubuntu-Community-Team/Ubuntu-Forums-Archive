---
title: "my compiz fusion problem"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by pinoyskull on 2007-11-08
vidcard: ATI RADEON 9600 Series 256MB
monitor: Dual Samsung SyncMaster 740n

I successfully installed and enabled the new ATI Binary Driver 8.42.3 on my system and enabled BigDesktop

```

#fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

```

but when I try to run compiz, it returned an error
```

$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4150 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

```

did i miss something?

---

### Post by santiagoward2000 on 2007-11-08
Well, it seems you need to install XGL. Just go to Synaptic and search for the "xserver-xgl" package. I think that should do it.

---

### Post by pinoyskull on 2007-11-08
The reason I did not install XGL cuz I want to use AIGLX which according to the guides I read around here, that you have to remove XGL

XGL wont work anyway on my Dualhead config

---

