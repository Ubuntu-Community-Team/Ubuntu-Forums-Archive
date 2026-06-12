---
title: "Intel 965 Graphics 1680X1050"
date: 2017-04-30
forum: Debian
---

### Post by friedchips2 on 2017-04-30
Hey all, got a lenovo T61 with an intel 965GM graphics chipset. When I go to screen resolution it only says up to 1280x800 for options. I'm almost positive it's 1680x1050 capable. I'm used to old xorg.conf stuff. What do I do now?

---

### Post by Yellow Pasque on 2017-04-30
If you look at the specs, 1280x800 displays were available for the 14" and 15" models: [https://support.lenovo.com/us/en/solutions/pd008989#vid](https://support.lenovo.com/us/en/solutions/pd008989#vid)

> I'm almost positive it's 1680x1050 capable

What are you basing that on? Does 1280x800 look fuzzy (like it may be a non-native resolution)?

A look at /var/log/Xorg.0.log might provide some clues (use code tags or pastebin if you share it).

---

### Post by friedchips2 on 2017-04-30
I have another T61, so in hindsight that was probably a wrong assumption to make cuz now that I'm looking the two have different graphics chipsets.

Here is the log

```
stephen@samurai:~$ cat /var/log/Xorg.0.log
[    27.000] 
X.Org X Server 1.16.4
Release Date: 2014-12-20
[    27.000] X Protocol Version 11, Revision 0
[    27.000] Build Operating System: Linux 3.16.0-4-amd64 x86_64 Debian
[    27.000] Current Operating System: Linux samurai 3.16.0-4-amd64 #1 SMP Debian 3.16.39-1+deb8u2 (2017-03-07) x86_64
[    27.000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-4-amd64 root=UUID=e1ae1fa2-eb73-4621-ae3f-dcf1cd83ccae ro initrd=/install/initrd.gz quiet
[    27.000] Build Date: 11 February 2015  12:32:02AM
[    27.000] xorg-server 2:1.16.4-1 (http://www.debian.org/support) 
[    27.000] Current version of pixman: 0.32.6
[    27.000]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.000] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.000] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 30 23:05:16 2017
[    27.036] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.063] (==) No Layout section.  Using the first Screen section.
[    27.063] (==) No screen section available. Using defaults.
[    27.063] (**) |-->Screen "Default Screen Section" (0)
[    27.063] (**) |   |-->Monitor "<default monitor>"
[    27.089] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    27.089] (==) Automatically adding devices
[    27.089] (==) Automatically enabling devices
[    27.089] (==) Automatically adding GPU devices
[    27.150] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.150]     Entry deleted from font path.
[    27.154] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    27.154] (==) ModulePath set to "/usr/lib/xorg/modules"
[    27.154] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.170] (II) Loader magic: 0x7f1fbbb3cd80
[    27.170] (II) Module ABI versions:
[    27.170]     X.Org ANSI C Emulation: 0.4
[    27.170]     X.Org Video Driver: 18.0
[    27.170]     X.Org XInput driver : 21.0
[    27.170]     X.Org Server Extension : 8.0
[    27.171] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.173] (--) PCI:*(0:0:2:0) 8086:2a02:17aa:20b5 rev 12, Mem @ 0xf8100000/1048576, 0xe0000000/268435456, I/O @ 0x00001800/8
[    27.173] (--) PCI: (0:0:2:1) 8086:2a03:17aa:20b5 rev 12, Mem @ 0xf8200000/1048576
[    27.174] (II) LoadModule: "glx"
[    27.195] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.780] (II) Module glx: vendor="X.Org Foundation"
[    27.780]     compiled for 1.16.4, module version = 1.0.0
[    27.780]     ABI class: X.Org Server Extension, version 8.0
[    27.780] (==) AIGLX enabled
[    27.780] (==) Matched intel as autoconfigured driver 0
[    27.780] (==) Matched intel as autoconfigured driver 1
[    27.780] (==) Matched modesetting as autoconfigured driver 2
[    27.780] (==) Matched fbdev as autoconfigured driver 3
[    27.780] (==) Matched vesa as autoconfigured driver 4
[    27.780] (==) Assigned the driver to the xf86ConfigLayout
[    27.780] (II) LoadModule: "intel"
[    27.803] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.005] (II) Module intel: vendor="X.Org Foundation"
[    28.005]     compiled for 1.15.99.904, module version = 2.21.15
[    28.005]     Module class: X.Org Video Driver
[    28.005]     ABI class: X.Org Video Driver, version 18.0
[    28.005] (II) LoadModule: "modesetting"
[    28.005] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.022] (II) Module modesetting: vendor="X.Org Foundation"
[    28.022]     compiled for 1.16.4, module version = 0.9.0
[    28.022]     Module class: X.Org Video Driver
[    28.022]     ABI class: X.Org Video Driver, version 18.0
[    28.022] (II) LoadModule: "fbdev"
[    28.022] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.032] (II) Module fbdev: vendor="X.Org Foundation"
[    28.032]     compiled for 1.15.99.904, module version = 0.4.4
[    28.032]     Module class: X.Org Video Driver
[    28.032]     ABI class: X.Org Video Driver, version 18.0
[    28.032] (II) LoadModule: "vesa"
[    28.032] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.044] (II) Module vesa: vendor="X.Org Foundation"
[    28.044]     compiled for 1.15.99.904, module version = 2.3.3
[    28.044]     Module class: X.Org Video Driver
[    28.044]     ABI class: X.Org Video Driver, version 18.0
[    28.044] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    28.045] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.046] (II) FBDEV: driver for framebuffer: fbdev
[    28.046] (II) VESA: driver for VESA chipsets: vesa
[    28.046] (++) using VT number 7

[    28.064] (WW) Falling back to old probe method for modesetting
[    28.064] (WW) Falling back to old probe method for fbdev
[    28.064] (II) Loading sub module "fbdevhw"
[    28.064] (II) LoadModule: "fbdevhw"
[    28.073] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.084] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.084]     compiled for 1.16.4, module version = 0.0.2
[    28.084]     ABI class: X.Org Video Driver, version 18.0
[    28.084] (WW) Falling back to old probe method for vesa
[    28.084] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.084] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    28.084] (==) intel(0): RGB weight 888
[    28.084] (==) intel(0): Default visual is TrueColor
[    28.084] (--) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    28.084] (**) intel(0): Relaxed fencing enabled
[    28.084] (**) intel(0): Wait on SwapBuffers? enabled
[    28.084] (**) intel(0): Triple buffering? enabled
[    28.084] (**) intel(0): Framebuffer tiled
[    28.084] (**) intel(0): Pixmaps tiled
[    28.084] (**) intel(0): 3D buffers tiled
[    28.084] (**) intel(0): SwapBuffers wait enabled
[    28.084] (==) intel(0): video overlay key set to 0x101fe
[    28.085] (II) intel(0): Output LVDS1 has no monitor section
[    28.085] (--) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    28.120] (II) intel(0): Output VGA1 has no monitor section
[    28.130] (II) intel(0): Output DVI1 has no monitor section
[    28.130] (II) intel(0): EDID for output LVDS1
[    28.130] (II) intel(0): Manufacturer: LEN  Model: 4050  Serial#: 0
[    28.130] (II) intel(0): Year: 2006  Week: 0
[    28.130] (II) intel(0): EDID Version: 1.3
[    28.130] (II) intel(0): Digital Display Input
[    28.130] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    28.130] (II) intel(0): Gamma: 2.20
[    28.130] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[    28.130] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    28.130] (II) intel(0): First detailed timing is preferred mode
[    28.130] (II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.320 greenY: 0.550
[    28.131] (II) intel(0): blueX: 0.152 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
[    28.131] (II) intel(0): Manufacturer's mask: 0
[    28.131] (II) intel(0): Supported detailed timing:
[    28.131] (II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
[    28.131] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    28.131] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    28.131] (II) intel(0): Supported detailed timing:
[    28.131] (II) intel(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
[    28.131] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    28.131] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    28.131] (II) intel(0): Unknown vendor-specific block f
[    28.131] (II) intel(0):  LTN154X3-L02
[    28.131] (II) intel(0): EDID (in hex):
[    28.131] (II) intel(0):     00ffffffffffff0030ae504000000000
[    28.131] (II) intel(0):     0010010380211578ea03159757528c27
[    28.131] (II) intel(0):     21505400000001010101010101010101
[    28.131] (II) intel(0):     010101010101c71b00a0502017303020
[    28.131] (II) intel(0):     36004bcf10000019261700a050201730
[    28.131] (II) intel(0):     302036004bcf100000190000000f0081
[    28.131] (II) intel(0):     0a32810a281401004ca35833000000fe
[    28.131] (II) intel(0):     004c544e31353458332d4c30320a0029
[    28.132] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    28.132] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    28.132] (II) intel(0): Printing probed modes for output LVDS1
[    28.132] (II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    28.132] (II) intel(0): Modeline "1280x800"x50.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[    28.132] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    28.132] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    28.132] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    28.132] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    28.168] (II) intel(0): EDID for output VGA1
[    28.178] (II) intel(0): EDID for output DVI1
[    28.178] (II) intel(0): Output LVDS1 connected
[    28.178] (II) intel(0): Output VGA1 disconnected
[    28.178] (II) intel(0): Output DVI1 disconnected
[    28.178] (II) intel(0): Using exact sizes for initial modes
[    28.178] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    28.178] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.178] (II) intel(0): Kernel page flipping support detected, enabling
[    28.178] (==) intel(0): DPI set to (96, 96)
[    28.178] (II) Loading sub module "fb"
[    28.178] (II) LoadModule: "fb"
[    28.179] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.193] (II) Module fb: vendor="X.Org Foundation"
[    28.193]     compiled for 1.16.4, module version = 1.0.0
[    28.193]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.193] (II) Loading sub module "dri2"
[    28.193] (II) LoadModule: "dri2"
[    28.193] (II) Module "dri2" already built-in
[    28.193] (II) UnloadModule: "modesetting"
[    28.193] (II) Unloading modesetting
[    28.193] (II) UnloadModule: "fbdev"
[    28.193] (II) Unloading fbdev
[    28.193] (II) UnloadSubModule: "fbdevhw"
[    28.193] (II) Unloading fbdevhw
[    28.194] (II) UnloadModule: "vesa"
[    28.194] (II) Unloading vesa
[    28.194] (==) Depth 24 pixmap format is 32 bpp
[    28.208] (II) intel(0): [DRI2] Setup complete
[    28.208] (II) intel(0): [DRI2]   DRI driver: i965
[    28.208] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    28.234] (II) UXA(0): Driver registered support for the following operations:
[    28.234] (II)         solid
[    28.234] (II)         copy
[    28.234] (II)         composite (RENDER acceleration)
[    28.234] (II)         put_image
[    28.234] (II)         get_image
[    28.234] (==) intel(0): Backing store enabled
[    28.234] (==) intel(0): Silken mouse enabled
[    28.235] (II) intel(0): Initializing HW Cursor
[    28.235] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.238] (==) intel(0): DPMS enabled
[    28.238] (==) intel(0): Intel XvMC decoder enabled
[    28.239] (II) intel(0): Set up textured video
[    28.239] (II) intel(0): Set up overlay video
[    28.239] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    28.239] (II) intel(0): direct rendering: DRI2 Enabled
[    28.239] (==) intel(0): hotplug detection: "enabled"
[    28.745] (--) RandR disabled
[    28.753] (II) SELinux: Disabled on system
[    28.993] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.993] (II) AIGLX: enabled GLX_ARB_create_context
[    28.993] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    28.993] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    28.993] (II) AIGLX: enabled GLX_INTEL_swap_event
[    28.993] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.993] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    28.993] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    28.993] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    28.993] (II) AIGLX: Loaded and initialized i965
[    28.993] (II) GLX: Initialized DRI2 GL provider for screen 0
[    28.994] (II) intel(0): Setting screen physical size to 338 x 211
[    29.454] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.454] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.454] (II) LoadModule: "evdev"
[    29.454] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.527] (II) Module evdev: vendor="X.Org Foundation"
[    29.527]     compiled for 1.16.0, module version = 2.9.0
[    29.527]     Module class: X.Org XInput Driver
[    29.527]     ABI class: X.Org XInput driver, version 21.0
[    29.527] (II) Using input driver 'evdev' for 'Power Button'
[    29.527] (**) Power Button: always reports core events
[    29.527] (**) evdev: Power Button: Device: "/dev/input/event3"
[    29.527] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.527] (--) evdev: Power Button: Found keys
[    29.527] (II) evdev: Power Button: Configuring as keyboard
[    29.527] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4/event3"
[    29.527] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.527] (**) Option "xkb_rules" "evdev"
[    29.527] (**) Option "xkb_model" "pc105"
[    29.527] (**) Option "xkb_layout" "us"
[    29.531] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    29.531] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.531] (II) Using input driver 'evdev' for 'Video Bus'
[    29.531] (**) Video Bus: always reports core events
[    29.531] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    29.531] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.531] (--) evdev: Video Bus: Found keys
[    29.531] (II) evdev: Video Bus: Configuring as keyboard
[    29.531] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event5"
[    29.531] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    29.531] (**) Option "xkb_rules" "evdev"
[    29.531] (**) Option "xkb_model" "pc105"
[    29.531] (**) Option "xkb_layout" "us"
[    29.532] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    29.532] (II) No input driver specified, ignoring this device.
[    29.532] (II) This device may have been added with another device file.
[    29.532] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    29.532] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.532] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.532] (**) Sleep Button: always reports core events
[    29.532] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    29.532] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    29.532] (--) evdev: Sleep Button: Found keys
[    29.532] (II) evdev: Sleep Button: Configuring as keyboard
[    29.532] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input3/event2"
[    29.532] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    29.532] (**) Option "xkb_rules" "evdev"
[    29.532] (**) Option "xkb_model" "pc105"
[    29.532] (**) Option "xkb_layout" "us"
[    29.533] (II) config/udev: Adding input device HDA Intel Dock Mic (/dev/input/event9)
[    29.533] (II) No input driver specified, ignoring this device.
[    29.533] (II) This device may have been added with another device file.
[    29.534] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[    29.534] (II) No input driver specified, ignoring this device.
[    29.534] (II) This device may have been added with another device file.
[    29.534] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
[    29.534] (II) No input driver specified, ignoring this device.
[    29.534] (II) This device may have been added with another device file.
[    29.534] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event0)
[    29.534] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.534] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.534] (**) AT Translated Set 2 keyboard: always reports core events
[    29.534] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event0"
[    29.535] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.535] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.535] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.535] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input0/event0"
[    29.535] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    29.535] (**) Option "xkb_rules" "evdev"
[    29.535] (**) Option "xkb_model" "pc105"
[    29.535] (**) Option "xkb_layout" "us"
[    29.535] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    29.535] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    29.535] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    29.535] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    29.535] (II) LoadModule: "synaptics"
[    29.536] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.560] (II) Module synaptics: vendor="X.Org Foundation"
[    29.560]     compiled for 1.16.0.901, module version = 1.8.99
[    29.560]     Module class: X.Org XInput Driver
[    29.560]     ABI class: X.Org XInput driver, version 21.0
[    29.560] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    29.560] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.560] (**) Option "Device" "/dev/input/event4"
[    29.592] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 93)
[    29.592] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 125)
[    29.592] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    29.592] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    29.592] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    29.593] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    29.593] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.593] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.644] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    29.644] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    29.644] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    29.644] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    29.645] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    29.645] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    29.645] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    29.645] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    29.645] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    29.646] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.646] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    29.646] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    29.647] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[    29.647] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    29.647] (II) Using input driver 'evdev' for 'TPPS/2 IBM TrackPoint'
[    29.647] (**) TPPS/2 IBM TrackPoint: always reports core events
[    29.648] (**) evdev: TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
[    29.648] (--) evdev: TPPS/2 IBM TrackPoint: Vendor 0x2 Product 0xa
[    29.648] (--) evdev: TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    29.648] (--) evdev: TPPS/2 IBM TrackPoint: Found relative axes
[    29.648] (--) evdev: TPPS/2 IBM TrackPoint: Found x and y relative axes
[    29.648] (II) evdev: TPPS/2 IBM TrackPoint: Configuring as mouse
[    29.648] (**) evdev: TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    29.648] (**) evdev: TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.648] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/serio2/input/input6/event6"
[    29.648] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE, id 11)
[    29.648] (II) evdev: TPPS/2 IBM TrackPoint: initialized for relative axes.
[    29.649] (**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
[    29.649] (**) TPPS/2 IBM TrackPoint: (accel) acceleration profile 0
[    29.649] (**) TPPS/2 IBM TrackPoint: (accel) acceleration factor: 2.000
[    29.649] (**) TPPS/2 IBM TrackPoint: (accel) acceleration threshold: 4
[    29.650] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    29.650] (II) No input driver specified, ignoring this device.
[    29.650] (II) This device may have been added with another device file.
[    29.651] (II) config/udev: Adding input device PC Speaker (/dev/input/event8)
[    29.651] (II) No input driver specified, ignoring this device.
[    29.651] (II) This device may have been added with another device file.
[    29.652] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event7)
[    29.653] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    29.653] (II) Using input driver 'evdev' for 'ThinkPad Extra Buttons'
[    29.653] (**) ThinkPad Extra Buttons: always reports core events
[    29.653] (**) evdev: ThinkPad Extra Buttons: Device: "/dev/input/event7"
[    29.653] (--) evdev: ThinkPad Extra Buttons: Vendor 0x17aa Product 0x5054
[    29.653] (--) evdev: ThinkPad Extra Buttons: Found keys
[    29.653] (II) evdev: ThinkPad Extra Buttons: Configuring as keyboard
[    29.653] (**) Option "config_info" "udev:/sys/devices/platform/thinkpad_acpi/input/input8/event7"
[    29.653] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD, id 12)
[    29.653] (**) Option "xkb_rules" "evdev"
[    29.653] (**) Option "xkb_model" "pc105"
[    29.653] (**) Option "xkb_layout" "us"
[    39.672] (II) intel(0): EDID vendor "LEN", prod id 16464
[    39.672] (II) intel(0): Printing DDC gathered Modelines:
[    39.672] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    39.672] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[    46.695] (II) intel(0): EDID vendor "LEN", prod id 16464
[    46.696] (II) intel(0): Printing DDC gathered Modelines:
[    46.696] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    46.696] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[    59.920] (II) AIGLX: Suspending AIGLX clients for VT switch
[    62.116] (II) AIGLX: Resuming AIGLX clients after VT switch
[    62.693] (II) intel(0): EDID vendor "LEN", prod id 16464
[    62.693] (II) intel(0): Printing DDC gathered Modelines:
[    62.694] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    62.694] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[    62.746] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    74.383] (II) intel(0): EDID vendor "LEN", prod id 16464
[    74.383] (II) intel(0): Printing DDC gathered Modelines:
[    74.383] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    74.383] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[    76.339] (II) intel(0): EDID vendor "LEN", prod id 16464
[    76.339] (II) intel(0): Printing DDC gathered Modelines:
[    76.339] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[    76.339] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[   100.707] (II) intel(0): EDID vendor "LEN", prod id 16464
[   100.707] (II) intel(0): Printing DDC gathered Modelines:
[   100.707] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[   100.708] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[   225.599] (II) intel(0): EDID vendor "LEN", prod id 16464
[   225.599] (II) intel(0): Printing DDC gathered Modelines:
[   225.599] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[   225.599] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1353.476] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1353.476] (II) intel(0): Printing DDC gathered Modelines:
[  1353.476] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1353.477] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.028] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.028] (II) intel(0): Printing DDC gathered Modelines:
[  1470.028] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.028] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.073] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.073] (II) intel(0): Printing DDC gathered Modelines:
[  1470.073] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.074] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.106] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.106] (II) intel(0): Printing DDC gathered Modelines:
[  1470.106] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.106] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.154] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.154] (II) intel(0): Printing DDC gathered Modelines:
[  1470.154] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.154] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.202] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.202] (II) intel(0): Printing DDC gathered Modelines:
[  1470.202] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.202] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.300] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.301] (II) intel(0): Printing DDC gathered Modelines:
[  1470.301] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.301] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.338] (II) intel(0): Allocated new frame buffer 2304x800 stride 9216, tiled
[  1470.520] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.520] (II) intel(0): Printing DDC gathered Modelines:
[  1470.520] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.520] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)
[  1470.603] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[  1470.720] (II) intel(0): EDID vendor "LEN", prod id 16464
[  1470.720] (II) intel(0): Printing DDC gathered Modelines:
[  1470.720] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz eP)
[  1470.720] (II) intel(0): Modeline "1280x800"x0.0   59.26  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (41.2 kHz e)

```


Everything just seems larger than from the windows install I wiped off of here :P Plus the contrast from my other T61.... Thanks for your help in figuring out either way.

---

