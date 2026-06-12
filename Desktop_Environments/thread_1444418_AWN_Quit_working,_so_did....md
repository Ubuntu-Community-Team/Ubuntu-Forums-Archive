---
title: "AWN Quit working, so did..."
date: 2010-04-01
forum: Desktop Environments
---

### Post by mike marfise on 2010-04-01
Let's see.  Last night, all was well with my computer.
This morning, I get a "Screen is not composited" error at the gui, AWN won't load, I can't TAB between open windows,
Also am now suddenly getting a "Desktop effects could not be enabled" error if I try to turn them on (which is odd because I have never turned them off)
As I said, yesterday, and for as long as I've had this lappy, everything worked perfectly, and I didn't change anything on it yesterday, just powered it down as normal and let it lay, same as always.
This is very frustrating.

I found "compiz-check" in the sticky at this site, compiz-check says
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

glxinfo returns
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

xorg.conf says
(This is the entire file minus the comments at the very beginning)
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
And it has a time/date stamp of 23OCT2009.


The Log File Viewer opens with this message:
Could Not Open The Following Files:
/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/btmp: You don't have enough permissions to read the file.
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory


The computer is a Dell Inspiron B120
2GB Ram
The aforementioned I915 Graphics chip (Intel 915GM/GMS/910GML Express Graphics Controller)
Intel Celron M 1.4GHz
Ubuntu 9.10 
Gnome 2.28.1
Kernel 2.6.31-20

A few snippets from Xorg.log (I'll post the entire file if I need to)
(--) PCI:*(0:0:2:0) 8086:2592:1028:01c9 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 3, Mem @ 0xdff00000/524288, 0xc0000000/268435456, 0xdfec0000/262144, I/O @ 0x0000eff8/8
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)

(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) GLX error: Can not get required symbols.
(II) intel(0): Setting screen physical size to 304 x 190

---

### Post by mike marfise on 2010-04-01
hmmmm... just saw this in my xorg.log:

(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0

Why is X loading an ATI module for an intel chip?

Here's the entire log:
(And is there something else I should post to aid in troubleshooting this?)

X.Org X Server 1.6.5
Release Date: 2009-10-11
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-xen i686 Ubuntu
Current Operating System: Linux greg-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: root=UUID=e6974a23-8516-4ad1-a972-a78ffd2d519d ro quiet splash 
Build Date: 07 November 2009  04:37:35PM
xorg-server 2:1.6.5+git20091107+server-1.6-branch.2dbcb06a-0ubuntu0sarvatt~karmic (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr  1 09:54:54 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2592:1028:01c9 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 3, Mem @ 0xdff00000/524288, 0xc0000000/268435456, 0xdfec0000/262144, I/O @ 0x0000eff8/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 2.11.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) intel(0): Chipset: "915GM"
(==) intel(0): video overlay key set to 0x101fe
(II) intel(0): Output VGA1 using monitor section Configured Monitor
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output TV1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x800
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(II)         put_image
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) GLX error: Can not get required symbols.
(II) intel(0): Setting screen physical size to 304 x 190
(II) config/hal: Adding input device Video Bus
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.5, module version = 2.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4.901, module version = 1.2.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.2.0
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: QDS  Model: 30  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.579 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.154 blueY: 0.153   whiteX: 0.314 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.0 MHz   Image Size:  304 x 190 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  KD145

(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004493300000000000
(II) intel(0): 	000f0103801e13780a479994574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	260030be100000180000000f0008002a
(II) intel(0): 	0001000400324a041400000000fe004b
(II) intel(0): 	443134350000000000000000000000fe
(II) intel(0): 	00f0dbcdc3a07f573001010a2020000b
(II) intel(0): EDID vendor "QDS", prod id 48
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1

---

### Post by Derek3x on 2010-04-01
Have you tried just purging the install of compiz, then reinstalling it?

---

### Post by mike marfise on 2010-04-01
> Have you tried just purging the install of compiz, then reinstalling it?
I have NOT tried that, simply because all the sudden appearance of the 'glxinfo' errors, the "desktop effects could not be enabled' message, the errors in the log file viewer, and the 'Error: No rendering method in use' from compiz-check.
This all leads me to believe something else is at fault, but I don't know just what that could be just overnight.
However, I am willing to try just about anything at all right now, not being able to tab through my windows is pretty frustrating!

---

### Post by mike marfise on 2010-04-01
...and, just so nobody could accuse me of NOT taking suggestions...
I did a full wipe of anything containing 'compiz' from the synaptic package manager, rebooted, reinstalled the same, rebooted just to be sure...
No change whatsoever.
Desktop effects could not be enabled,
glxinfo still bombs,
awn still kvetches about 'screen is not composited'.
i haven't tried anything else on my machine since this started happening this morning; 
a quick check reveals...
almost none of my screensavers work today,
glxgears fails to start with the same errors as glxinfo
celestia does not go past the splash screen, neither will google earth
vega strike won't start at all, for that matter neither will the setup program!
everything in open office appears to be ok,
the sound is... well, it's unchanged (always been buggy though, but that's been the same on every ubuntu i've installed)
vlc seems quite content with a few videos i tried,
most games won't play at all, neither will a few graphic-intense programs in wine (roller coaster tycoon - the first one - won't even start up at all, autocad hangs at the splash screen)

ummm... this appears to be more than just a minor inconvenience.
Any help with troubleshooting this would be very much so appreciated.

---

### Post by GepettoBR on 2010-04-01
I have two suggestions: first, try running without you xorg.conf file (just rename it to something else). If that fails, put the file back in place but add a line to your device section: ```
Section "Device"
Identifier "Configured Video Device"
**Driver "<DRIVERNAMEHERE">**
EndSection
```

