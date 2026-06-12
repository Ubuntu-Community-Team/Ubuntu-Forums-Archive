---
title: "Asus EEE B202 Black Screen"
date: 2009-05-06
forum: General Help
---

### Post by campbecf on 2009-05-06
Hi all, having a bit of trouble with an Asus EEE Box B202. Seems that the screen is going completely black sometimes.

I previously had a video issue in 8.10 (whatever the last version was) but I was able to fix that by disabling the desktop effects.

Im using 9.04 now and I have disabled the desktop effects but I get the black screen issue, anyone have ideas on how to fix this?

I'll try to post the xorg log when I get access to the computer again.

---

### Post by wisd0m on 2009-08-12
I have a similar issue.

I have Ubuntu Netbook Remix 9.04 installed on my EEE Box 202. After a period of time the display will go blank. I know the machine is still on and it responds to keystrokes (If I press the power button and then <down> and then <enter> the power will shut off). To get the display back I have to restart the machine.

This happens at random intervals. Some times within 5min of usage, sometime after 30min.

Any help would be appreciated.

---

### Post by 09lefthand on 2009-10-26
Same problem, Asus EEE 1000H. I just switched to ubuntu after win xp blue screen of death, now I have this blank screen of death. Could it be the result of the latest update ? 

lscpi
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

```

lsusb 
```
Bus 005 Device 005: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 062a:0003 Creative Labs 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

/var/log/Xorg.0.log
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux siah1000h 2.6.28-12-netbook-eeepc #43 SMP Mon Apr 27 16:06:05 MDT 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 26 13:02:05 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) Option "BlankTime" "0"
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

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7f00000/524288, 0xd0000000/268435456, 0xf7ec0000/262144, I/O @ 0x0000dc00/8
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
	compiled for 1.6.0, module version = 1.0.0
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.9.0
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
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xF7F00000 size 524288
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(II) intel(0): No SDVO device is found in VBT
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): found backlight control method /sys/class/backlight/eeepc
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1024x600
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000202 to 0x80000242
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS LBLC_EVENT_STATUS VBLANK_INT_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): Kernel reported 489216 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1956860 kB available
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(WW) intel(0): drmSetMaster failed: 2.6.29 or newer kernel required for multi-server DRI
(II) intel(0): adjusting plane->pipe mappings to allow for framebuffer compression
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x005fffff: compressed frame buffer (6144 kB, 0x000000007f800000 physical
)
(II) intel(0): 0x00600000-0x00600fff: compressed ll buffer (4 kB, 0x000000007fe00000 physical
)
(II) intel(0): 0x00601000-0x0060afff: HW cursors (40 kB, 0x000000007fe01000 physical
)
(II) intel(0): 0x0060b000-0x0060bfff: overlay registers (4 kB, 0x000000007fe0b000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x007bf000-0x0f9f3fff: DRI memory manager (248020 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x007bf000:            start of memory manager
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x0f9f4000:            end of memory manager
(II) intel(0): using SSC reference clock of 100 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 220 x 129
(II) config/hal: Adding input device   USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event7"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**)   USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**)   USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**)   USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Asus EeePC extra buttons
(**) Asus EeePC extra buttons: always reports core events
(**) Asus EeePC extra buttons: Device: "/dev/input/event6"
(II) Asus EeePC extra buttons: Found keys
(II) Asus EeePC extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Asus EeePC extra buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Asus EeePC extra buttons: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Asus EeePC extra buttons: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Asus EeePC extra buttons: xkb_layout: "us"
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event8"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**)   USB Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**)   USB Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**)   USB Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device ETPS/2 Elantech Touchpad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event12"
(II) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
(II) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
(WW) ETPS/2 Elantech Touchpad: priv->synpara->movement_bottom_edge NOT AVAILABLE.
(II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
(II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
(II) ETPS/2 Elantech Touchpad: buttons: left right middle double triple
(--) ETPS/2 Elantech Touchpad touchpad found
(**) ETPS/2 Elantech Touchpad: always reports core events
(II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
(**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
(**) ETPS/2 Elantech Touchpad: (accel) filter chain progression: 2.00
(**) ETPS/2 Elantech Touchpad: (accel) filter stage 0: 20.00 ms
(**) ETPS/2 Elantech Touchpad: (accel) set acceleration profile 0
(--) ETPS/2 Elantech Touchpad touchpad found
(II) config/hal: Adding input device MosArt Optical Mouse
(**) MosArt Optical Mouse: always reports core events
(**) MosArt Optical Mouse: Device: "/dev/input/event5"
(II) MosArt Optical Mouse: Found 3 mouse buttons
(II) MosArt Optical Mouse: Found x and y relative axes
(II) MosArt Optical Mouse: Configuring as mouse
(**) MosArt Optical Mouse: YAxisMapping: buttons 4 and 5
(**) MosArt Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "MosArt Optical Mouse" (type: MOUSE)
(**) MosArt Optical Mouse: (accel) keeping acceleration scheme 1
(**) MosArt Optical Mouse: (accel) filter chain progression: 2.00
(**) MosArt Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) MosArt Optical Mouse: (accel) set acceleration profile 0
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
```

---

### Post by 09lefthand on 2009-10-26
After hours of googling, I found this solution from launchpad. So far it worked for me, 2 hours without glitches and blank screens.

First, ```
sudo gedit /etc/X11/xorg.conf

```

Then, add these lines into the "Device" section,

```
Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "ForceEnablePipeA" "true"
 Option "FramebufferCompression" "off"
EndSection
```

I will update if anything goes wrong in the next 24 hours.

---

### Post by ajaxaddicted on 2009-11-17
Same problem in Ubuntu 9.10 on EEPC 1000H, works fine after adding 

 Option "ForceEnablePipeA" "true"
 Option "FramebufferCompression" "off"

---

