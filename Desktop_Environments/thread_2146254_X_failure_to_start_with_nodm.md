---
title: "X failure to start with nodm"
date: 2013-05-17
forum: Desktop Environments
---

### Post by sempernoctis on 2013-05-17
I am trying to set up a kiosk-type system using nodm, but half the time I boot the system, X fails to load.  The logs below suggest this has something to do with modesetting or the Intel DRM drivers.


When X fails, the end of /var/log/Xorg.0.log looks like this:
[     7.973] (II) VESA: driver for VESA chipsets: vesa
[     7.973] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     7.973] (II) FBDEV: driver for framebuffer: fbdev
[     7.973] (++) using VT number 8


[     8.390] (II) intel(0): using device path '/dev/dri/card0'
[     8.391] (WW) Falling back to old probe method for vesa
[     8.391] (WW) Falling back to old probe method for modesetting
[     8.391] (WW) Falling back to old probe method for fbdev
[     8.391] (II) Loading sub module "fbdevhw"
[     8.391] (II) LoadModule: "fbdevhw"
[     8.391] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     8.391] (II) Module fbdevhw: vendor="X.Org Foundation"
[     8.391]     compiled for 1.13.0, module version = 0.0.2
[     8.391]     ABI class: X.Org Video Driver, version 13.0
[     8.456] (EE) intel(0): [drm] Failed to open DRM device for pci:0000:00:02.0: No such file or directory
[     8.456] (EE) intel(0): Failed to become DRM master.
[     8.456] (II) UnloadModule: "intel"
[     8.456] (EE) Screen(s) found, but none have a usable configuration.
[     8.456] 
Fatal server error:
[     8.456] no screens found
[     8.456] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[     8.456] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     8.456] (EE) 
[     8.459] Server terminated with error (1). Closing log file.


When X starts successfully, the corresponding section of /var/log/Xorg.0.log looks like this:
[     8.321] (II) VESA: driver for VESA chipsets: vesa
[     8.321] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     8.321] (II) FBDEV: driver for framebuffer: fbdev
[     8.321] (++) using VT number 8


[     8.425] vesa: Ignoring device with a bound kernel driver
[     8.425] (WW) Falling back to old probe method for vesa
[     8.425] (**) modeset(1): claimed PCI slot 0@0:2:0
[     8.425] (II) modeset(1): using default device
[     8.425] (WW) Falling back to old probe method for fbdev
[     8.425] (II) Loading sub module "fbdevhw"
[     8.425] (II) LoadModule: "fbdevhw"
[     8.425] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     8.425] (II) Module fbdevhw: vendor="X.Org Foundation"
[     8.425]     compiled for 1.13.0, module version = 0.0.2
[     8.425]     ABI class: X.Org Video Driver, version 13.0
[     8.425] (EE) Screen 0 deleted because of no matching config section.
[     8.425] (II) UnloadModule: "vesa"
[     8.425] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32


I have not found any errors or other useful information in any other log files.  Does anybody know how I can get X to start reliably?

---

