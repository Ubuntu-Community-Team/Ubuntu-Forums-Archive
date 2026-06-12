---
title: "X crashes"
date: 2011-06-08
forum: Desktop Environments
---

### Post by dkarnows on 2011-06-08
Since upgrading to 11.04 I've been experiencing fairly regular X-Server crashes. It has always occurred while playing flash video in my browser. I'll watch videos and then after about perhaps 20 minutes of watching the X Server will segmentation fault, then restart.

I did not experience this when I was Ubuntu 10.10.

Looking for pointers.

I don't have a /etc/X11/xorg.conf (did it move or go away with Ubuntu 11.04?).

It's Samsung netbook with a Intel Atom CPU N270. Here's the display section of the "lshw" output:
```

        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f007ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:f0300000-f033ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0080000-f00fffff

```


An entire X.org.log (with the segmentation fault near the bottom):
```

[    30.821] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    30.821] X Protocol Version 11, Revision 0
[    30.821] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    30.821] Current Operating System: Linux freedom 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    30.821] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=0c450c3e-f321-46ea-ba17-c3140cfbf9bc ro quiet splash vt.handoff=7
[    30.822] Build Date: 19 April 2011  03:33:17PM
[    30.822] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    30.822] Current version of pixman: 0.20.2
[    30.822] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    30.822] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.822] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  8 21:05:00 2011
[    30.849] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.850] (==) No Layout section.  Using the first Screen section.
[    30.850] (==) No screen section available. Using defaults.
[    30.850] (**) |-->Screen "Default Screen Section" (0)
[    30.851] (**) |   |-->Monitor "<default monitor>"
[    30.851] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    30.852] (==) Automatically adding devices
[    30.852] (==) Automatically enabling devices
[    30.852] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.852] 	Entry deleted from font path.
[    30.853] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    30.853] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.853] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.853] (II) Loader magic: 0x81ffde0
[    30.853] (II) Module ABI versions:
[    30.853] 	X.Org ANSI C Emulation: 0.4
[    30.853] 	X.Org Video Driver: 10.0
[    30.853] 	X.Org XInput driver : 12.3
[    30.853] 	X.Org Server Extension : 5.0
[    30.856] (--) PCI:*(0:0:2:0) 8086:27ae:144d:c052 rev 3, Mem @ 0xf0000000/524288, 0xd0000000/268435456, 0xf0300000/262144, I/O @ 0x00001800/8
[    30.856] (--) PCI: (0:0:2:1) 8086:27a6:144d:c052 rev 3, Mem @ 0xf0080000/524288
[    30.857] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.857] (II) LoadModule: "extmod"
[    30.868] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.869] (II) Module extmod: vendor="X.Org Foundation"
[    30.869] 	compiled for 1.10.1, module version = 1.0.0
[    30.869] 	Module class: X.Org Server Extension
[    30.869] 	ABI class: X.Org Server Extension, version 5.0
[    30.869] (II) Loading extension MIT-SCREEN-SAVER
[    30.869] (II) Loading extension XFree86-VidModeExtension
[    30.869] (II) Loading extension XFree86-DGA
[    30.869] (II) Loading extension DPMS
[    30.870] (II) Loading extension XVideo
[    30.870] (II) Loading extension XVideo-MotionCompensation
[    30.870] (II) Loading extension X-Resource
[    30.870] (II) LoadModule: "dbe"
[    30.871] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.871] (II) Module dbe: vendor="X.Org Foundation"
[    30.871] 	compiled for 1.10.1, module version = 1.0.0
[    30.871] 	Module class: X.Org Server Extension
[    30.871] 	ABI class: X.Org Server Extension, version 5.0
[    30.871] (II) Loading extension DOUBLE-BUFFER
[    30.872] (II) LoadModule: "glx"
[    30.873] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.873] (II) Module glx: vendor="X.Org Foundation"
[    30.873] 	compiled for 1.10.1, module version = 1.0.0
[    30.873] 	ABI class: X.Org Server Extension, version 5.0
[    30.874] (==) AIGLX enabled
[    30.874] (II) Loading extension GLX
[    30.874] (II) LoadModule: "record"
[    30.875] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.875] (II) Module record: vendor="X.Org Foundation"
[    30.875] 	compiled for 1.10.1, module version = 1.13.0
[    30.875] 	Module class: X.Org Server Extension
[    30.875] 	ABI class: X.Org Server Extension, version 5.0
[    30.876] (II) Loading extension RECORD
[    30.876] (II) LoadModule: "dri"
[    30.877] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.877] (II) Module dri: vendor="X.Org Foundation"
[    30.878] 	compiled for 1.10.1, module version = 1.0.0
[    30.878] 	ABI class: X.Org Server Extension, version 5.0
[    30.878] (II) Loading extension XFree86-DRI
[    30.878] (II) LoadModule: "dri2"
[    30.879] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.879] (II) Module dri2: vendor="X.Org Foundation"
[    30.879] 	compiled for 1.10.1, module version = 1.2.0
[    30.879] 	ABI class: X.Org Server Extension, version 5.0
[    30.879] (II) Loading extension DRI2
[    30.880] (==) Matched intel as autoconfigured driver 0
[    30.880] (==) Matched vesa as autoconfigured driver 1
[    30.880] (==) Matched fbdev as autoconfigured driver 2
[    30.880] (==) Assigned the driver to the xf86ConfigLayout
[    30.880] (II) LoadModule: "intel"
[    30.881] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    30.882] (II) Module intel: vendor="X.Org Foundation"
[    30.882] 	compiled for 1.10.0.902, module version = 2.14.0
[    30.882] 	Module class: X.Org Video Driver
[    30.882] 	ABI class: X.Org Video Driver, version 10.0
[    30.882] (II) LoadModule: "vesa"
[    30.883] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.883] (II) Module vesa: vendor="X.Org Foundation"
[    30.883] 	compiled for 1.10.0, module version = 2.3.0
[    30.884] 	Module class: X.Org Video Driver
[    30.884] 	ABI class: X.Org Video Driver, version 10.0
[    30.884] (II) LoadModule: "fbdev"
[    30.885] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.885] (II) Module fbdev: vendor="X.Org Foundation"
[    30.885] 	compiled for 1.10.0, module version = 0.4.2
[    30.885] 	ABI class: X.Org Video Driver, version 10.0
[    30.885] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    30.889] (II) VESA: driver for VESA chipsets: vesa
[    30.889] (II) FBDEV: driver for framebuffer: fbdev
[    30.889] (++) using VT number 7

[    30.896] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    30.896] (WW) Falling back to old probe method for vesa
[    30.897] (WW) Falling back to old probe method for fbdev
[    30.897] (II) Loading sub module "fbdevhw"
[    30.897] (II) LoadModule: "fbdevhw"
[    30.928] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.929] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.929] 	compiled for 1.10.1, module version = 0.0.2
[    30.929] 	ABI class: X.Org Video Driver, version 10.0
[    30.930] drmOpenDevice: node name is /dev/dri/card0
[    30.930] drmOpenDevice: open result is 9, (OK)
[    30.930] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    30.930] drmOpenDevice: node name is /dev/dri/card0
[    30.930] drmOpenDevice: open result is 9, (OK)
[    30.930] drmOpenByBusid: drmOpenMinor returns 9
[    30.930] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    30.930] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    30.930] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    30.930] (==) intel(0): RGB weight 888
[    30.930] (==) intel(0): Default visual is TrueColor
[    30.931] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
[    30.931] (--) intel(0): Chipset: "945GME"
[    30.931] (**) intel(0): Tiling enabled
[    30.931] (**) intel(0): SwapBuffers wait enabled
[    30.931] (==) intel(0): video overlay key set to 0x101fe
[    30.931] (II) intel(0): Output LVDS1 has no monitor section
[    30.964] (II) intel(0): Output VGA1 has no monitor section
[    30.964] (II) intel(0): EDID for output LVDS1
[    30.964] (II) intel(0): Manufacturer: SEC  Model: 3052  Serial#: 0
[    30.964] (II) intel(0): Year: 2009  Week: 0
[    30.964] (II) intel(0): EDID Version: 1.0
[    30.964] (II) intel(0): Digital Display Input
[    30.964] (II) intel(0): Max Image Size [cm]: horiz.: 22  vert.: 13
[    30.964] (II) intel(0): Gamma: 2.20
[    30.965] (II) intel(0): No DPMS capabilities specified
[    30.965] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.965] (II) intel(0): First detailed timing is preferred mode
[    30.965] (II) intel(0): redX: 0.600 redY: 0.340   greenX: 0.310 greenY: 0.560
[    30.965] (II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
[    30.965] (II) intel(0): Manufacturer's mask: 0
[    30.965] (II) intel(0): Supported detailed timing:
[    30.965] (II) intel(0): clock: 63.2 MHz   Image Size:  223 x 125 mm
[    30.965] (II) intel(0): h_active: 1024  h_sync: 1040  h_sync_end 1088 h_blank_end 1564 h_border: 0
[    30.965] (II) intel(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 673 v_border: 0
[    30.965] (II) intel(0): EDID (in hex):
[    30.965] (II) intel(0): 	00ffffffffffff004ca3523000000000
[    30.966] (II) intel(0): 	0013010080160d780a859599574f8f26
[    30.966] (II) intel(0): 	21505400000001010101010101010101
[    30.966] (II) intel(0): 	010101010101b018001c425849201030
[    30.966] (II) intel(0): 	1300df7d000000190000000f00000000
[    30.966] (II) intel(0): 	00000000002387026400000000fe0053
[    30.966] (II) intel(0): 	414d53554e470a2020202020000000fe
[    30.966] (II) intel(0): 	004c544e3130314e54303130303000d4
[    30.966] (II) intel(0): EDID vendor "SEC", prod id 12370
[    30.966] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    30.966] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    30.966] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    30.966] (II) intel(0): Printing DDC gathered Modelines:
[    30.966] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    30.967] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    30.967] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    30.967] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    30.968] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    30.969] (II) intel(0): Printing probed modes for output LVDS1
[    30.969] (II) intel(0): Modeline "1024x600"x60.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    30.969] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    30.969] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    30.969] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    31.004] (II) intel(0): EDID for output VGA1
[    31.004] (II) intel(0): Output LVDS1 connected
[    31.004] (II) intel(0): Output VGA1 disconnected
[    31.004] (II) intel(0): Using exact sizes for initial modes
[    31.004] (II) intel(0): Output LVDS1 using initial mode 1024x600
[    31.004] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    31.006] (II) intel(0): Kernel page flipping support detected, enabling
[    31.006] (**) intel(0): Display dimensions: (220, 130) mm
[    31.006] (**) intel(0): DPI set to (118, 117)
[    31.006] (II) Loading sub module "fb"
[    31.006] (II) LoadModule: "fb"
[    31.007] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.007] (II) Module fb: vendor="X.Org Foundation"
[    31.008] 	compiled for 1.10.1, module version = 1.0.0
[    31.008] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    31.008] (II) UnloadModule: "vesa"
[    31.008] (II) Unloading vesa
[    31.008] (II) UnloadModule: "fbdev"
[    31.008] (II) Unloading fbdev
[    31.008] (II) UnloadModule: "fbdevhw"
[    31.008] (II) Unloading fbdevhw
[    31.008] (==) Depth 24 pixmap format is 32 bpp
[    31.008] (==) intel(0): VideoRam: 262144 KB
[    31.008] (II) intel(0): [DRI2] Setup complete
[    31.008] (II) intel(0): [DRI2]   DRI driver: i915
[    31.008] (II) intel(0): Allocated new frame buffer 1024x600 stride 4096, tiled
[    31.009] (II) UXA(0): Driver registered support for the following operations:
[    31.009] (II)         solid
[    31.009] (II)         copy
[    31.009] (II)         composite (RENDER acceleration)
[    31.009] (II)         put_image
[    31.009] (II)         get_image
[    31.009] (==) intel(0): Backing store disabled
[    31.009] (==) intel(0): Silken mouse enabled
[    31.009] (II) intel(0): Initializing HW Cursor
[    31.048] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    31.048] (==) intel(0): DPMS enabled
[    31.049] (==) intel(0): Intel XvMC decoder disabled
[    31.049] (II) intel(0): Set up textured video
[    31.049] (II) intel(0): Set up overlay video
[    31.049] (II) intel(0): direct rendering: DRI2 Enabled
[    31.049] (==) intel(0): hotplug detection: "enabled"
[    31.049] (--) RandR disabled
[    31.049] (II) Initializing built-in extension Generic Event Extension
[    31.049] (II) Initializing built-in extension SHAPE
[    31.050] (II) Initializing built-in extension MIT-SHM
[    31.050] (II) Initializing built-in extension XInputExtension
[    31.050] (II) Initializing built-in extension XTEST
[    31.050] (II) Initializing built-in extension BIG-REQUESTS
[    31.050] (II) Initializing built-in extension SYNC
[    31.050] (II) Initializing built-in extension XKEYBOARD
[    31.050] (II) Initializing built-in extension XC-MISC
[    31.050] (II) Initializing built-in extension SECURITY
[    31.050] (II) Initializing built-in extension XINERAMA
[    31.050] (II) Initializing built-in extension XFIXES
[    31.050] (II) Initializing built-in extension RENDER
[    31.050] (II) Initializing built-in extension RANDR
[    31.050] (II) Initializing built-in extension COMPOSITE
[    31.050] (II) Initializing built-in extension DAMAGE
[    31.050] (II) Initializing built-in extension GESTURE
[    31.093] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    31.118] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    31.118] (II) AIGLX: enabled GLX_INTEL_swap_event
[    31.118] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    31.119] (II) AIGLX: enabled GLX_SGI_make_current_read
[    31.119] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    31.119] (II) AIGLX: Loaded and initialized i915
[    31.119] (II) GLX: Initialized DRI2 GL provider for screen 0
[    31.122] (II) intel(0): Setting screen physical size to 270 x 158
[    31.213] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.264] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    31.264] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.265] (II) LoadModule: "evdev"
[    31.266] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.268] (II) Module evdev: vendor="X.Org Foundation"
[    31.268] 	compiled for 1.10.0.902, module version = 2.6.0
[    31.268] 	Module class: X.Org XInput Driver
[    31.268] 	ABI class: X.Org XInput driver, version 12.3
[    31.268] (II) Using input driver 'evdev' for 'Power Button'
[    31.268] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.269] (**) Power Button: always reports core events
[    31.269] (**) Power Button: Device: "/dev/input/event3"
[    31.284] (--) Power Button: Found keys
[    31.284] (II) Power Button: Configuring as keyboard
[    31.284] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    31.284] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    31.284] (**) Option "xkb_rules" "evdev"
[    31.285] (**) Option "xkb_model" "pc105"
[    31.285] (**) Option "xkb_layout" "us"
[    31.290] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    31.290] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    31.290] (II) Using input driver 'evdev' for 'Video Bus'
[    31.290] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.290] (**) Video Bus: always reports core events
[    31.291] (**) Video Bus: Device: "/dev/input/event5"
[    31.304] (--) Video Bus: Found keys
[    31.304] (II) Video Bus: Configuring as keyboard
[    31.304] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    31.304] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    31.304] (**) Option "xkb_rules" "evdev"
[    31.304] (**) Option "xkb_model" "pc105"
[    31.304] (**) Option "xkb_layout" "us"
[    31.321] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.321] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.321] (II) Using input driver 'evdev' for 'Power Button'
[    31.321] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.322] (**) Power Button: always reports core events
[    31.322] (**) Power Button: Device: "/dev/input/event1"
[    31.336] (--) Power Button: Found keys
[    31.336] (II) Power Button: Configuring as keyboard
[    31.336] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    31.336] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    31.336] (**) Option "xkb_rules" "evdev"
[    31.336] (**) Option "xkb_model" "pc105"
[    31.336] (**) Option "xkb_layout" "us"
[    31.339] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    31.339] (II) No input driver/identifier specified (ignoring)
[    31.340] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    31.341] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    31.341] (II) Using input driver 'evdev' for 'Sleep Button'
[    31.341] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.341] (**) Sleep Button: always reports core events
[    31.341] (**) Sleep Button: Device: "/dev/input/event2"
[    31.364] (--) Sleep Button: Found keys
[    31.364] (II) Sleep Button: Configuring as keyboard
[    31.364] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    31.364] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    31.364] (**) Option "xkb_rules" "evdev"
[    31.364] (**) Option "xkb_model" "pc105"
[    31.364] (**) Option "xkb_layout" "us"
[    31.371] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[    31.371] (II) No input driver/identifier specified (ignoring)
[    31.373] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[    31.373] (II) No input driver/identifier specified (ignoring)
[    31.387] (II) config/udev: Adding input device Namuga 1.3M Webcam (/dev/input/event7)
[    31.387] (**) Namuga 1.3M Webcam: Applying InputClass "evdev keyboard catchall"
[    31.387] (II) Using input driver 'evdev' for 'Namuga 1.3M Webcam'
[    31.387] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.388] (**) Namuga 1.3M Webcam: always reports core events
[    31.388] (**) Namuga 1.3M Webcam: Device: "/dev/input/event7"
[    31.416] (--) Namuga 1.3M Webcam: Found keys
[    31.416] (II) Namuga 1.3M Webcam: Configuring as keyboard
[    31.416] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input7/event7"
[    31.416] (II) XINPUT: Adding extended input device "Namuga 1.3M Webcam" (type: KEYBOARD)
[    31.416] (**) Option "xkb_rules" "evdev"
[    31.416] (**) Option "xkb_model" "pc105"
[    31.416] (**) Option "xkb_layout" "us"
[    31.440] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    31.440] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.440] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.440] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.440] (**) AT Translated Set 2 keyboard: always reports core events
[    31.440] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    31.460] (--) AT Translated Set 2 keyboard: Found keys
[    31.460] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    31.460] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    31.460] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    31.460] (**) Option "xkb_rules" "evdev"
[    31.460] (**) Option "xkb_model" "pc105"
[    31.460] (**) Option "xkb_layout" "us"
[    31.463] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    31.464] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    31.464] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    31.464] (II) LoadModule: "synaptics"
[    31.466] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    31.466] (II) Module synaptics: vendor="X.Org Foundation"
[    31.466] 	compiled for 1.10.0.902, module version = 1.3.99
[    31.466] 	Module class: X.Org XInput Driver
[    31.466] 	ABI class: X.Org XInput driver, version 12.3
[    31.466] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    31.466] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    31.466] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.467] (**) Option "Device" "/dev/input/event6"
[    31.552] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5806
[    31.552] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4906
[    31.552] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    31.552] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    31.552] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    31.616] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    31.616] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.648] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    31.648] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    31.648] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    31.648] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    31.648] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.036
[    31.649] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    31.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    31.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    31.649] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    31.698] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    31.699] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    31.700] (II) No input driver/identifier specified (ignoring)
[    34.469] (II) intel(0): EDID vendor "SEC", prod id 12370
[    34.469] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    34.469] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    34.470] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    34.470] (II) intel(0): Printing DDC gathered Modelines:
[    34.470] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    34.504] (II) intel(0): EDID vendor "SEC", prod id 12370
[    34.504] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    34.504] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    34.505] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    34.505] (II) intel(0): Printing DDC gathered Modelines:
[    34.505] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    34.540] (II) intel(0): EDID vendor "SEC", prod id 12370
[    34.540] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    34.540] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    34.540] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    34.540] (II) intel(0): Printing DDC gathered Modelines:
[    34.540] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    34.574] (II) intel(0): EDID vendor "SEC", prod id 12370
[    34.575] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    34.575] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    34.575] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    34.575] (II) intel(0): Printing DDC gathered Modelines:
[    34.575] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    36.614] (II) intel(0): EDID vendor "SEC", prod id 12370
[    36.614] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    36.614] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    36.614] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    36.615] (II) intel(0): Printing DDC gathered Modelines:
[    36.615] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    52.355] (II) intel(0): EDID vendor "SEC", prod id 12370
[    52.355] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    52.355] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    52.355] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    52.356] (II) intel(0): Printing DDC gathered Modelines:
[    52.356] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    52.392] (II) intel(0): EDID vendor "SEC", prod id 12370
[    52.392] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    52.393] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    52.393] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    52.393] (II) intel(0): Printing DDC gathered Modelines:
[    52.393] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    52.427] (II) intel(0): EDID vendor "SEC", prod id 12370
[    52.427] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    52.427] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    52.427] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    52.427] (II) intel(0): Printing DDC gathered Modelines:
[    52.427] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    53.294] (II) intel(0): EDID vendor "SEC", prod id 12370
[    53.294] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    53.294] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    53.294] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    53.294] (II) intel(0): Printing DDC gathered Modelines:
[    53.294] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    55.945] (II) intel(0): EDID vendor "SEC", prod id 12370
[    55.946] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    55.946] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    55.946] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    55.946] (II) intel(0): Printing DDC gathered Modelines:
[    55.946] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    57.138] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 1991 < target_msc 1992
[    58.291] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 2063 < target_msc 2064
[    59.509] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 2139 < target_msc 2140
[    59.696] (II) intel(0): EDID vendor "SEC", prod id 12370
[    59.696] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    59.696] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    59.696] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    59.696] (II) intel(0): Printing DDC gathered Modelines:
[    59.696] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[    59.877] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 2162 < target_msc 2163
[    79.934] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 3414 < target_msc 3415
[   759.490] (II) intel(0): EDID vendor "SEC", prod id 12370
[   759.490] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[   759.490] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[   759.490] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[   759.490] (II) intel(0): Printing DDC gathered Modelines:
[   759.490] (II) intel(0): Modeline "1024x600"x0.0   63.20  1024 1040 1088 1564  600 601 604 673 -hsync -vsync (40.4 kHz)
[  1365.372] 
Backtrace:
[  1365.397] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[  1365.398] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[  1365.398] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x40240c]
[  1365.398] 3: /usr/bin/X (_CallCallbacks+0x3e) [0x8074e1e]
[  1365.398] 4: /usr/bin/X (WriteToClient+0x267) [0x80a7607]
[  1365.398] 5: /usr/lib/xorg/modules/extensions/libdri2.so (ProcDRI2WaitMSCReply+0x62) [0x2d7bf2]
[  1365.398] 6: /usr/lib/xorg/modules/extensions/libdri2.so (DRI2WaitMSCComplete+0x75) [0x2d5fc5]
[  1365.398] 7: /usr/lib/xorg/modules/drivers/intel_drv.so (0xbaa000+0x2261c) [0xbcc61c]
[  1365.398] 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0xbaa000+0x87c2) [0xbb27c2]
[  1365.398] 9: /lib/i386-linux-gnu/libdrm.so.2 (drmHandleEvent+0xf5) [0x2d1665]
[  1365.398] 10: /usr/lib/xorg/modules/drivers/intel_drv.so (0xbaa000+0x7927) [0xbb1927]
[  1365.398] 11: /usr/bin/X (WakeupHandler+0x52) [0x8074602]
[  1365.399] 12: /usr/bin/X (WaitForSomething+0x1ba) [0x80a1f3a]
[  1365.399] 13: /usr/bin/X (0x8048000+0x27f1e) [0x806ff1e]
[  1365.399] 14: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[  1365.399] 15: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x126e37]
[  1365.399] 16: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[  1365.399] Segmentation fault at address 0x9000668
[  1365.399] 
Caught signal 11 (Segmentation fault). Server aborting
[  1365.399] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  1365.399] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1365.399] 
[  1365.524] (II) Power Button: Close
[  1365.528] (II) UnloadModule: "evdev"
[  1365.528] (II) Unloading evdev
[  1365.561] (II) Video Bus: Close
[  1365.561] (II) UnloadModule: "evdev"
[  1365.561] (II) Unloading evdev
[  1365.608] (II) Power Button: Close
[  1365.609] (II) UnloadModule: "evdev"
[  1365.609] (II) Unloading evdev
[  1365.619] (II) Sleep Button: Close
[  1365.619] (II) UnloadModule: "evdev"
[  1365.619] (II) Unloading evdev
[  1365.620] (II) Namuga 1.3M Webcam: Close
[  1365.621] (II) UnloadModule: "evdev"
[  1365.621] (II) Unloading evdev
[  1365.623] (II) AT Translated Set 2 keyboard: Close
[  1365.623] (II) UnloadModule: "evdev"
[  1365.624] (II) Unloading evdev
[  1365.637] (II) UnloadModule: "synaptics"
[  1365.637] (II) Unloading synaptics
[  1365.683] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1365.747]  ddxSigGiveUp: Closing log

```

---

