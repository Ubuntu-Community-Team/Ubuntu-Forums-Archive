---
title: "Problem installaing desktop gui on ubuntu server"
date: 2015-02-23
forum: Desktop Environments
---

### Post by Jose_R_Pech on 2015-02-23
Good day, I don't know if here is the right place of this but I hope someone help me. I'm installing the  lightweight[COLOR=#212121] [/COLOR]desktop gui on ubuntu server 14.04, It seems to work well, but when I write my password and access the home server, shortly the server seems shutdown, but when I try it to turn it on, the home server doesn't start, I have to turn off from the power supply and turn on again, but the problem repeats. Even I tried installing the other desktops gui.

If I use it in console mode, all is perfect.

---

### Post by TheFu on 2015-02-23
Did you check the logs?

---

### Post by tgalati4 on 2015-02-24
Welcome to the forums.

Check your video RAM in BIOS, add more shared video RAM if needed.  I presume that the machine "locks up" rather than shuts down, since you have to turn off the power to reset it.  Next time it freezes, hit Control-Alt-F1 and that should bring up a terminal.  From there you can log in and shut down.

From the terminal:

```
more /var/log/Xorg.0.log
```

Spacebar to page forward, "q" to quit.  Only post errors, not the whole output.

---

### Post by Jose_R_Pech on 2015-02-27
tgalati4 thanks for you advice, but with the keys it didn't work. In the log, I'm not sure what to look. 

Again, thanks for the help.

This is the log:

```
[SIZE=2][    33.063]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    33.063] X Protocol Version 11, Revision 0
[    33.063] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    33.063] Current Operating System: Linux ubuntu 3.13.0-46-generic #76-Ubuntu SMP Thu Feb 26 18:52:13 UTC 2015 x86_64
[    33.063] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=3b18d0fa-065d-4d1a-8c56-e14b8df675f2 ro
[    33.064] Build Date: 12 February 2015  02:49:29PM
[    33.064] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    33.064] Current version of pixman: 0.30.2
[    33.064]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    33.064] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.064] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 27 13:39:50 2015
[    33.130] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.131] (==) No Layout section.  Using the first Screen section.
[    33.131] (==) No screen section available. Using defaults.
[    33.131] (**) |-->Screen "Default Screen Section" (0)
[    33.131] (**) |   |-->Monitor "<default monitor>"
[    33.131] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    33.131] (==) Automatically adding devices
[    33.131] (==) Automatically enabling devices
[    33.131] (==) Automatically adding GPU devices
[    33.131] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (==) FontPath set to:
        /usr/share/fonts/X11/misc,built-ins
[    33.131] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.131] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.131] (II) Loader magic: 0x7fdd350b9d40
[    33.131] (II) Module ABI versions:
[    33.131]    X.Org ANSI C Emulation: 0.4
[    33.131]    X.Org Video Driver: 15.0
[    33.131]    X.Org XInput driver : 20.0
[    33.131]    X.Org Server Extension : 8.0
[    33.132] (II) xfree86: Adding drm device (/dev/dri/card0)
[    33.133] (--) PCI:*(0:0:2:0) 8086:2972:8086:5354 rev 2, Mem @ 0x90100000/1048576, 0x80000000/268435456, I/O @ 0x000020e0/8
[    33.133] Initializing built-in extension Generic Event Extension
[    33.133] Initializing built-in extension SHAPE
[    33.133] Initializing built-in extension MIT-SHM
[    33.133] Initializing built-in extension XInputExtension
[    33.133] Initializing built-in extension XTEST
[    33.133] Initializing built-in extension BIG-REQUESTS
[    33.133] Initializing built-in extension SYNC
[    33.131] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    33.131]    Entry deleted from font path.
[    33.131] (==) FontPath set to:
        /usr/share/fonts/X11/misc,built-ins
[    33.131] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    33.131] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    33.131] (II) Loader magic: 0x7fdd350b9d40
[    33.131] (II) Module ABI versions:
[    33.131]    X.Org ANSI C Emulation: 0.4
[    33.131]    X.Org Video Driver: 15.0
[    33.131]    X.Org XInput driver : 20.0
[    33.131]    X.Org Server Extension : 8.0
[    33.132] (II) xfree86: Adding drm device (/dev/dri/card0)
[    33.133] (--) PCI:*(0:0:2:0) 8086:2972:8086:5354 rev 2, Mem @ 0x90100000/1048576, 0x80000000/268435456, I/O @ 0x000020e0/8
[    33.133] Initializing built-in extension Generic Event Extension
[    33.133] Initializing built-in extension SHAPE
[    33.133] Initializing built-in extension MIT-SHM
[    33.133] Initializing built-in extension XInputExtension
[    33.133] Initializing built-in extension XTEST
[    33.133] Initializing built-in extension BIG-REQUESTS
[    33.133] Initializing built-in extension SYNC
[    33.133] Initializing built-in extension XKEYBOARD
[    33.133] Initializing built-in extension XC-MISC
[    33.133] Initializing built-in extension SECURITY
[    33.133] Initializing built-in extension XINERAMA
[    33.133] Initializing built-in extension XFIXES
[    33.133] Initializing built-in extension RENDER
[    33.133] Initializing built-in extension RANDR
[    33.133] Initializing built-in extension COMPOSITE
[    33.133] Initializing built-in extension DAMAGE
[    33.134] Initializing built-in extension MIT-SCREEN-SAVER
[    33.134] Initializing built-in extension DOUBLE-BUFFER
[    33.134] Initializing built-in extension RECORD
[    33.134] Initializing built-in extension DPMS
[    33.134] Initializing built-in extension Present
[    33.134] Initializing built-in extension DRI3
[    33.134] Initializing built-in extension X-Resource
[    33.134] Initializing built-in extension XVideo
[    33.134] Initializing built-in extension XVideo-MotionCompensation
[    33.134] Initializing built-in extension SELinux
[    33.134] Initializing built-in extension XFree86-VidModeExtension
[    33.134] Initializing built-in extension XFree86-DGA
[    33.134] Initializing built-in extension XFree86-DRI
[    33.134] Initializing built-in extension DRI2
[    33.134] (II) LoadModule: "glx"
[    33.264] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    33.770] (II) Module glx: vendor="X.Org Foundation"
[    33.770]    compiled for 1.15.1, module version = 1.0.0
[    33.770]    ABI class: X.Org Server Extension, version 8.0
[    33.771] (==) AIGLX enabled
[    33.771] Loading extension GLX
[    33.133] Initializing built-in extension XC-MISC
[    33.133] Initializing built-in extension SECURITY
[    33.133] Initializing built-in extension XINERAMA
[    33.133] Initializing built-in extension XFIXES
[    33.133] Initializing built-in extension RENDER
[    33.133] Initializing built-in extension RANDR
[    33.133] Initializing built-in extension COMPOSITE
[    33.133] Initializing built-in extension DAMAGE
[    33.134] Initializing built-in extension MIT-SCREEN-SAVER
[    33.134] Initializing built-in extension DOUBLE-BUFFER
[    33.134] Initializing built-in extension RECORD
[    33.134] Initializing built-in extension DPMS
[    33.134] Initializing built-in extension Present
[    33.134] Initializing built-in extension DRI3
[    33.134] Initializing built-in extension X-Resource
[    33.134] Initializing built-in extension XVideo
[    33.134] Initializing built-in extension XVideo-MotionCompensation
[    33.134] Initializing built-in extension SELinux
[    33.134] Initializing built-in extension XFree86-VidModeExtension
[    33.134] Initializing built-in extension XFree86-DGA
[    33.134] Initializing built-in extension XFree86-DRI
[    33.134] Initializing built-in extension DRI2
[    33.134] (II) LoadModule: "glx"
[    33.264] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    33.770] (II) Module glx: vendor="X.Org Foundation"
[    33.770]    compiled for 1.15.1, module version = 1.0.0
[    33.770]    ABI class: X.Org Server Extension, version 8.0
[    33.771] (==) AIGLX enabled
[    33.771] Loading extension GLX
[    33.771] (==) Matched intel as autoconfigured driver 0
[    33.771] (==) Matched intel as autoconfigured driver 1
[    33.771] (==) Matched modesetting as autoconfigured driver 2
[    33.771] (==) Matched fbdev as autoconfigured driver 3
[    33.771] (==) Matched vesa as autoconfigured driver 4
[    33.771] (==) Assigned the driver to the xf86ConfigLayout
[    33.771] (II) LoadModule: "intel"
[    33.771] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.784] (II) Module intel: vendor="X.Org Foundation"
[    33.784]    compiled for 1.15.1, module version = 2.99.910
[    33.784]    Module class: X.Org Video Driver
[    33.784]    ABI class: X.Org Video Driver, version 15.0
[    33.784] (II) LoadModule: "modesetting"
[    33.784] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    33.785] (II) Module modesetting: vendor="X.Org Foundation"
[    33.785]    compiled for 1.15.0, module version = 0.8.1
[    33.785]    Module class: X.Org Video Driver
[    33.785]    ABI class: X.Org Video Driver, version 15.0
[    33.785] (II) LoadModule: "fbdev"
[    33.785] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.785] (II) Module fbdev: vendor="X.Org Foundation"
[    33.785]    compiled for 1.15.0, module version = 0.4.4
[    33.785]    Module class: X.Org Video Driver
[    33.785]    ABI class: X.Org Video Driver, version 15.0
[    33.785] (II) LoadModule: "vesa"
[    33.785] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.785] (II) Module vesa: vendor="X.Org Foundation"
[    33.785]    compiled for 1.15.0, module version = 2.3.3
[    33.785]    Module class: X.Org Video Driver
[    33.785]    ABI class: X.Org Video Driver, version 15.0
[    33.771] (==) Matched intel as autoconfigured driver 1
[    33.771] (==) Matched modesetting as autoconfigured driver 2
[    33.771] (==) Matched fbdev as autoconfigured driver 3
[    33.771] (==) Matched vesa as autoconfigured driver 4
[    33.771] (==) Assigned the driver to the xf86ConfigLayout
[    33.771] (II) LoadModule: "intel"
[    33.771] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.784] (II) Module intel: vendor="X.Org Foundation"
[    33.784]    compiled for 1.15.1, module version = 2.99.910
[    33.784]    Module class: X.Org Video Driver
[    33.784]    ABI class: X.Org Video Driver, version 15.0
[    33.784] (II) LoadModule: "modesetting"
[    33.784] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    33.785] (II) Module modesetting: vendor="X.Org Foundation"
[    33.785]    compiled for 1.15.0, module version = 0.8.1
[    33.785]    Module class: X.Org Video Driver
[    33.785]    ABI class: X.Org Video Driver, version 15.0
[    33.785] (II) LoadModule: "fbdev"
[    33.785] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.785] (II) Module fbdev: vendor="X.Org Foundation"
[    33.785]    compiled for 1.15.0, module version = 0.4.4
[    33.785]    Module class: X.Org Video Driver
[    33.785]    ABI class: X.Org Video Driver, version 15.0
[    33.785] (II) LoadModule: "vesa"
[    33.785] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.785] (II) Module vesa: vendor="X.Org Foundation"
[    33.785]    compiled for 1.15.0, module version = 2.3.3
[    33.785]    Module class: X.Org Video Driver
[    33.785]    ABI class: X.Org Video Driver, version 15.0
[    33.785] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE,G33, Q35, Q33,GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    33.786] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    33.786] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    33.786] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    33.786] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    33.786] (II) FBDEV: driver for framebuffer: fbdev
[    33.786] (II) VESA: driver for VESA chipsets: vesa
[    33.786] (++) using VT number 7
[    33.786] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.4 (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[    33.787] (WW) Falling back to old probe method for modesetting
[    33.787] (WW) Falling back to old probe method for fbdev
[    33.787] (II) Loading sub module "fbdevhw"
[    33.787] (II) LoadModule: "fbdevhw"
[    33.811] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.811] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.811]    compiled for 1.15.1, module version = 0.0.2
[    33.811]    ABI class: X.Org Video Driver, version 15.0
[    33.811] (WW) Falling back to old probe method for vesa
[    33.812] (--) intel(0): Integrated Graphics Chipset: Intel(R) 946GZ
[    33.812] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[    33.812] (II) intel(0): Creating default Display subsection in Screen section "Default Screen Section" for depth/fbbpp 24/32
[    33.812] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    33.812] (==) intel(0): RGB weight 888
[    33.812] (==) intel(0): Default visual is TrueColori810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    33.786] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    33.786] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    33.786] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    33.786] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    33.786] (II) FBDEV: driver for framebuffer: fbdev
[    33.786] (II) VESA: driver for VESA chipsets: vesa
[    33.786] (++) using VT number 7


[    33.786] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.4 (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[    33.787] (WW) Falling back to old probe method for modesetting
[    33.787] (WW) Falling back to old probe method for fbdev
[    33.787] (II) Loading sub module "fbdevhw"
[    33.787] (II) LoadModule: "fbdevhw"
[    33.811] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.811] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.811]    compiled for 1.15.1, module version = 0.0.2
[    33.811]    ABI class: X.Org Video Driver, version 15.0
[    33.811] (WW) Falling back to old probe method for vesa
[    33.812] (--) intel(0): Integrated Graphics Chipset: Intel(R) 946GZ
[    33.812] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[    33.812] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    33.812] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    33.812] (==) intel(0): RGB weight 888
[    33.812] (==) intel(0): Default visual is TrueColor
[    33.812] (**) intel(0): Framebuffer tiled
[    33.812] (**) intel(0): Pixmaps tiled
[    33.812] (**) intel(0): "Tear free" disabled
[    33.812] (**) intel(0): Forcing per-crtc-pixmaps? no
[    33.813] (II) intel(0): Output VGA1 has no monitor section
[    33.813] (II) intel(0): Output VIRTUAL1 has no monitor section
[    33.813] (--) intel(0): Output VGA1 using initial mode 1280x720 on pipe 0
[    33.813] (==) intel(0): DPI set to (96, 96)
[    33.813] (II) Loading sub module "dri2"
[    33.813] (II) LoadModule: "dri2"
[    33.813] (II) Module "dri2" already built-in
[    33.813] (II) UnloadModule: "modesetting"
[    33.813] (II) Unloading modesetting
[    33.813] (II) UnloadModule: "fbdev"
[    33.813] (II) Unloading fbdev
[    33.813] (II) UnloadSubModule: "fbdevhw"
[    33.813] (II) Unloading fbdevhw
[    33.813] (II) UnloadModule: "vesa"
[    33.813] (II) Unloading vesa
[    33.813] (==) Depth 24 pixmap format is 32 bpp
[    33.814] (II) intel(0): SNA initialized with Broadwater (gen4) backend
[    33.814] (==) intel(0): Backing store enabled
[    33.814] (==) intel(0): Silken mouse enabled
[    33.814] (II) intel(0): HW Cursor enabled
[    33.814] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    33.814] (==) intel(0): DPMS enabled
[    33.814] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    33.814] (II) intel(0): [DRI2] Setup complete
[    33.814] (II) intel(0): [DRI2]   DRI driver: i965
[    33.814] (II) intel(0): [DRI2]   VDPAU driver: i965
[    33.812] (**) intel(0): Pixmaps tiled
[    33.812] (**) intel(0): "Tear free" disabled
[    33.812] (**) intel(0): Forcing per-crtc-pixmaps? no
[    33.813] (II) intel(0): Output VGA1 has no monitor section
[    33.813] (II) intel(0): Output VIRTUAL1 has no monitor section
[    33.813] (--) intel(0): Output VGA1 using initial mode 1280x720 on pipe 0
[    33.813] (==) intel(0): DPI set to (96, 96)
[    33.813] (II) Loading sub module "dri2"
[    33.813] (II) LoadModule: "dri2"
[    33.813] (II) Module "dri2" already built-in
[    33.813] (II) UnloadModule: "modesetting"
[    33.813] (II) Unloading modesetting
[    33.813] (II) UnloadModule: "fbdev"
[    33.813] (II) Unloading fbdev
[    33.813] (II) UnloadSubModule: "fbdevhw"
[    33.813] (II) Unloading fbdevhw
[    33.813] (II) UnloadModule: "vesa"
[    33.813] (II) Unloading vesa
[    33.813] (==) Depth 24 pixmap format is 32 bpp
[    33.814] (II) intel(0): SNA initialized with Broadwater (gen4) backend
[    33.814] (==) intel(0): Backing store enabled
[    33.814] (==) intel(0): Silken mouse enabled
[    33.814] (II) intel(0): HW Cursor enabled
[    33.814] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    33.814] (==) intel(0): DPMS enabled
[    33.814] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    33.814] (II) intel(0): [DRI2] Setup complete
[    33.814] (II) intel(0): [DRI2]   DRI driver: i965
[    33.814] (II) intel(0): [DRI2]   VDPAU driver: i965
[    33.814] (II) intel(0): direct rendering: DRI2 Enabled
[    33.814] (==) intel(0): hotplug detection: "enabled"
[    33.814] (--) RandR disabled
[    33.828] (II) SELinux: Disabled on system
[    33.870] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    33.870] (II) AIGLX: enabled GLX_ARB_create_context
[    33.870] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    33.870] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    33.870] (II) AIGLX: enabled GLX_INTEL_swap_event
[    33.870] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    33.870] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    33.870] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    33.870] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    33.870] (II) AIGLX: Loaded and initialized i965
[    33.870] (II) GLX: Initialized DRI2 GL provider for screen 0
[    33.876] (II) intel(0): switch to mode 1280x720@59.9 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    33.892] (II) intel(0): Setting screen physical size to 338 x 190
[    33.906] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.911] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.911] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.911] (II) LoadModule: "evdev"
[    33.911] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.937] (II) Module evdev: vendor="X.Org Foundation"
[    33.937]    compiled for 1.15.0, module version = 2.8.2
[    33.937]    Module class: X.Org XInput Driver
[    33.937]    ABI class: X.Org XInput driver, version 20.0
[    33.937] (II) Using input driver 'evdev' for 'Power Button'
[    33.938] (**) Power Button: always reports core events
[    33.938] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.938] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.814] (==) intel(0): hotplug detection: "enabled"
[    33.814] (--) RandR disabled
[    33.828] (II) SELinux: Disabled on system
[    33.870] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    33.870] (II) AIGLX: enabled GLX_ARB_create_context
[    33.870] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    33.870] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    33.870] (II) AIGLX: enabled GLX_INTEL_swap_event
[    33.870] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    33.870] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    33.870] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    33.870] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    33.870] (II) AIGLX: Loaded and initialized i965
[    33.870] (II) GLX: Initialized DRI2 GL provider for screen 0
[    33.876] (II) intel(0): switch to mode 1280x720@59.9 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[    33.892] (II) intel(0): Setting screen physical size to 338 x 190
[    33.906] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.911] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.911] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.911] (II) LoadModule: "evdev"
[    33.911] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.937] (II) Module evdev: vendor="X.Org Foundation"
[    33.937]    compiled for 1.15.0, module version = 2.8.2
[    33.937]    Module class: X.Org XInput Driver
[    33.937]    ABI class: X.Org XInput driver, version 20.0
[    33.937] (II) Using input driver 'evdev' for 'Power Button'
[    33.938] (**) Power Button: always reports core events
[    33.938] (**) evdev: Power Button: Device: "/dev/input/event1"
[    33.938] (--) evdev: Power Button: Vendor 0 Product 0x1
[    33.938] (--) evdev: Power Button: Found keys
[    33.938] (II) evdev: Power Button: Configuring as keyboard
[    33.938] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    33.938] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.938] (**) Option "xkb_rules" "evdev"
[    33.938] (**) Option "xkb_model" "pc105"
[    33.938] (**) Option "xkb_layout" "es"
[    33.944] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    33.945] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    33.945] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    33.945] (II) Using input driver 'evdev' for 'Sleep Button'
[    33.945] (**) Sleep Button: always reports core events
[    33.945] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    33.945] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    33.945] (--) evdev: Sleep Button: Found keys
[    33.945] (II) evdev: Sleep Button: Configuring as keyboard
[    33.945] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    33.945] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[    33.945] (**) Option "xkb_rules" "evdev"
[    33.945] (**) Option "xkb_model" "pc105"
[    33.945] (**) Option "xkb_layout" "es"
[    33.946] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    33.946] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    33.946] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    33.946] (II) No input driver specified, ignoring this device.
[    33.946] (II) This device may have been added with another device file.
[    33.947] (II) config/udev: Adding input device HDA Intel Speaker Front (/dev/input/event6)
[    33.947] (II) No input driver specified, ignoring this device.
[    33.947] (II) This device may have been added with another device file.
[    33.947] (II) config/udev: Adding input device HDA Intel Speaker Surround (/dev/input/event5)
[    33.938] (II) evdev: Power Button: Configuring as keyboard
[    33.938] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    33.938] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.938] (**) Option "xkb_rules" "evdev"
[    33.938] (**) Option "xkb_model" "pc105"
[    33.938] (**) Option "xkb_layout" "es"
[    33.944] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    33.945] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    33.945] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    33.945] (II) Using input driver 'evdev' for 'Sleep Button'
[    33.945] (**) Sleep Button: always reports core events
[    33.945] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    33.945] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    33.945] (--) evdev: Sleep Button: Found keys
[    33.945] (II) evdev: Sleep Button: Configuring as keyboard
[    33.945] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    33.945] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[    33.945] (**) Option "xkb_rules" "evdev"
[    33.945] (**) Option "xkb_model" "pc105"
[    33.945] (**) Option "xkb_layout" "es"
[    33.946] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    33.946] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    33.946] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    33.946] (II) No input driver specified, ignoring this device.
[    33.946] (II) This device may have been added with another device file.
[    33.947] (II) config/udev: Adding input device HDA Intel Speaker Front (/dev/input/event6)
[    33.947] (II) No input driver specified, ignoring this device.
[    33.947] (II) This device may have been added with another device file.
[    33.947] (II) config/udev: Adding input device HDA Intel Speaker Surround (/dev/input/event5)
[    33.947] (II) No input driver specified, ignoring this device.
[    33.947] (II) This device may have been added with another device file.
[    33.947] (II) config/udev: Adding input device HDA Intel Speaker CLFE (/dev/input/event4)
[    33.948] (II) No input driver specified, ignoring this device.
[    33.948] (II) This device may have been added with another device file.
[    33.948] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event3)
[    33.948] (II) No input driver specified, ignoring this device.
[    33.948] (II) This device may have been added with another device file.
[    33.949] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    33.949] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.949] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.949] (**) AT Translated Set 2 keyboard: always reports core events
[    33.949] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    33.949] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    33.949] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    33.949] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    33.949] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    33.949] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[    33.949] (**) Option "xkb_rules" "evdev"
[    33.949] (**) Option "xkb_model" "pc105"
[    33.949] (**) Option "xkb_layout" "es"
[    39.620] (II) intel(0): EDID vendor "ACR", prod id 12800
[    39.620] (II) intel(0): Using EDID range info for horizontal sync
[    39.620] (II) intel(0): Using EDID range info for vertical refresh
[    39.620] (II) intel(0): Printing DDC gathered Modelines:
[    39.620] (II) intel(0): Modeline "1280x720"x0.0   74.50  1280 1344 1472 1664  720 723 728 748 -hsync -vsync (44.8 kHz eP)
[    39.620] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    39.620] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    39.620] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    39.620] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    33.947] (II) This device may have been added with another device file.
[    33.947] (II) config/udev: Adding input device HDA Intel Speaker CLFE (/dev/input/event4)
[    33.948] (II) No input driver specified, ignoring this device.
[    33.948] (II) This device may have been added with another device file.
[    33.948] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event3)
[    33.948] (II) No input driver specified, ignoring this device.
[    33.948] (II) This device may have been added with another device file.
[    33.949] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    33.949] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.949] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.949] (**) AT Translated Set 2 keyboard: always reports core events
[    33.949] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    33.949] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    33.949] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    33.949] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    33.949] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    33.949] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[    33.949] (**) Option "xkb_rules" "evdev"
[    33.949] (**) Option "xkb_model" "pc105"
[    33.949] (**) Option "xkb_layout" "es"
[    39.620] (II) intel(0): EDID vendor "ACR", prod id 12800
[    39.620] (II) intel(0): Using EDID range info for horizontal sync
[    39.620] (II) intel(0): Using EDID range info for vertical refresh
[    39.620] (II) intel(0): Printing DDC gathered Modelines:
[    39.620] (II) intel(0): Modeline "1280x720"x0.0   74.50  1280 1344 1472 1664  720 723 728 748 -hsync -vsync (44.8 kHz eP)
[    39.620] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    39.620] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    39.620] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    39.620] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    39.620] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    39.620] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    39.620] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    39.620] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    39.620] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    39.620] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    39.620] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    39.620] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    39.620] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    39.620] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    39.620] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  6876.752] (II) intel(0): switch to mode 1280x720@59.9 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none
[  6876.808] (II) intel(0): switch to mode 1280x720@59.9 on VGA1 using pipe 0, position (0, 0), rotation normal, reflection none[/SIZE]
```







[SIZE=2][FONT=arial]
[/FONT][/SIZE]

---

### Post by TheFu on 2015-02-27
[B]sudo lshw -C video
[/B]
here's mine:
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:58 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:1800(size=64)
```

I run ubuntu server 14.04 with openbox or fluxbox on my desktop machines.

---

