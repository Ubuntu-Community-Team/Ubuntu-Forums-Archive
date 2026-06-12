---
title: "OpenChrome 3D accel is on, but can´t enable Desktop Effects"
date: 2009-02-07
forum: General Help
---

### Post by radzfoto on 2009-02-07
I just installed Ubuntu 8.10 fresh on an hp pavilion a610n with a Via graphics chipset on the motherboard. Ubuntu correctly installed the OpenChrome drivers and 3d accel is on, but I cannot enable Desktop Effects.

Here is what Ubuntu says about the status of the installed 3d drivers:
```

raul@ubuntu1:/etc/X11$ glxinfo | grep -i direct
direct rendering: Yes
raul@ubuntu1:/etc/X11$ cat /var/log/Xorg.0.log | grep -i accel
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
raul@ubuntu1:/etc/X11$ cat /var/log/Xorg.0.log | grep "dri"
	X.Org XInput driver : 2.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched openchrome for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(!!) VIA Technologies does not support this driver in any way.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) [drm] loaded kernel module for "via" driver.
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): [dri] Using AGP.
(II) CHROME(0): [dri] Frame buffer initialized.
(II) CHROME(0): [dri] Kernel data initialized.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
	ABI class: X.Org XInput driver, version 2.1
raul@ubuntu1:/etc/X11$ 

```

From this result it looks like all should be well, and, yet, Desktop Effects just won´t work.

Any suggestions or help would be greatly appreciated.

Thanks,
Radzfoto

---

### Post by gettinoriginal on 2009-02-07
Did you check System, Preferences, Appearance, Visual Effects to make sure they are set to Extra or Custom?

---

