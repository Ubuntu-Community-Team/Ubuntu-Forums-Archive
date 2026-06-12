---
title: "Excessive CPU usage (system pauses)"
date: 2009-03-20
forum: General Help
---

### Post by Torquemada28 on 2009-03-20
I've noticed increasing system "pauses" for a long time (6 months or so) but now it has got to the stage where it's annoying the absolute crap out of me. The first symptoms became evident when watching movies (.avi mostly). Different applications (VLC, MPlayer, etc) all behave slightly differently but they all suffered from "pauses" in one way or another. It started out as occasional stutters but now when watching a movie in VLC, the picture will freeze for 3-6 seconds but the audio continues. This will happen every 20-30 seconds on average. MPlayer will also freeze but both the audio and the picture will freeze. I then noticed that other applications (such as amarok, nautilus and firefox) would randomly "grey out" and stop responding.
This led me to have a look at the system monitor, where I discovered one of my CPU cores was maxing out. As I watched, the core 1 would be at 5% and core 2 would be between 82 and 100%, then they'd swap and core 1 would be the one maxing out (screenshots attached). Strange thing is, if I looked at the Processes tab on System Monitor, there was nothing using anywhere near that many cpu cycles.
I searched on this forum and read about the "top" command. This showed that Xorg was hovering at 80% CPU and above but only if I had system monitor open on the resources tab. When I ran VLC in fullscreen mode without System Monitor, "top" did report high CPU usage (screenshot attached) but I'm not sure if it's within normal range.

How the hell do I fix this? I can't even seem to identify the problem.
If I have to reinstall Ubuntu, I'm going to be mega-pissed.

---

### Post by wfp on 2009-03-20
I was having the same issues as you posted with vlc and video. I had to turn  desktop effects off that fixed it for me.

---

### Post by Torquemada28 on 2009-03-20
> **wfp said:**
> I was having the same issues as you posted with vlc and video. I had to turn  desktop effects off that fixed it for me.
I'll try that in the short-term but I'm rather fond of my desktop effects and would prefer a more complete resolution. After all, most people have desktop effects _and_ the ability to play video files. I don't see why I should have to choose between the two. My PC is more than adequate for the task.

---

### Post by Torquemada28 on 2009-03-20
El Bumpo

---

### Post by The Pinny Parlour on 2009-04-29
I am experiencing the exact issue you guys are experiencing.  Darn cpu is maxing and VLC is behave as described below.  Kind off ticks me off as previous version was okay.  My solution is to roll back to Intrepid.  Kinda sucks however.


> **wfp said:**
> I was having the same issues as you posted with vlc and video. I had to turn  desktop effects off that fixed it for me.

> **Torquemada28 said:**
> I've noticed increasing system "pauses" for a long time (6 months or so) but now it has got to the stage where it's annoying the absolute crap out of me. The first symptoms became evident when watching movies (.avi mostly). Different applications (VLC, MPlayer, etc) all behave slightly differently but they all suffered from "pauses" in one way or another. It started out as occasional stutters but now when watching a movie in VLC, the picture will freeze for 3-6 seconds but the audio continues. This will happen every 20-30 seconds on average. MPlayer will also freeze but both the audio and the picture will freeze. I then noticed that other applications (such as amarok, nautilus and firefox) would randomly "grey out" and stop responding.
This led me to have a look at the system monitor, where I discovered one of my CPU cores was maxing out. As I watched, the core 1 would be at 5% and core 2 would be between 82 and 100%, then they'd swap and core 1 would be the one maxing out (screenshots attached). Strange thing is, if I looked at the Processes tab on System Monitor, there was nothing using anywhere near that many cpu cycles.
I searched on this forum and read about the "top" command. This showed that Xorg was hovering at 80% CPU and above but only if I had system monitor open on the resources tab. When I ran VLC in fullscreen mode without System Monitor, "top" did report high CPU usage (screenshot attached) but I'm not sure if it's within normal range.

