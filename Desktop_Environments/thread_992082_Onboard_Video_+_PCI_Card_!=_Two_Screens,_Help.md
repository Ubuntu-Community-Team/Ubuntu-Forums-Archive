---
title: "Onboard Video + PCI Card != Two Screens, Help?"
date: 2008-11-24
forum: Desktop Environments
---

### Post by Hubuki Kai on 2008-11-24
Hey guys,

I have my work computer sitting here. It was built on the cheap using scavenged parts mainly and Geeks.com. I'm running kubuntu 8.10.

The mobo I got is a server board. Dual xeons, no sound, onboard RAGE graphics, and only 2 PCI slots (3 PCI-X, but have you seen the prices on PCI-X stuff?). I need to have sound and a second monitor. I have an old soundblaster installed, works great, no problems, takes care of the sound.

The second monitor has been a major problem, though.

Since I have only PCI (effectively) on this board, I went and got a cheap dual-out ATI 7500 PCI card- which, when installed, makes the computer emit the beep of death. Works fine in other boards, though. Turns out, my board supports PCI 2.2, not 3.0- major difference being signal voltage levels (5v vs. 3.3v), and apparently that card was not a happy camper at 5v. So it's back for another cheap card- and being as I suspect that most "modern-ish" cards may have the same problem, I went with a fairly old card- a single-out RAGE card. I think it's identical to the onboard graphics. I know that combining on and off-board graphics messes with Windows, but Linux is much more capable, so I figured I'd be OK.

Well, yes and no. The card works (no beep of death), and X loads fine. However, I only see a single screen in the graphical system settings. I did an lspci:

00:00.0 Host bridge: Intel Corporation E7501 Memory Controller Hub (rev 01)
00:00.1 Class ff00: Intel Corporation E7500/E7501 Host RASUM Controller (rev 01)
00:02.0 PCI bridge: Intel Corporation E7500/E7501 Hub Interface B PCI-to-PCI Bridge (rev 01)
00:02.1 Class ff00: Intel Corporation E7500/E7501 Hub Interface B RASUM Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CA LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CA Ultra ATA Storage Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
01:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
01:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
01:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
01:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
04:01.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
04:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
04:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
04:03.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
04:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
04:05.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

There at the bottom, you can see that both devices are showing up.

I started up a console session, and did:

Xorg -configure

And it generated a great config file (two screens, two devices, all there, all detected). But when I tried to load it:

Xorg -config /home/me/xorg.conf.new

I got just the gray background and the X cursor, on one screen. In /var/log/xorg.0.log, I get this:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux cwsbox 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:2
0 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 22 10:41:28 2008
(++) Using config file: "/home/charlie/xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
...

(**) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
        X.Org Server Extension : 1.1
        X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@4:1:0) ATI Technologies Inc Rage XL rev 39, Mem @ 0xfc000000/0, 0xfb240000/0, I/O @ 0x00007000/0, BIOS @ 0x????????/131072
(--) PCI: (0@4:3:0) ATI Technologies Inc Rage XL rev 39, Mem @ 0xfd000000/0, 0xfb242000/0, I/O @ 0x00007800/0, BIOS @ 0x????????/131072
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified inthe config file.

...