Replace <DRIVERNAMEHERE> with the module name for the video driver you're using. remember to leave the quotation marks around it, as they're necessary.

You'll need to restart X in both cases for the change to take effect.

If you're not sure what your video driver is, lsmod can give you a clue.

---

### Post by mike marfise on 2010-04-01
I will try that in a second, after I post this...
I have been hesitant to make any changes to xorg simply because it is the same time and date stamp that it has been for the past 5 months and I hate to begin mucking around with it (old wounds from the past several years have left me gun shy about opening the can of worms that is xorg!)
But as I did not realize how hosed this machine is until just now, I will try anything!
Back in a few...

---

### Post by mike marfise on 2010-04-01
wow.
OK... no xorg.conf at all made no difference whatsoever.
adding Driver "i810", "i915", "intel"
no, no, and no.
In fact, hosed the display to the point that it was completely unusable; short of going in and adding refresh and v/hsync info.
And since I have not had to ever mess with xorg.conf on tis machine through 2 upgrades, then I really don't like the thought that something happened in 5-6 hours of being powered off that suddenly requires going back to the head-pound-against-desk marathon that editing xorg.conf tends to bring about.   (fresh install of intrepid, replaced HDD with intrepid and upgraded to jaunty, then to Karmic if my memory serves.)
In all seriousness, just going through the exercise of trying out a few different Driver "blah blah" edits was enough to make me want to go back to XP rather than start that chaotic mess again.

But enough venting.

No, specifying the driver in xorg.conf did not work, nor did simply deleting xorg.conf.

---

### Post by GepettoBR on 2010-04-01
what's odd about your problem is that it seems to have come out of nowhere. Are you sure the computer didn't suffer any damage?

---

### Post by mike marfise on 2010-04-01
well, no damage sitting on the desk by the bed overnight; it sits there every night. And all was well last night... i sent a few emails, watched an "epic beard man" video, and worked on a sudoku for a little while, then shut it down.
awn has complained about "screen not composited" before, but that's always been at shutdown, and appears to be a known bug... something about compiz shutting down before awn does.  It's mentioned in the forums somewhere, but never really went anywhere since it is an issue at shutdown when it's exiting anyway.

fsck shows no issues with the hdd, and the graphics all appear to be good to go with the exception of glx... 
iirc, the intel driver is open source and fresh from the ubuntu disk; i don't know why it would suddenly be bad...

I am still a little puzzled about the "Module glx: vendor="FireGL - ATI Technologies Inc. compiled for 7.4.0, module version = 1.0.0" in the output from the xorg log... is there an ati module driving the glx system?

---

### Post by GepettoBR on 2010-04-01
It is odd. I'm sorry but I have no idea how to help. =/ Good luck fixing the issue.

---

### Post by mike marfise on 2010-04-03
OK, I am officially done.
I tried rebooting into recovery mode, and I ran dpkg from that prompt... it took it nearly 20 minutes to download and reinstall python, or at least nearly 140 Meg of python files...
Rebooted, and now I get
"Mount of filesystem failed", and it dumps me into a maintenance shell.
fsck simply hangs after displaying "Pass 1: checking inodes, blocks, and sizes", even after using the verbose switch...  (at least I assume that after 45 minutes and a blank screen that it is hung)
I have no problems reported on the hdd with several utilities on the "ultimate boot cd" doing numerous tests checks and scans on all 3 partitions.

Now I am at an end.
All of my personal stuff is on this machine; pictures, budget, taxes, my girls' homework and some personal memories...
I know... waah waah waah... why didn't I back it up if it was so important...
Thie sickening part is that I regularly backed up all of my important stuff onto a 4gb thumb drive; I copied the drive onto the computer this morning so I could make room for a fresh install image of 9.10... but now I can't even get onto it to copy the image I downloaded.  All I'm left with is this crummy netbook pos to post my trials and tribulations with ubuntu.

I know I am venting, but for crying out loud... all of this from what appears to be a simple graphics driver issue, I can't help but notice that mucking around in xorg.conf is still an ordeal that will leave any sane person wondering why the #&*^#(&^$% anyone would think a casual user would want to ever have to spend so much time just trying to get a computer working when nothing appears to be physically wrong with it! it has turned into a freaking 3-ring circus that has left me with essentially a worthless installation of an operating system.

If anyone has any input on how to recover anything whatsoever from this thing, then I would like to know soon.  I can't afford to be without a working machine for this upcoming week, and it looks as though I need to just completely reinstall a new operating system...  if linux isn't up to the challange of normal day-to-day use, then I may just shell out the money for microsoft... i hate to put it that way, but this is simply ridiculous that it has fallen flat on its face so completely.

---

### Post by lidex on 2010-04-04
At least a re-install...but could be hardware related. Use a LiveCD (boot into live session) to copy data from your HDD.

---

### Post by mike marfise on 2010-04-05
OK... Live CD of 9.10 boots and functions just fine, most notably the glx components...

So... how do I get the video setup from the live cd copied over to the computer without doing a full wipe and reinstall?

---

### Post by lidex on 2010-04-06
> Rebooted, and now I get
"Mount of filesystem failed", and it dumps me into a maintenance shell.

That's not a graphics issue. Are you getting a grub prompt?

---

### Post by mike marfise on 2010-04-08
> "I tried rebooting into recovery mode"I did that from the Grub prompt.

Not really an issue at this point though; I went ahead and did a fresh install of XP and all appears to be doing just fine.

I'll check out linux again when it is a little more... "complete."  It really had always felt to me like a 'work in progress' anyway. /rant

Thanks for all the assistance though.

---

### Post by Squideshi on 2010-05-02
> **mike marfise said:**
> 
/var/log/btmp: You don't have enough permissions to read the file.


[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---