How the hell do I fix this? I can't even seem to identify the problem.
If I have to reinstall Ubuntu, I'm going to be mega-pissed.

---

### Post by mightyiam on 2009-04-29
Dear friends,

Does the Xorg.0.log show anything interesting? How about other logs?

Many blessings.

---

### Post by The Pinny Parlour on 2009-04-29
> **DawnLight said:**
> Dear friends,

Does the Xorg.0.log show anything interesting? How about other logs?

Many blessings.


Thank you.  It show a lot of information, is it interesting? not to me but hey it may float someone's boat.

Other logs?


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux tv-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 29 18:41:44 2009
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

(--) PCI:*(0@2:0:0) nVidia Corporation GeForce 8500 GT rev 161, Mem @ 0xdf000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.41.00.00
(II) NVIDIA(0): Detected PCI Express Link width: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:2:0:0:
(--) NVIDIA(0):     Panasonic-TV (DFP-0)
(--) NVIDIA(0): Panasonic-TV (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Panasonic-TV (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(WW) NVIDIA(0): Panasonic-TV (DFP-0)'s EDID does not contain a maximum image
(WW) NVIDIA(0):     size; cannot compute DPI from Panasonic-TV (DFP-0)'s
(WW) NVIDIA(0):     EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
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
(II) Initializing extension GLX
(II) config/hal: Adding input device HOLTEK Wireless 2.4GHz TouchPad Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: always reports core events
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Device: "/dev/input/event4"
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found 4 mouse buttons
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found x and y relative axes
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found keys
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Configuring as mouse
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Configuring as keyboard
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: YAxisMapping: buttons 4 and 5
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HOLTEK Wireless 2.4GHz TouchPad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_layout: "us"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) keeping acceleration scheme 1
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) filter chain progression: 2.00
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) filter stage 0: 20.00 ms
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: (accel) set acceleration profile 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device HOLTEK Wireless 2.4GHz TouchPad Keyboard
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: always reports core events
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Device: "/dev/input/event3"
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Found keys
(II) HOLTEK Wireless 2.4GHz TouchPad Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "HOLTEK Wireless 2.4GHz TouchPad Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HOLTEK Wireless 2.4GHz TouchPad Keyboard: xkb_layout: "us"

---

### Post by LowSky on 2009-04-29
> **The Pinny Parlour said:**
> I am experiencing the exact issue you guys are experiencing.  Darn cpu is maxing and VLC is behave as described below.  Kind off ticks me off as previous version was okay.  My solution is to roll back to Intrepid.  Kinda sucks however.

why does everyone think they have to roll back the distro, just uninstall VLC and install from source files the older verison or try a newer version if its available.

the easiest way is to install the old Intrepid DEB
[http://security.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc_0.9.4-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc_0.9.4-1ubuntu3.1_i386.deb)

just dont ever update or it might screw up again.

or use source code
here is the ftp to the older verisons

[http://download.videolan.org/pub/videolan/vlc/](http://download.videolan.org/pub/videolan/vlc/)

---

### Post by The Pinny Parlour on 2009-04-30
> **LowSky said:**
> why does everyone think they have to roll back the distro, just uninstall VLC and install from source files the older verison or try a newer version if its available.

the easiest way is to install the old Intrepid DEB
[http://security.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc_0.9.4-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc_0.9.4-1ubuntu3.1_i386.deb)

just dont ever update or it might screw up again.

or use source code
here is the ftp to the older verisons

[http://download.videolan.org/pub/videolan/vlc/](http://download.videolan.org/pub/videolan/vlc/)


Thank you but unfortunatly it is the same with Totem, so I think the issue is much deeper than just VLC.

And to answer your question, because rolling back to a version that worked for you previously is sensible.  "The easiest way" as you called it is NOT so easy for some.  Heck I didn't know you could do that.  :)

Cheers for the help but rolling back IS the ONLY option unless something or someone can shed better light on the issue.

---