(II) Primary Device is: PCI 04@00:01:0
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(==) MACH64(0): Depth 24, (==) framebuffer bpp 32
(==) MACH64(0): Using XAA acceleration architecture
(II) MACH64: Mach64 in slot 4:1:0 detected.
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 4.1
(II) MACH64(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) MACH64(0): VESA BIOS detected
(II) MACH64(0): VESA VBE Version 2.0
(II) MACH64(0): VESA VBE Total Mem: 8128 kB
(II) MACH64(0): VESA VBE OEM: ATI MACH64
(II) MACH64(0): VESA VBE OEM Software Rev: 1.0
(II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) MACH64(0): VESA VBE OEM Product: MACH64GM
(II) MACH64(0): VESA VBE OEM Product Rev: 01.00
(II) MACH64(0): VESA VBE DDC supported
(II) MACH64(0): VESA VBE DDC Level 2
(II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
(II) MACH64(0): VESA VBE DDC read successfully
(II) MACH64(0): Manufacturer: DEL  Model: 4025  Serial#: 827938124
(II) MACH64(0): Year: 2008  Week: 26
(II) MACH64(0): EDID Version: 1.3
(II) MACH64(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MACH64(0): Sync:  Separate  Composite  SyncOnGreen
(II) MACH64(0): Max Image Size [cm]: horiz.: 38  vert.: 30
(II) MACH64(0): Gamma: 2.20
(II) MACH64(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MACH64(0): Default color space is primary color space
(II) MACH64(0): First detailed timing is preferred mode
(II) MACH64(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) MACH64(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) MACH64(0): Supported VESA Video Modes:
(II) MACH64(0): 720x400@70Hz
(II) MACH64(0): 640x480@60Hz
(II) MACH64(0): 640x480@75Hz
(II) MACH64(0): 800x600@60Hz
(II) MACH64(0): 800x600@75Hz
(II) MACH64(0): 1024x768@60Hz
(II) MACH64(0): 1024x768@75Hz
(II) MACH64(0): 1280x1024@75Hz
(II) MACH64(0): Manufacturer's mask: 0
(II) MACH64(0): Supported Future Video Modes:
(II) MACH64(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) MACH64(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MACH64(0): Supported additional Video Mode:
(II) MACH64(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) MACH64(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) MACH64(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) MACH64(0): Serial No: G313H86P1YUL
(II) MACH64(0): Monitor name: DELL 1908FP
(II) MACH64(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 140 MHz
(II) MACH64(0): EDID (in hex):
(II) MACH64(0):         00ffffffffffff0010ac25404c555931
(II) MACH64(0):         1a1201030e261e78eeee91a3544c9926
(II) MACH64(0):         0f5054a54b00714f8180010101010101
(II) MACH64(0):         010101010101302a009851002a403070
(II) MACH64(0):         1300782d1100001e000000ff00473331
(II) MACH64(0): EDID vendor "DEL", prod id 16421
(II) MACH64(0): Using hsync ranges from config file
(II) MACH64(0): Using vrefresh ranges from config file
(II) MACH64(0): Printing DDC gathered Modelines:
(II) MACH64(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MACH64(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MACH64(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MACH64(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MACH64(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MACH64(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MACH64(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) MACH64(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) MACH64(0): BIOS Data:  BIOSSize=0x8000, ROMTable=0x010E.
(II) MACH64(0): BIOS Data:  ClockTable=0x097C, FrequencyTable=0x0000.
(II) MACH64(0): BIOS Data:  LCDTable=0x0000.
(II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0158.
(II) MACH64(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) MACH64(0): ATI 3D Rage XL or XC graphics controller detected.
(--) MACH64(0): Chip type 4752 "GR", version 7, foundry TSMC, class 0, revision
(--) MACH64(0): PCI bus interface detected;  block I/O base is 0x7000.
(--) MACH64(0): ATI Mach64 adapter detected.
(!!) MACH64(0): For information on using the multimedia capabilities
        of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) MACH64(0): Internal RAMDAC (subtype 1) detected.
(==) MACH64(0): RGB weight 888
(==) MACH64(0): Default visual is TrueColor
(==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
(II) MACH64(0): Using Mach64 accelerator CRTC.
(WW) MACH64(0): Logic error setting operating state for VGA I/O.
(II) MACH64(0): Storing hardware cursor image at 0xFC7FFC00.
(II) MACH64(0): Using 8 MB linear aperture at 0xFC000000.
(!!) MACH64(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) MACH64(0): Using Block 0 MMIO aperture at 0xFB240400.
(II) MACH64(0): Using Block 1 MMIO aperture at 0xFB240000.
(WW) MACH64(0): Logic error setting operating state for VGA memory aperture.
(II) MACH64(0): MMIO write caching enabled.
(--) MACH64(0): 8192 kB of SGRAM (2:1) 32-bit detected (using 8191 kB).
(WW) MACH64(0): Cannot shadow an accelerated frame buffer.
(II) MACH64(0): Engine XCLK 62.815 MHz;  Refresh rate code 1.
(--) MACH64(0): Internal programmable clock generator detected.
(--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
(II) MACH64(0): Monitor0: Using hsync range of 31.00-83.00 kHz
(II) MACH64(0): Monitor0: Using vrefresh range of 56.00-76.00 Hz
(II) MACH64(0): Monitor0: Using maximum pixel clock of 140.00 MHz
(II) MACH64(0): Estimated virtual size for aspect ratio 1.2667 is 1280x1024
(II) MACH64(0): Maximum clock: 125.00 MHz
(II) MACH64(0): Not using default mode "640x350" (vrefresh out of range)
(II) MACH64(0): Not using default mode "320x175" (vrefresh out of range)

...

(**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 26
2 doublescan -hsync -vsync (31.5 kHz)
(**) MACH64(0): Display dimensions: (380, 300) mm
(**) MACH64(0): DPI set to (85, 86)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(==) MACH64(1): Depth 24, (==) framebuffer bpp 32
(==) MACH64(1): Using XAA acceleration architecture
(WW) MACH64: Mach64 in slot 4:3:0 could not be detected!
(II) UnloadModule: "mach64"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(WW) MACH64(0): DRI static buffer allocation failed -- need at least 12800 kB vi
deo memory
(II) MACH64(0): Largest offscreen areas (with overlaps):
(II) MACH64(0):         1280 x 614 rectangle at 0,1024
(II) MACH64(0):         256 x 615 rectangle at 0,1024
(II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Setting up tile and stipple cache:
                20 128x128 slots
                5 256x256 slots
(==) MACH64(0): Backing store disabled
(==) MACH64(0): Silken mouse enabled
(**) Option "dpms"
(**) MACH64(0): DPMS enabled
(II) MACH64(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0

Whew. Well, to save some searching, I took out the most repetetive and boring entries, but there very near the bottom it says

(II) Module "i2c" already built-in
(II) MACH64(0): I2C bus "Mach64" initialized.
(==) MACH64(1): Depth 24, (==) framebuffer bpp 32
(==) MACH64(1): Using XAA acceleration architecture
(WW) MACH64: Mach64 in slot 4:3:0 could not be detected!
(II) UnloadModule: "mach64"

At this point I'm stumped. It shows up on the PCI bus with two devices, in diferent locations. Xorg -config detects and configures for two devices and two screens, but when it tries to execute, it gets major problems. For completeness, here's the xorg.conf that generates this. Note that I haven't tried overwriting my "real" xorg.conf, as it seems to be broken (hence this post), and I don't know if that would be different from Xorg -config.

The conf file:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "glx"
	Load  "xtrap"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  380   300	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL 1908FP"
	HorizSync    31.0 - 83.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "probe_sparse"       	# [<bool>]
        #Option     "accel"              	# [<bool>]
        #Option     "crt_display"        	# [<bool>]
        #Option     "composite_sync"     	# [<bool>]
        #Option     "hw_cursor"          	# [<bool>]
        #Option     "force_pci_mode"     	# [<bool>]
        #Option     "dma_mode"           	# <str>
        #Option     "agp_mode"           	# <i>
        #Option     "agp_size"           	# <i>
        #Option     "local_textures"     	# [<bool>]
        #Option     "buffer_size"        	# <i>
        #Option     "tv_out"             	# [<bool>]
        #Option     "tv_standard"        	# <str>
        #Option     "mmio_cache"         	# [<bool>]
        #Option     "test_mmio_cache"    	# [<bool>]
        #Option     "panel_display"      	# [<bool>]
        #Option     "reference_clock"    	# <freq>
        #Option     "shadow_fb"          	# [<bool>]
        #Option     "sw_cursor"          	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "RenderAccel"        	# [<bool>]
	Identifier  "Card0"
	Driver      "mach64"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage XL"
	BusID       "PCI:4:1:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "probe_sparse"       	# [<bool>]
        #Option     "accel"              	# [<bool>]
        #Option     "crt_display"        	# [<bool>]
        #Option     "composite_sync"     	# [<bool>]
        #Option     "hw_cursor"          	# [<bool>]
        #Option     "force_pci_mode"     	# [<bool>]
        #Option     "dma_mode"           	# <str>
        #Option     "agp_mode"           	# <i>
        #Option     "agp_size"           	# <i>
        #Option     "local_textures"     	# [<bool>]
        #Option     "buffer_size"        	# <i>
        #Option     "tv_out"             	# [<bool>]
        #Option     "tv_standard"        	# <str>
        #Option     "mmio_cache"         	# [<bool>]
        #Option     "test_mmio_cache"    	# [<bool>]
        #Option     "panel_display"      	# [<bool>]
        #Option     "reference_clock"    	# <freq>
        #Option     "shadow_fb"          	# [<bool>]
        #Option     "sw_cursor"          	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "RenderAccel"        	# [<bool>]
	Identifier  "Card1"
	Driver      "mach64"
	VendorName  "ATI Technologies Inc"
	BoardName   "Rage XL"
	BusID       "PCI:4:3:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by Hubuki Kai on 2008-12-11
I never was able to get this to work! This is just a bump; I've gone back periodically but I haven't been able to find any more info or tease anything extra out of the log files. lspci still shows two devices, but onboard is not working.

Any help is appreciated greatly!

---

