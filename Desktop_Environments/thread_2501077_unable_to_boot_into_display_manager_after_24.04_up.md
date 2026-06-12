---
title: "unable to boot into display manager after 24.04 update"
date: 2024-09-22
forum: Desktop Environments
---

### Post by iceteacake on 2024-09-22
After updating to Ubuntu 24.04.1 (from Ubuntu 22.04), Xorg fails to  start while using NVIDIA drivers. I have tried everything except apart  from reinstalling (intended to be the last resort).

Below are the logs from Xorg.

```

[    28.003] (--) Log file renamed from "/var/lib/gdm3/.local/share/xorg/Xorg.pid-1478.log" to "/var/lib/gdm3/.local/share/xorg/Xorg.0.log"
[    28.003] 
X.Org X Server 1.21.1.11
X Protocol Version 11, Revision 0
[    28.003] Current Operating System: Linux <redacted> 6.8.0-45-generic #45-Ubuntu SMP PREEMPT_DYNAMIC Fri Aug 30 12:02:04 UTC 2024 x86_64
[    28.003] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.8.0-45-generic root=UUID=29471745-9eb1-47cb-a1b2-a0a1f2872dad ro nomodeset quiet
[    28.003] xorg-server 2:21.1.12-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    28.003] Current version of pixman: 0.42.2
[    28.003]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.003] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.003] (==) Log file: "/var/lib/gdm3/.local/share/xorg/Xorg.0.log", Time: Sun Sep 22 15:28:58 2024
[    28.004] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.004] (==) ServerLayout "layout"
[    28.004] (==) No screen section available. Using defaults.
[    28.004] (**) |-->Screen "Default Screen Section" (0)
[    28.004] (**) |   |-->Monitor "<default monitor>"
[    28.004] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.004] (**) Allowing byte-swapped clients
[    28.004] (==) Automatically adding devices
[    28.004] (==) Automatically enabling devices
[    28.004] (==) Automatically adding GPU devices
[    28.004] (==) Automatically binding GPU devices
[    28.004] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    28.004] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.004]     Entry deleted from font path.
[    28.004] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.004]     Entry deleted from font path.
[    28.004] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.004]     Entry deleted from font path.
[    28.004] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.004]     Entry deleted from font path.
[    28.004] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.004]     Entry deleted from font path.
[    28.004] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    28.004] (==) ModulePath set to "/usr/lib/xorg/modules"
[    28.004] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.004] (II) Loader magic: 0x5a6c08e2a020
[    28.004] (II) Module ABI versions:
[    28.004]     X.Org ANSI C Emulation: 0.4
[    28.004]     X.Org Video Driver: 25.2
[    28.004]     X.Org XInput driver : 24.4
[    28.004]     X.Org Server Extension : 10.0
[    28.005] (++) using VT number 1

[    28.007] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c6
[    28.008] (II) xfree86: Adding drm device (/dev/dri/card1)
[    28.008] (II) Platform probe for /sys/devices/pci0000:00/0000:00:06.0/0000:01:00.0/drm/card1
[    28.009] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 14 paused 0
[    28.010] (II) xfree86: Adding drm device (/dev/dri/card0)
[    28.010] (II) Platform probe for /sys/devices/platform/simple-framebuffer.0/drm/card0
[    28.010] (EE) systemd-logind: failed to take device /dev/dri/card0: No such file or directory
[    28.012] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[    28.014] (--) PCI:*(0@0:2:0) 8086:9a49:103c:8850 rev 1, Mem @ 0x56000000/16777216, 0x60000000/268435456, I/O @ 0x00004000/64, BIOS @ 0x????????/131072
[    28.014] (--) PCI: (1@0:0:0) 10de:1f97:103c:8850 rev 161, Mem @ 0x57000000/16777216, 0x40000000/268435456, 0x50000000/33554432, I/O @ 0x00003000/128
[    28.014] (II) LoadModule: "glx"
[    28.015] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.016] (II) Module glx: vendor="X.Org Foundation"
[    28.016]     compiled for 1.21.1.11, module version = 1.0.0
[    28.016]     ABI class: X.Org Server Extension, version 10.0
[    28.016] (II) Applying OutputClass "nvidia" to /dev/dri/card1
[    28.016]     loading driver: nvidia
[    28.504] (==) Matched nvidia as autoconfigured driver 0
[    28.504] (==) Matched nouveau as autoconfigured driver 1
[    28.504] (==) Matched modesetting as autoconfigured driver 2
[    28.504] (==) Matched fbdev as autoconfigured driver 3
[    28.504] (==) Matched vesa as autoconfigured driver 4
[    28.504] (==) Assigned the driver to the xf86ConfigLayout
[    28.504] (II) LoadModule: "nvidia"
[    28.504] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[    28.505] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.505]     compiled for 1.6.99.901, module version = 1.0.0
[    28.505]     Module class: X.Org Video Driver
[    28.505] (II) LoadModule: "nouveau"
[    28.505] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.505] (II) Module nouveau: vendor="X.Org Foundation"
[    28.505]     compiled for 1.21.1.3, module version = 1.0.17
[    28.505]     Module class: X.Org Video Driver
[    28.505]     ABI class: X.Org Video Driver, version 25.2
[    28.505] (II) LoadModule: "modesetting"
[    28.506] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.506] (II) Module modesetting: vendor="X.Org Foundation"
[    28.506]     compiled for 1.21.1.11, module version = 1.21.1
[    28.506]     Module class: X.Org Video Driver
[    28.506]     ABI class: X.Org Video Driver, version 25.2
[    28.506] (II) LoadModule: "fbdev"
[    28.506] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.506] (II) Module fbdev: vendor="X.Org Foundation"
[    28.506]     compiled for 1.21.1.11, module version = 0.5.0
[    28.506]     Module class: X.Org Video Driver
[    28.506]     ABI class: X.Org Video Driver, version 25.2
[    28.506] (II) LoadModule: "vesa"
[    28.506] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.506] (II) Module vesa: vendor="X.Org Foundation"
[    28.506]     compiled for 1.21.1.7, module version = 2.6.0
[    28.506]     Module class: X.Org Video Driver
[    28.506]     ABI class: X.Org Video Driver, version 25.2
[    28.506] (II) NVIDIA dlloader X Driver  555.42.06  Tue Jun  4 00:30:49 UTC 2024
[    28.506] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    28.506] (II) NOUVEAU driver Date:   Sat Jan 23 12:24:42 2021 -0500
[    28.506] (II) NOUVEAU driver for NVIDIA chipset families :
[    28.506]     RIVA TNT            (NV04)
[    28.506]     RIVA TNT2           (NV05)
[    28.507]     GeForce 256         (NV10)
[    28.507]     GeForce 2           (NV11, NV15)
[    28.507]     GeForce 4MX         (NV17, NV18)
[    28.507]     GeForce 3           (NV20)
[    28.507]     GeForce 4Ti         (NV25, NV28)
[    28.507]     GeForce FX          (NV3x)
[    28.507]     GeForce 6           (NV4x)
[    28.507]     GeForce 7           (G7x)
[    28.507]     GeForce 8           (G8x)
[    28.507]     GeForce 9           (G9x)
[    28.507]     GeForce GTX 2xx/3xx (GT2xx)
[    28.507]     GeForce GTX 4xx/5xx (GFxxx)
[    28.507]     GeForce GTX 6xx/7xx (GKxxx)
[    28.507]     GeForce GTX 9xx     (GMxxx)
[    28.507]     GeForce GTX 10xx    (GPxxx)
[    28.507] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.507] (II) FBDEV: driver for framebuffer: fbdev
[    28.507] (II) VESA: driver for VESA chipsets: vesa
[    28.507] xf86EnableIO: failed to enable I/O ports 0000-03ff (Operation not permitted)
[    28.507] (EE) open /dev/dri/card0: No such file or directory
[    28.507] (WW) Falling back to old probe method for modesetting
[    28.507] (EE) open /dev/dri/card0: No such file or directory
[    28.507] (II) Loading sub module "fbdevhw"
[    28.507] (II) LoadModule: "fbdevhw"
[    28.507] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.508] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.508]     compiled for 1.21.1.11, module version = 0.0.2
[    28.508]     ABI class: X.Org Video Driver, version 25.2
[    28.508] (EE) Unable to find a valid framebuffer device
[    28.508] (WW) Falling back to old probe method for fbdev
[    28.508] (II) Loading sub module "fbdevhw"
[    28.508] (II) LoadModule: "fbdevhw"
[    28.508] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.508] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.508]     compiled for 1.21.1.11, module version = 0.0.2
[    28.508]     ABI class: X.Org Video Driver, version 25.2
[    28.508] (EE) open /dev/fb0: Permission denied
[    28.508] vesa: Refusing to run, Framebuffer or dri device present
[    28.508] (II) systemd-logind: releasing fd for 226:1
[    28.509] (II) Loading sub module "fb"
[    28.509] (II) LoadModule: "fb"
[    28.509] (II) Module "fb" already built-in
[    28.509] (II) Loading sub module "wfb"
[    28.509] (II) LoadModule: "wfb"
[    28.509] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    28.509] (II) Module wfb: vendor="X.Org Foundation"
[    28.509]     compiled for 1.21.1.11, module version = 1.0.0
[    28.509]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.510] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    28.510] (EE) Screen 0 deleted because of no matching config section.
[    28.510] (II) UnloadModule: "modesetting"
[    28.510] (EE) Screen 0 deleted because of no matching config section.
[    28.510] (II) UnloadModule: "fbdev"
[    28.510] (II) UnloadSubModule: "fbdevhw"
[    28.510] (EE) Device(s) detected, but none match those in the config file.
[    28.510] (II) Applying OutputClass "nvidia" to /dev/dri/card1
[    28.510]     loading driver: nvidia
[    28.995] (==) Matched nvidia as autoconfigured driver 0
[    28.995] (==) Matched nouveau as autoconfigured driver 1
[    28.995] (==) Matched modesetting as autoconfigured driver 2
[    28.995] (==) Matched fbdev as autoconfigured driver 3
[    28.995] (==) Matched vesa as autoconfigured driver 4
[    28.995] (==) Assigned the driver to the xf86ConfigLayout
[    28.995] (II) LoadModule: "nvidia"
[    28.995] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[    28.995] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.995]     compiled for 1.6.99.901, module version = 1.0.0
[    28.995]     Module class: X.Org Video Driver
[    28.995] (II) UnloadModule: "nvidia"
[    28.995] (II) Unloading nvidia
[    28.995] (II) Failed to load module "nvidia" (already loaded, 0)
[    28.995] (II) LoadModule: "nouveau"
[    28.995] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.995] (II) Module nouveau: vendor="X.Org Foundation"
[    28.995]     compiled for 1.21.1.3, module version = 1.0.17
[    28.995]     Module class: X.Org Video Driver
[    28.995]     ABI class: X.Org Video Driver, version 25.2
[    28.995] (II) UnloadModule: "nouveau"
[    28.995] (II) Unloading nouveau
[    28.995] (II) Failed to load module "nouveau" (already loaded, 0)
[    28.995] (II) LoadModule: "modesetting"
[    28.995] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.995] (II) Module modesetting: vendor="X.Org Foundation"
[    28.995]     compiled for 1.21.1.11, module version = 1.21.1
[    28.995]     Module class: X.Org Video Driver
[    28.995]     ABI class: X.Org Video Driver, version 25.2
[    28.995] (II) UnloadModule: "modesetting"
[    28.995] (II) Unloading modesetting
[    28.995] (II) Failed to load module "modesetting" (already loaded, 0)
[    28.995] (II) LoadModule: "fbdev"
[    28.995] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.995] (II) Module fbdev: vendor="X.Org Foundation"
[    28.995]     compiled for 1.21.1.11, module version = 0.5.0
[    28.996]     Module class: X.Org Video Driver
[    28.996]     ABI class: X.Org Video Driver, version 25.2
[    28.996] (II) UnloadModule: "fbdev"
[    28.996] (II) Unloading fbdev
[    28.996] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.996] (II) LoadModule: "vesa"
[    28.996] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.996] (II) Module vesa: vendor="X.Org Foundation"
[    28.996]     compiled for 1.21.1.7, module version = 2.6.0
[    28.996]     Module class: X.Org Video Driver
[    28.996]     ABI class: X.Org Video Driver, version 25.2
[    28.996] (II) UnloadModule: "vesa"
[    28.996] (II) Unloading vesa
[    28.996] (II) Failed to load module "vesa" (already loaded, 0)
[    28.996] (II) NVIDIA dlloader X Driver  555.42.06  Tue Jun  4 00:30:49 UTC 2024
[    28.996] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    28.996] (II) NOUVEAU driver Date:   Sat Jan 23 12:24:42 2021 -0500
[    28.996] (II) NOUVEAU driver for NVIDIA chipset families :
[    28.996]     RIVA TNT            (NV04)
[    28.996]     RIVA TNT2           (NV05)
[    28.996]     GeForce 256         (NV10)
[    28.996]     GeForce 2           (NV11, NV15)
[    28.996]     GeForce 4MX         (NV17, NV18)
[    28.996]     GeForce 3           (NV20)
[    28.996]     GeForce 4Ti         (NV25, NV28)
[    28.996]     GeForce FX          (NV3x)
[    28.996]     GeForce 6           (NV4x)
[    28.996]     GeForce 7           (G7x)
[    28.996]     GeForce 8           (G8x)
[    28.996]     GeForce 9           (G9x)
[    28.996]     GeForce GTX 2xx/3xx (GT2xx)
[    28.996]     GeForce GTX 4xx/5xx (GFxxx)
[    28.996]     GeForce GTX 6xx/7xx (GKxxx)
[    28.996]     GeForce GTX 9xx     (GMxxx)
[    28.996]     GeForce GTX 10xx    (GPxxx)
[    28.996] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.996] (II) FBDEV: driver for framebuffer: fbdev
[    28.996] (II) VESA: driver for VESA chipsets: vesa
[    28.996] xf86EnableIO: failed to enable I/O ports 0000-03ff (Operation not permitted)
[    28.996] (WW) Falling back to old probe method for modesetting
[    28.996] (WW) Falling back to old probe method for fbdev
[    28.996] (WW) Falling back to old probe method for modesetting
[    28.996] (WW) Falling back to old probe method for fbdev
[    28.996] (EE) No devices detected.
[    28.996] (EE) 
Fatal server error:
[    28.996] (EE) no screens found(EE) 
[    28.996] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    28.996] (EE) Please also check the log file at "/var/lib/gdm3/.local/share/xorg/Xorg.0.log" for additional information.
[    28.996] (EE) 
[    29.010] (EE) Server terminated with error (1). Closing log file.

```

NVIDIA driver version: 555 (proprietary). I have cycled  through every combination starting from 535 open to 560 proprietary.  22.04 was working fine with NVIDIA 535 open.

---

