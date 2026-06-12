---
title: "Nvidia Geforce4 MX driver 96 not functioning"
date: 2009-06-26
forum: Desktop Environments
---

### Post by DyBurke on 2009-06-26
Hey, guys.  I'm having trouble enabling desktop effects/change resolution to a proper one.  I've enabled the proprietary nvidia drivers using System>Administration>Hardware Drivers which makes the xserver crash repeatedly at bootup until it finally asks if I would like to start the xserver in low graphics mode.  I've tried everything I could find with a lot of Google searches.  Can't seem to find the bottom of this.

If you would like any other information, please just ask.  I will be more than happy to provide you with any logs I can.

Info on the card I have:

```
 dburke@Lucy:~$ lspci | grep -i nvidia
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)         
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)             
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) 
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)                        
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)                                     
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)                                        
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) 
```



In my Xorg.0.log I found "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)":

```
 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Lucy 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 25 21:53:14 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
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
(++) using VT number 9

(--) PCI:*(0@2:0:0) nVidia Corporation NV18 [GeForce4 MX - nForce GPU] rev 163, Mem @ 0xe2000000/16777216, 0xd0000000/134217728, 0xd8000000/524288, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.10  Sat Jan 24 20:04:30 PST 2009
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
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 02@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 131072 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 4.31
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: CR17 Board
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A3
(II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: FNI  Model: 0  Serial#: 0
(II) VESA(0): Year: 2007  Week: 0
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.649 redY: 0.332   greenX: 0.274 greenY: 0.673
(II) VESA(0): blueX: 0.164 blueY: 0.101   whiteX: 0.320 whiteY: 0.334
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 848  vsize 477  refresh: 60  vid: 49227
(II) VESA(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 79.5 MHz   Image Size:  410 x 257 mm
(II) VESA(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 85.5 MHz   Image Size:  410 x 257 mm
(II) VESA(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 74.2 MHz   Image Size:  410 x 257 mm
(II) VESA(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
(II) VESA(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 106.5 MHz   Image Size:  410 x 257 mm
(II) VESA(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) VESA(0): Number of EDID sections to follow: 1
(II) VESA(0): EDID (in hex):
(II) VESA(0):     00ffffffffffff0019c9000000000000
(II) VESA(0):     0011010308291a780a4532a65546ac2a
(II) VESA(0):     195255a108004bc09500010101010101
(II) VESA(0):     0101010101010e1f008051001e304080
(II) VESA(0):     37009a011100001c662150b051001b30
(II) VESA(0):     407036009a011100001e011d007251d0
(II) VESA(0):     1e206e2855009a011100001e9a29a0d0
(II) VESA(0):     51842230509836009a011100001c01dc
(II) VESA(0): EDID vendor "FNI", prod id 0
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) VESA(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) VESA(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "848x477"x60.0   31.30  848 864 952 1056  477 478 481 494 -hsync +vsync (29.6 kHz)
(II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 14
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 14
    LinNumberOfImagePages: 14
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 101 (640x480)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 640
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 10
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 10
    LinNumberOfImagePages: 10
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 102 (800x600)
    ModeAttributes: 0x31f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 100
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 4
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 3
    BankSize: 0
    NumberOfImages: 14
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 100
    BnkNumberOfImagePages: 14
    LinNumberOfImagePages: 14
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 103 (800x600)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 800
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 6
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 800
    BnkNumberOfImagePages: 6
    LinNumberOfImagePages: 6
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 104 (1024x768)
    ModeAttributes: 0x31f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 128
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 4
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 3
    BankSize: 0
    NumberOfImages: 6
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 128
    BnkNumberOfImagePages: 6
    LinNumberOfImagePages: 6
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 105 (1024x768)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1024
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 3
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1024
    BnkNumberOfImagePages: 3
    LinNumberOfImagePages: 3
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 106 (1280x1024)
    ModeAttributes: 0x31f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 160
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 4
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 3
    BankSize: 0
    NumberOfImages: 3
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0x0
    LinBytesPerScanLine: 160
    BnkNumberOfImagePages: 3
    LinNumberOfImagePages: 3
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 107 (1280x1024)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1280
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 108 (80x60)
    ModeAttributes: 0x38f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 32
    WinSize: 32
    WinASegment: 0xb800
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 160
    XResolution: 80
    YResolution: 60
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 160
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 109 (132x25)
    ModeAttributes: 0x38f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 32
    WinSize: 32
    WinASegment: 0xb800
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 264
    XResolution: 132
    YResolution: 25
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 264
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 10a (132x43)
    ModeAttributes: 0x38f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 32
    WinSize: 32
    WinASegment: 0xb800
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 264
    XResolution: 132
    YResolution: 43
    XCharSize: 8
    YCharSize: 9
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 264
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 10b (132x50)
    ModeAttributes: 0x38f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 32
    WinSize: 32
    WinASegment: 0xb800
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 264
    XResolution: 132
    YResolution: 50
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 264
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 10c (132x60)
    ModeAttributes: 0x38f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 32
    WinSize: 32
    WinASegment: 0xb800
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 264
    XResolution: 132
    YResolution: 60
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 4
    NumberOfBanks: 1
    MemoryModel: 0
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 264
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 108500000
Mode: 10e (320x200)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 30
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 30
    LinNumberOfImagePages: 30
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 10f (320x200)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1280
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 14
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 14
    LinNumberOfImagePages: 14
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 111 (640x480)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 4
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 4
    LinNumberOfImagePages: 4
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 112 (640x480)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 480
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 114 (800x600)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1600
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 115 (800x600)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 3200
    XResolution: 800
    YResolution: 600
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 117 (1024x768)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 2048
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2048
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 118 (1024x768)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 4096
    XResolution: 1024
    YResolution: 768
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 4096
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 11a (1280x1024)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 2560
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 11b (1280x1024)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 5120
    XResolution: 1280
    YResolution: 1024
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 5120
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 130 (320x200)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 320
    XResolution: 320
    YResolution: 200
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 62
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 320
    BnkNumberOfImagePages: 62
    LinNumberOfImagePages: 62
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 131 (320x400)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 320
    XResolution: 320
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 30
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 320
    BnkNumberOfImagePages: 30
    LinNumberOfImagePages: 30
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 132 (320x400)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 14
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 14
    LinNumberOfImagePages: 14
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 133 (320x400)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1280
    XResolution: 320
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 6
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 6
    LinNumberOfImagePages: 6
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 134 (320x240)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 320
    XResolution: 320
    YResolution: 240
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 30
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 320
    BnkNumberOfImagePages: 30
    LinNumberOfImagePages: 30
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 135 (320x240)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 640
    XResolution: 320
    YResolution: 240
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 19
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 640
    BnkNumberOfImagePages: 19
    LinNumberOfImagePages: 19
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 136 (320x240)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1280
    XResolution: 320
    YResolution: 240
    XCharSize: 8
    YCharSize: 8
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 10
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 10
    LinNumberOfImagePages: 10
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 13d (640x400)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1280
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 6
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1280
    BnkNumberOfImagePages: 6
    LinNumberOfImagePages: 6
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 13e (640x400)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 2560
    XResolution: 640
    YResolution: 400
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 2
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2560
    BnkNumberOfImagePages: 2
    LinNumberOfImagePages: 2
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000
Mode: 145 (1600x1200)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1600
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1600
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 146 (1600x1200)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 3200
    XResolution: 1600
    YResolution: 1200
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 3200
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 147 (1400x1050)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 1400
    XResolution: 1400
    YResolution: 1050
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 8
    NumberOfBanks: 1
    MemoryModel: 4
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 0
    RedFieldPosition: 0
    GreenMaskSize: 0
    GreenFieldPosition: 0
    BlueMaskSize: 0
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 1400
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 0
    LinRedFieldPosition: 0
    LinGreenMaskSize: 0
    LinGreenFieldPosition: 0
    LinBlueMaskSize: 0
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
Mode: 148 (1400x1050)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 2800
    XResolution: 1400
    YResolution: 1050
    XCharSize: 8
    YCharSize: 14
    NumberOfPlanes: 1
    BitsPerPixel: 16
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 1
    RedMaskSize: 5
    RedFieldPosition: 11
    GreenMaskSize: 6
    GreenFieldPosition: 5
    BlueMaskSize: 5
    BlueFieldPosition: 0
    RsvdMaskSize: 0
    RsvdFieldPosition: 0
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 2800
    BnkNumberOfImagePages: 1
    LinNumberOfImagePages: 1
    LinRedMaskSize: 5
    LinRedFieldPosition: 11
    LinGreenMaskSize: 6
    LinGreenFieldPosition: 5
    LinBlueMaskSize: 5
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 0
    LinRsvdFieldPosition: 0
    MaxPixelClock: 229500000
*Mode: 152 (2048x1536)
    ModeAttributes: 0x39f
    WinAAttributes: 0x7
    WinBAttributes: 0x0
    WinGranularity: 64
    WinSize: 64
    WinASegment: 0xa000
    WinBSegment: 0x0
    WinFuncPtr: 0xc00084c6
    BytesPerScanline: 8192
    XResolution: 2048
    YResolution: 1536
    XCharSize: 8
    YCharSize: 16
    NumberOfPlanes: 1
    BitsPerPixel: 32
    NumberOfBanks: 1
    MemoryModel: 6
    BankSize: 0
    NumberOfImages: 0
    RedMaskSize: 8
    RedFieldPosition: 16
    GreenMaskSize: 8
    GreenFieldPosition: 8
    BlueMaskSize: 8
    BlueFieldPosition: 0
    RsvdMaskSize: 8
    RsvdFieldPosition: 24
    DirectColorModeInfo: 0
    PhysBasePtr: 0xd0000000
    LinBytesPerScanLine: 8192
    BnkNumberOfImagePages: 0
    LinNumberOfImagePages: 0
    LinRedMaskSize: 8
    LinRedFieldPosition: 16
    LinGreenMaskSize: 8
    LinGreenFieldPosition: 8
    LinBlueMaskSize: 8
    LinBlueFieldPosition: 0
    LinRsvdMaskSize: 8
    LinRsvdFieldPosition: 24
    MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 2048 64KB banks (131072kB)
(II) VESA(0): Configured Monitor: Using hsync range of 29.64-55.93 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 59.87-70.08 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (410, 260) mm
(**) VESA(0): DPI set to (63, 75)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 131072 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 4.31
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: CR17 Board
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A3
(II) VESA(0): virtual address = 0xaedb4000,
    physical address = 0xd0000000, size = 134217728
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
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
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
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
(II) config/hal: Adding input device Microsoft Basic Optical Mouse
(**) Microsoft Basic Optical Mouse: always reports core events
(**) Microsoft Basic Optical Mouse: Device: "/dev/input/event4"
(II) Microsoft Basic Optical Mouse: Found 3 mouse buttons
(II) Microsoft Basic Optical Mouse: Found x and y relative axes
(II) Microsoft Basic Optical Mouse: Configuring as mouse
(**) Microsoft Basic Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Microsoft Basic Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Basic Optical Mouse" (type: MOUSE)
(**) Microsoft Basic Optical Mouse: (accel) keeping acceleration scheme 1
(**) Microsoft Basic Optical Mouse: (accel) filter chain progression: 2.00
(**) Microsoft Basic Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Microsoft Basic Optical Mouse: (accel) set acceleration profile 0
```Here is my xorg.config:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```I ran compiz-check and got these results:

```
 dburke@Lucy:~$ ./compiz-check       

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card.

Check if there's an alternate (proprietary) driver available? (Y/n) y

```Why does it say I'm using the vesa driver if both Hardware Drivers and the xorg config say I'm using nvidia?

Here's the output from the cmd 'sudo lshw' (Sorry for the length, I didn't want to miss anything.):

```
 dburke@Lucy:~$ sudo lshw                                                                                                        
lucy                                                                                                                            
    description: Desktop Computer                                                                                               
    product: Product Name                                                                                                       
    vendor: eMachines                                                                                                           
    version: SYS-xxxxxx                                                                                                         
    serial: Serial number xxxxxx                                                                                                
    width: 32 bits                                                                                                              
    capabilities: smbios-2.3 dmi-2.3 smp                                                                                        
    configuration: boot=normal chassis=desktop                                                                                  
  *-core                                                                                                                        
       description: Motherboard                                                                                                 
       product: AU31                                                                                                            
       vendor: First International Computer, Inc.                                                                               
       physical id: 0                                                                                                           
       version: PCB 1.x                                                                                                         
       serial: Serial number xxxxxx                                                                                             
     *-firmware                                                                                                                 
          description: BIOS                                                                                                     
          vendor: Phoenix Technologies, LTD                                                                                     
          physical id: 0                                                                                                        
          version: TCB427G (05/12/2004)                                                                                         
          size: 128KiB                                                                                                          
          capacity: 192KiB                                                                                                      
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification               
     *-cpu                                                                                                                      
          description: CPU                                                                                                      
          product: AMD Athlon(tm) XP 3000+                                                                                      
          vendor: Advanced Micro Devices [AMD]                                                                                  
          physical id: 4                                                                                                        
          bus info: cpu@0                                                                                                       
          version: 6.10.0                                                                                                       
          slot: Socket A                                                                                                        
          size: 2171MHz                                                                                                         
          capacity: 2800MHz                                                                                                     
          width: 32 bits                                                                                                        
          clock: 166MHz                                                                                                         
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up cpufreq                                                                                          
        *-cache:0                                                                                                               
             description: L1 cache                                                                                              
             physical id: 8                                                                                                     
             slot: Internal Cache                                                                                               
             size: 128KiB                                                                                                       
             capacity: 128KiB                                                                                                   
             capabilities: synchronous internal write-back                                                                      
        *-cache:1                                                                                                               
             description: L2 cache                                                                                              
             physical id: 9                                                                                                     
             slot: External Cache                                                                                               
             size: 512KiB                                                                                                       
             capacity: 512KiB                                                                                                   
             capabilities: synchronous external write-back                                                                      
     *-memory                                                                                                                   
          description: System Memory                                                                                            
          physical id: 18                                                                                                       
          slot: System board or motherboard                                                                                     
          size: 768MiB                                                                                                          
          capacity: 1GiB                                                                                                        
        *-bank:0                                                                                                                
             description: DIMM                                                                                                  
             product: None                                                                                                      
             vendor: None                                                                                                       
             physical id: 0                                                                                                     
             serial: None                                                                                                       
             slot: A0                                                                                                           
             size: 256MiB                                                                                                       
        *-bank:1                                                                                                                
             description: DIMM                                                                                                  
             product: None                                                                                                      
             vendor: None                                                                                                       
             physical id: 1                                                                                                     
             serial: None                                                                                                       
             slot: A1                                                                                                           
             size: 512MiB                                                                                                       
     *-pci                                                                                                                      
          description: Host bridge                                                                                              
          product: nForce2 IGP2                                                                                                 
          vendor: nVidia Corporation                                                                                            
          physical id: 100                                                                                                      
          bus info: pci@0000:00:00.0                                                                                            
          version: a2                                                                                                           
          width: 32 bits                                                                                                        
          clock: 66MHz                                                                                                          
          configuration: driver=agpgart-nvidia module=nvidia_agp                                                                
        *-memory:0 UNCLAIMED                                                                                                    
             description: RAM memory                                                                                            
             product: nForce2 Memory Controller 1                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 0.1                                                                                                   
             bus info: pci@0000:00:00.1                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz (15.2ns)                                                                                              
             configuration: latency=0                                                                                           
        *-memory:1 UNCLAIMED                                                                                                    
             description: RAM memory                                                                                            
             product: nForce2 Memory Controller 4                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 0.2                                                                                                   
             bus info: pci@0000:00:00.2                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz (15.2ns)                                                                                              
             configuration: latency=0                                                                                           
        *-memory:2 UNCLAIMED                                                                                                    
             description: RAM memory                                                                                            
             product: nForce2 Memory Controller 3                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 0.3                                                                                                   
             bus info: pci@0000:00:00.3                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz (15.2ns)                                                                                              
             configuration: latency=0                                                                                           
        *-memory:3 UNCLAIMED                                                                                                    
             description: RAM memory                                                                                            
             product: nForce2 Memory Controller 2                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 0.4                                                                                                   
             bus info: pci@0000:00:00.4                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz (15.2ns)                                                                                              
             configuration: latency=0                                                                                           
        *-memory:4 UNCLAIMED                                                                                                    
             description: RAM memory                                                                                            
             product: nForce2 Memory Controller 5                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 0.5                                                                                                   
             bus info: pci@0000:00:00.5                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz (15.2ns)                                                                                              
             configuration: latency=0                                                                                           
        *-isa                                                                                                                   
             description: ISA bridge                                                                                            
             product: nForce2 ISA Bridge                                                                                        
             vendor: nVidia Corporation                                                                                         
             physical id: 1                                                                                                     
             bus info: pci@0000:00:01.0                                                                                         
             version: a4                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: isa ht bus_master cap_list                                                                           
             configuration: latency=0                                                                                           
        *-serial                                                                                                                
             description: SMBus                                                                                                 
             product: nForce2 SMBus (MCP)                                                                                       
             vendor: nVidia Corporation                                                                                         
             physical id: 1.1                                                                                                   
             bus info: pci@0000:00:01.1                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pm cap_list                                                                                          
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2                             
        *-usb:0                                                                                                                 
             description: USB Controller                                                                                        
             product: nForce2 USB Controller                                                                                    
             vendor: nVidia Corporation                                                                                         
             physical id: 2                                                                                                     
             bus info: pci@0000:00:02.0                                                                                         
             version: a4                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pm bus_master cap_list                                                                               
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3                                                     
        *-usb:1                                                                                                                 
             description: USB Controller                                                                                        
             product: nForce2 USB Controller                                                                                    
             vendor: nVidia Corporation                                                                                         
             physical id: 2.1                                                                                                   
             bus info: pci@0000:00:02.1                                                                                         
             version: a4                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pm bus_master cap_list                                                                               
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3                                                     
        *-usb:2                                                                                                                 
             description: USB Controller                                                                                        
             product: nForce2 USB Controller                                                                                    
             vendor: nVidia Corporation                                                                                         
             physical id: 2.2                                                                                                   
             bus info: pci@0000:00:02.2                                                                                         
             version: a4                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: debug pm bus_master cap_list                                                                         
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd                                     
        *-network                                                                                                               
             description: Ethernet interface                                                                                    
             product: nForce2 Ethernet Controller                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 4                                                                                                     
             bus info: pci@0000:00:04.0                                                                                         
             logical name: eth0                                                                                                 
             version: a1                                                                                                        
             serial: 00:40:ca:7f:3f:e1                                                                                          
             size: 100MB/s                                                                                                      
             capacity: 100MB/s                                                                                                  
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation             
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.112 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s                                   
        *-multimedia:0 UNCLAIMED                                                                                                
             description: Multimedia audio controller                                                                           
             product: nForce Audio Processing Unit                                                                              
             vendor: nVidia Corporation                                                                                         
             physical id: 5                                                                                                     
             bus info: pci@0000:00:05.0                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pm bus_master cap_list                                                                               
             configuration: latency=0 maxlatency=12 mingnt=1                                                                    
        *-multimedia:1                                                                                                          
             description: Multimedia audio controller                                                                           
             product: nForce2 AC97 Audio Controler (MCP)                                                                        
             vendor: nVidia Corporation                                                                                         
             physical id: 6                                                                                                     
             bus info: pci@0000:00:06.0                                                                                         
             version: a1                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pm bus_master cap_list                                                                               
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0                                
        *-pci:0                                                                                                                 
             description: PCI bridge                                                                                            
             product: nForce2 External PCI Bridge                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 8                                                                                                     
             bus info: pci@0000:00:08.0                                                                                         
             version: a3                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pci bus_master                                                                                       
           *-network UNCLAIMED                                                                                                  
                description: Network controller                                                                                 
                product: BCM4306 802.11b/g Wireless LAN Controller                                                              
                vendor: Broadcom Corporation                                                                                    
                physical id: 7                                                                                                  
                bus info: pci@0000:01:07.0                                                                                      
                version: 03                                                                                                     
                width: 32 bits                                                                                                  
                clock: 33MHz                                                                                                    
                capabilities: bus_master                                                                                        
                configuration: latency=32                                                                                       
           *-communication UNCLAIMED                                                                                            
                description: Communication controller                                                                           
                product: HSF 56k Data/Fax Modem                                                                                 
                vendor: Conexant Systems, Inc.                                                                                  
                physical id: 8                                                                                                  
                bus info: pci@0000:01:08.0                                                                                      
                version: 00                                                                                                     
                width: 32 bits                                                                                                  
                clock: 33MHz                                                                                                    
                capabilities: pm bus_master cap_list                                                                            
                configuration: latency=32                                                                                       
        *-ide                                                                                                                   
             description: IDE interface                                                                                         
             product: nForce2 IDE                                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 9                                                                                                     
             bus info: pci@0000:00:09.0                                                                                         
             logical name: scsi0                                                                                                
             logical name: scsi1                                                                                                
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: ide pm bus_master cap_list emulated                                                                  
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3                                                     
           *-disk                                                                                                               
                description: ATA Disk                                                                                           
                product: WDC WD1600BB-00F                                                                                       
                vendor: Western Digital                                                                                         
                physical id: 0                                                                                                  
                bus info: scsi@0:0.0.0                                                                                          
                logical name: /dev/sda                                                                                          
                version: 15.0                                                                                                   
                serial: WD-WMAES3275472                                                                                         
                size: 149GiB (160GB)                                                                                            
                capabilities: partitioned partitioned:dos                                                                       
                configuration: ansiversion=5 signature=3972cd75                                                                 
              *-volume:0                                                                                                        
                   description: Windows NTFS volume                                                                             
                   physical id: 1                                                                                               
                   bus info: scsi@0:0.0.0,1                                                                                     
                   logical name: /dev/sda1                                                                                      
                   version: 3.1                                                                                                 
                   serial: 845f9817-4b5d-1141-a2be-7f53abc4f318                                                                 
                   size: 73GiB                                                                                                  
                   capacity: 73GiB                                                                                              
                   capabilities: primary bootable ntfs initialized                                                              
                   configuration: clustersize=4096 created=2008-06-22 04:41:58 filesystem=ntfs state=clean                      
              *-volume:1                                                                                                        
                   description: EXT3 volume                                                                                     
                   vendor: Linux                                                                                                
                   physical id: 2                                                                                               
                   bus info: scsi@0:0.0.0,2                                                                                     
                   logical name: /dev/sda2                                                                                      
                   logical name: /                                                                                              
                   version: 1.0                                                                                                 
                   serial: 18009a53-ce69-4139-8802-634772621033                                                                 
                   size: 74GiB                                                                                                  
                   capacity: 74GiB                                                                                              
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized                
                   configuration: created=2008-10-29 18:01:23 filesystem=ext3 modified=2009-06-25 21:51:24 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-06-25 21:51:24 state=mounted                                 
              *-volume:2                                                                                                        
                   description: Extended partition                                                                              
                   physical id: 3                                                                                               
                   bus info: scsi@0:0.0.0,3                                                                                     
                   logical name: /dev/sda3                                                                                      
                   size: 956MiB                                                                                                 
                   capacity: 956MiB                                                                                             
                   capabilities: primary extended partitioned partitioned:extended                                              
                 *-logicalvolume                                                                                                
                      description: Linux swap / Solaris partition                                                               
                      physical id: 5                                                                                            
                      logical name: /dev/sda5                                                                                   
                      capacity: 956MiB                                                                                          
                      capabilities: nofs                                                                                        
           *-cdrom:0                                                                                                            
                description: DVD writer                                                                                         
                product: DVDRW SOHW-812S                                                                                        
                vendor: LITE-ON                                                                                                 
                physical id: 1                                                                                                  
                bus info: scsi@1:0.0.0                                                                                          
                logical name: /dev/cdrom                                                                                        
                logical name: /dev/cdrw                                                                                         
                logical name: /dev/dvd                                                                                          
                logical name: /dev/dvdrw                                                                                        
                logical name: /dev/scd0                                                                                         
                logical name: /dev/sr0                                                                                          
                version: UTS2                                                                                                   
                capabilities: removable audio cd-r cd-rw dvd dvd-r                                                              
                configuration: ansiversion=5 status=nodisc                                                                      
           *-cdrom:1                                                                                                            
                description: SCSI CD-ROM                                                                                        
                physical id: 0.1.0                                                                                              
                bus info: scsi@1:0.1.0                                                                                          
                logical name: /dev/cdrom1                                                                                       
                logical name: /dev/scd1                                                                                         
                logical name: /dev/sr1                                                                                          
                logical name: /media/Note Cards for__                                                                           
                capabilities: audio partitioned partitioned:mac                                                                 
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted status=ready      
              *-volume:0 UNCLAIMED                                                                                              
                   description: Apple partition map                                                                             
                   physical id: 1                                                                                               
                   bus info: scsi@1:0.1.0,1                                                                                     
                   capacity: 17KiB                                                                                              
              *-volume:1 UNCLAIMED                                                                                              
                   description: Apple HFS                                                                                       
                   vendor: Mac OS X                                                                                             
                   physical id: 2                                                                                               
                   bus info: scsi@1:0.1.0,2                                                                                     
                   version: 4                                                                                                   
                   serial: 00000000-0000-0000-0000-000000004000                                                                 
                   size: 425MiB                                                                                                 
                   capacity: 425MiB                                                                                             
                   capabilities: hfsplus initialized                                                                            
                   configuration: checked=1903-12-31 16:00:00 created=2009-01-12 18:31:13 filesystem=hfsplus lastmountedby=10.0 modified=2009-01-12 10:41:07 state=clean                                                                                        
        *-pci:1                                                                                                                 
             description: PCI bridge                                                                                            
             product: nForce2 AGP                                                                                               
             vendor: nVidia Corporation                                                                                         
             physical id: 1e                                                                                                    
             bus info: pci@0000:00:1e.0                                                                                         
             version: a2                                                                                                        
             width: 32 bits                                                                                                     
             clock: 66MHz                                                                                                       
             capabilities: pci bus_master                                                                                       
           *-display                                                                                                            
                description: VGA compatible controller                                                                          
                product: NV18 [GeForce4 MX - nForce GPU]                                                                        
                vendor: nVidia Corporation                                                                                      
                physical id: 0                                                                                                  
                bus info: pci@0000:02:00.0                                                                                      
                version: a3                                                                                                     
                width: 32 bits                                                                                                  
                clock: 66MHz                                                                                                    
                capabilities: pm agp agp-2.0 bus_master cap_list                                                                
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia                                    
     *-scsi                                                                                                                     
          physical id: 1                                                                                                        
          bus info: usb@3:3                                                                                                     
          logical name: scsi2                                                                                                   
          capabilities: emulated scsi-host                                                                                      
          configuration: driver=usb-storage                                                                                     
        *-disk:0                                                                                                                
             description: SCSI Disk                                                                                             
             physical id: 0.0.0                                                                                                 
             bus info: scsi@2:0.0.0                                                                                             
             logical name: /dev/sdb                                                                                             
        *-disk:1                                                                                                                
             description: SCSI Disk                                                                                             
             physical id: 0.0.1                                                                                                 
             bus info: scsi@2:0.0.1                                                                                             
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:47:d7:a9:f0:18
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Even More:

The results of the cmd dmesg |grep -i nv :

```
dburke@Lucy:~$ dmesg |grep -i nv
[    0.000000]  BIOS-e820: 0000000027ff0000 - 0000000027ff3000 (ACPI NVS)
[    0.000000]  modified: 0000000027ff0000 - 0000000027ff3000 (ACPI NVS) 
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.      
[    0.572442] ACPI: Invalid _PRS IRQ 0                                  
[    0.572682] ACPI: Invalid _PRS IRQ 0                                  
[    0.572913] ACPI: Invalid _PRS IRQ 0                                  
[    0.573142] ACPI: Invalid _PRS IRQ 0                                  
[    0.573369] ACPI: Invalid _PRS IRQ 0                                  
[    0.573600] ACPI: Invalid _PRS IRQ 0                                  
[    0.573827] ACPI: Invalid _PRS IRQ 0                                  
[    0.574058] ACPI: Invalid _PRS IRQ 0                                  
[    0.574285] ACPI: Invalid _PRS IRQ 0                                  
[    0.574515] ACPI: Invalid _PRS IRQ 0                                  
[    0.574745] ACPI: Invalid _PRS IRQ 0                                  
[    0.574973] ACPI: Invalid _PRS IRQ 0                                  
[    0.575203] ACPI: Invalid _PRS IRQ 0                                  
[    0.575430] ACPI: Invalid _PRS IRQ 0                                  
[    1.805555] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c0c0) ACPI=0x3f01f (20:600:0x13)
[    1.992379] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc600c0c0) ACPI=0x701f (60:60:0x1f)      
[    1.992383] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc600c0c0) ACPI=0x701f (60:60:0x1f)      
[    2.194994] rtc0: alarms up to one year, y3k, 242 bytes nvram                                                   
[    2.702683] nv_probe: set workaround bit for reversed mac addr                                                  
[    9.888306] agpgart: Detected NVIDIA nForce2 chipset                                                            
[    9.893547] agpgart-nvidia 0000:00:00.0: AGP aperture is 32M @ 0xe0000000                                       
[   10.839874] nvidia: module license 'NVIDIA' taints kernel.                                                      
[   11.115426] nvidia 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, high) -> IRQ 16                      
[   11.117566] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.10  Sat Jan 24 19:49:38 PST 2009                
[   20.242512] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge                                                         
[   20.242529] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode                                     
[   20.242587] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode                                             
[   48.777821] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge                                                         
[   48.777842] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode                                     
[   48.777909] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode                                             
[   76.309042] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge                                                         
[   76.309062] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode                                     
[   76.309126] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode                                             
[   88.453238] NVRM: vmap() failed to map pages!                                                                   
[   88.453973] NVRM: vmap() failed to map pages!                                                                   
[   88.454706] NVRM: vmap() failed to map pages!                                                                   
[   88.455439] NVRM: vmap() failed to map pages!                                                                   
[   88.456219] NVRM: vmap() failed to map pages!                                                                   
[   88.458408] NVRM: vmap() failed to map pages!                                                                   
[   88.459155] NVRM: vmap() failed to map pages!                                                                   
[   88.459892] NVRM: vmap() failed to map pages!                                                                   
[   88.460675] NVRM: vmap() failed to map pages!                                                                   
[   88.462546] NVRM: vmap() failed to map pages!                                                                   
[   88.463273] NVRM: vmap() failed to map pages!                                                                   
[   88.464057] NVRM: vmap() failed to map pages!                                                                   
[   88.465483] NVRM: vmap() failed to map pages!                                                                   
[   88.466207] NVRM: vmap() failed to map pages!                                                                   
[   88.466930] NVRM: vmap() failed to map pages!                                                                   
[   88.467658] NVRM: vmap() failed to map pages!                                                                   
[   88.468440] NVRM: vmap() failed to map pages!                                                                   
[   88.469941] NVRM: vmap() failed to map pages!                                                                   
[   88.470672] NVRM: vmap() failed to map pages!                                                                   
[   88.471404] NVRM: vmap() failed to map pages!                                                                   
[   88.472189] NVRM: vmap() failed to map pages!                                                                   
[   88.473589] NVRM: vmap() failed to map pages!                                                                   
[   88.474323] NVRM: vmap() failed to map pages!                                                                   
[   88.475056] NVRM: vmap() failed to map pages!                                                                   
[   88.475784] NVRM: vmap() failed to map pages!                                                                   
[   88.476562] NVRM: vmap() failed to map pages!                                                                   
[   88.478052] NVRM: vmap() failed to map pages!                                                                   
[   88.478785] NVRM: vmap() failed to map pages!                                                                   
[   88.479533] NVRM: vmap() failed to map pages!                                                                   
[   88.480307] NVRM: vmap() failed to map pages!                                                                   
[   88.481737] NVRM: vmap() failed to map pages!                                                                   
[   88.482468] NVRM: vmap() failed to map pages!                                                                   
[   88.483199] NVRM: vmap() failed to map pages!                                                                   
[   88.483930] NVRM: vmap() failed to map pages!                                                                   
[   88.485361] NVRM: vmap() failed to map pages!                                                                   
[   88.486094] NVRM: vmap() failed to map pages!                                                                   
[   88.486827] NVRM: vmap() failed to map pages!                                                                   
[   88.487560] NVRM: vmap() failed to map pages!                                                                   
[   88.488346] NVRM: vmap() failed to map pages!                                                                   
[   88.489845] NVRM: vmap() failed to map pages!                                                                   
[   88.490575] NVRM: vmap() failed to map pages!                                                                   
[   88.491309] NVRM: vmap() failed to map pages!                                                                   
[   88.492094] NVRM: vmap() failed to map pages!                                                                   
[   88.493557] NVRM: vmap() failed to map pages!                                                                   
[   88.494287] NVRM: vmap() failed to map pages!                                                                   
[   88.495014] NVRM: vmap() failed to map pages!                                                                   
[   88.495742] NVRM: vmap() failed to map pages!                                                                   
[   88.496527] NVRM: vmap() failed to map pages!                                                                   
[   88.498017] NVRM: vmap() failed to map pages!                                                                   
[   88.498751] NVRM: vmap() failed to map pages!                                                                   
[   88.499503] NVRM: vmap() failed to map pages!                                                                   
[   88.500288] NVRM: vmap() failed to map pages!                                                                   
[   88.501679] NVRM: vmap() failed to map pages!                                                                   
[   88.502414] NVRM: vmap() failed to map pages!                                                                   
[   88.503153] NVRM: vmap() failed to map pages!                                                                   
[   88.503885] NVRM: vmap() failed to map pages!                                                                   
[   88.504664] NVRM: vmap() failed to map pages!                                                                   
[   88.506146] NVRM: vmap() failed to map pages!                                                                   
[   88.506880] NVRM: vmap() failed to map pages!                                                                   
[   88.507617] NVRM: vmap() failed to map pages!                                                                   
[   88.508398] NVRM: vmap() failed to map pages!                                                                   
[   88.509786] NVRM: vmap() failed to map pages!                                                                   
[   88.510518] NVRM: vmap() failed to map pages!                                                                   
[   88.511252] NVRM: vmap() failed to map pages!                                                                   
[   88.511989] NVRM: vmap() failed to map pages!                                                                   
[   88.513431] NVRM: vmap() failed to map pages!                                                                   
[   88.514166] NVRM: vmap() failed to map pages!                                                                   
[   88.514902] NVRM: vmap() failed to map pages!                                                                   
[   88.515638] NVRM: vmap() failed to map pages!                                                                   
[   88.516423] NVRM: vmap() failed to map pages!                                                                   
[   88.517907] NVRM: vmap() failed to map pages!                                                                   
[   88.518636] NVRM: vmap() failed to map pages!                                                                   
[   88.519382] NVRM: vmap() failed to map pages!                                                                   
[   88.520168] NVRM: vmap() failed to map pages!                                                                   
[   88.521562] NVRM: vmap() failed to map pages!                                                                   
[   88.522298] NVRM: vmap() failed to map pages!                                                                   
[   88.523028] NVRM: vmap() failed to map pages!                                                                   
[   88.523758] NVRM: vmap() failed to map pages!                                                                   
[   88.524539] NVRM: vmap() failed to map pages!                                                                   
[   88.526006] NVRM: vmap() failed to map pages!                                                                   
[   88.526742] NVRM: vmap() failed to map pages!                                                                   
[   88.527477] NVRM: vmap() failed to map pages!                                                                   
[   88.528263] NVRM: vmap() failed to map pages!                                                                   
[   88.529721] NVRM: vmap() failed to map pages!                                                                   
[   88.530457] NVRM: vmap() failed to map pages!                                                                   
[   88.531193] NVRM: vmap() failed to map pages!                                                                   
[   88.531931] NVRM: vmap() failed to map pages!                                                                   
[   88.533369] NVRM: vmap() failed to map pages!                                                                   
[   88.534102] NVRM: vmap() failed to map pages!                                                                   
[   88.534833] NVRM: vmap() failed to map pages!                                                                   
[   88.535564] NVRM: vmap() failed to map pages!                                                                   
[   88.536344] NVRM: vmap() failed to map pages!                                                                   
[   88.537812] NVRM: vmap() failed to map pages!                                                                   
[   88.538552] NVRM: vmap() failed to map pages!                                                                   
[   88.539278] NVRM: vmap() failed to map pages!                                                                   
[   88.540056] NVRM: vmap() failed to map pages!                                                                   
[   88.541513] NVRM: vmap() failed to map pages!                                                                   
[   88.542244] NVRM: vmap() failed to map pages!                                                                   
[   88.542975] NVRM: vmap() failed to map pages!                                                                   
[   88.543706] NVRM: vmap() failed to map pages!                                                                   
[   88.544488] NVRM: vmap() failed to map pages!                                                                   
[   88.545969] NVRM: vmap() failed to map pages!                                                                   
[   88.546696] NVRM: vmap() failed to map pages!                                                                   
[   88.547422] NVRM: vmap() failed to map pages!                                                                   
[   88.548202] NVRM: vmap() failed to map pages!                                                                   
[   88.549606] NVRM: vmap() failed to map pages!                                                                   
[   88.550336] NVRM: vmap() failed to map pages!                                                                   
[   88.551067] NVRM: vmap() failed to map pages!                                                                   
[   88.551789] NVRM: vmap() failed to map pages!                                                                   
[   88.552563] NVRM: vmap() failed to map pages!                                                                   
[   88.554040] NVRM: vmap() failed to map pages!                                                                   
[   88.554770] NVRM: vmap() failed to map pages!                                                                   
[   88.555503] NVRM: vmap() failed to map pages!                                                                   
[   88.556284] NVRM: vmap() failed to map pages!                                                                   
[   88.557673] NVRM: vmap() failed to map pages!                                                                   
[   88.558420] NVRM: vmap() failed to map pages!                                                                   
[   88.559152] NVRM: vmap() failed to map pages!                                                                   
[   88.559887] NVRM: vmap() failed to map pages!                                                                   
[   88.560665] NVRM: vmap() failed to map pages!                                                                   
[   88.562137] NVRM: vmap() failed to map pages!                                                                   
[   88.562869] NVRM: vmap() failed to map pages!                                                                   
[   88.563602] NVRM: vmap() failed to map pages!                                                                   
[   88.564382] NVRM: vmap() failed to map pages!                                                                   
[   88.565763] NVRM: vmap() failed to map pages!                                                                   
[   88.566487] NVRM: vmap() failed to map pages!                                                                   
[   88.567212] NVRM: vmap() failed to map pages!                                                                   
[   88.567940] NVRM: vmap() failed to map pages!                                                                   
[   88.569375] NVRM: vmap() failed to map pages!                                                                   
[   88.570106] NVRM: vmap() failed to map pages!                                                                   
[   88.570837] NVRM: vmap() failed to map pages!                                                                   
[   88.571566] NVRM: vmap() failed to map pages!                                                                   
[   88.572348] NVRM: vmap() failed to map pages!                                                                   
[   88.573828] NVRM: vmap() failed to map pages!                                                                   
[   88.574560] NVRM: vmap() failed to map pages!                                                                   
[   88.575286] NVRM: vmap() failed to map pages!                                                                   
[   88.576060] NVRM: vmap() failed to map pages!                                                                   
[   88.577498] NVRM: vmap() failed to map pages!                                                                   
[   88.578243] NVRM: vmap() failed to map pages!                                                                   
[   88.578973] NVRM: vmap() failed to map pages!                                                                   
[   88.579703] NVRM: vmap() failed to map pages!                                                                   
[   88.580477] NVRM: vmap() failed to map pages!                                                                   
[   88.581946] NVRM: vmap() failed to map pages!                                                                   
[   88.582674] NVRM: vmap() failed to map pages!                                                                   
[   88.583405] NVRM: vmap() failed to map pages!                                                                   
[   88.584184] NVRM: vmap() failed to map pages!                                                                   
[   88.585617] NVRM: vmap() failed to map pages!                                                                   
[   88.586343] NVRM: vmap() failed to map pages!                                                                   
[   88.587072] NVRM: vmap() failed to map pages!                                                                   
[   88.587803] NVRM: vmap() failed to map pages!                                                                   
[   88.588600] NVRM: vmap() failed to map pages!                                                                   
[   88.590117] NVRM: vmap() failed to map pages!                                                                   
[   88.590872] NVRM: vmap() failed to map pages!                                                                   
[   88.591605] NVRM: vmap() failed to map pages!                                                                   
[   88.592386] NVRM: vmap() failed to map pages!                                                                   
[   88.593783] NVRM: vmap() failed to map pages!                                                                   
[   88.594506] NVRM: vmap() failed to map pages!                                                                   
[   88.595230] NVRM: vmap() failed to map pages!                                                                   
[   88.595957] NVRM: vmap() failed to map pages!                                                                   
[   88.597383] NVRM: vmap() failed to map pages!                                                                   
[   88.598128] NVRM: vmap() failed to map pages!                                                                   
[   88.598860] NVRM: vmap() failed to map pages!                                                                   
[   88.599589] NVRM: vmap() failed to map pages!                                                                   
[   88.600369] NVRM: vmap() failed to map pages!                                                                   
[   88.601852] NVRM: vmap() failed to map pages!                                                                   
[   88.602585] NVRM: vmap() failed to map pages!                                                                   
[   88.603316] NVRM: vmap() failed to map pages!                                                                   
[   88.604090] NVRM: vmap() failed to map pages!                                                                   
[   88.605477] NVRM: vmap() failed to map pages!                                                                   
[   88.606208] NVRM: vmap() failed to map pages!                                                                   
[   88.606939] NVRM: vmap() failed to map pages!                                                                   
[   88.607671] NVRM: vmap() failed to map pages!                                                                   
[   88.608463] NVRM: vmap() failed to map pages!                                                                   
[   88.609932] NVRM: vmap() failed to map pages!                                                                   
[   88.610660] NVRM: vmap() failed to map pages!                                                                   
[   88.611389] NVRM: vmap() failed to map pages!                                                                   
[   88.612168] NVRM: vmap() failed to map pages!                                                                   
[   88.613557] NVRM: vmap() failed to map pages!                                                                   
[   88.614289] NVRM: vmap() failed to map pages!                                                                   
[   88.615020] NVRM: vmap() failed to map pages!                                                                   
[   88.615752] NVRM: vmap() failed to map pages!                                                                   
[   88.616538] NVRM: vmap() failed to map pages!                                                                   
[   88.618032] NVRM: vmap() failed to map pages!                                                                   
[   88.618759] NVRM: vmap() failed to map pages!                                                                   
[   88.619488] NVRM: vmap() failed to map pages!                                                                   
[   88.620268] NVRM: vmap() failed to map pages!                                                                   
[   88.621658] NVRM: vmap() failed to map pages!                                                                   
[   88.622389] NVRM: vmap() failed to map pages!                                                                   
[   88.623114] NVRM: vmap() failed to map pages!                                                                   
[   88.623837] NVRM: vmap() failed to map pages!                                                                   
[   88.624617] NVRM: vmap() failed to map pages!                                                                   
[   88.626143] NVRM: vmap() failed to map pages!                                                                   
[   88.626875] NVRM: vmap() failed to map pages!                                                                   
[   88.627606] NVRM: vmap() failed to map pages!                                                                   
[   88.628398] NVRM: vmap() failed to map pages!                                                                   
[   88.629785] NVRM: vmap() failed to map pages!                                                                   
[   88.630517] NVRM: vmap() failed to map pages!                                                                   
[   88.631251] NVRM: vmap() failed to map pages!                                                                   
[   88.631981] NVRM: vmap() failed to map pages!                                                                   
[   88.633446] NVRM: vmap() failed to map pages!                                                                   
[   88.634176] NVRM: vmap() failed to map pages!                                                                   
[   88.634907] NVRM: vmap() failed to map pages!                                                                   
[   88.635639] NVRM: vmap() failed to map pages!                                                                   
[   88.636420] NVRM: vmap() failed to map pages!                                                                   
[   88.637953] NVRM: vmap() failed to map pages!                                                                   
[   88.638680] NVRM: vmap() failed to map pages!                                                                   
[   88.639408] NVRM: vmap() failed to map pages!                                                                   
[   88.640187] NVRM: vmap() failed to map pages!                                                                   
[   88.641577] NVRM: vmap() failed to map pages!                                                                   
[   88.642308] NVRM: vmap() failed to map pages!                                                                   
[   88.643037] NVRM: vmap() failed to map pages!                                                                   
[   88.643768] NVRM: vmap() failed to map pages!                                                                   
[   88.644551] NVRM: vmap() failed to map pages!                                                                   
[   88.646035] NVRM: vmap() failed to map pages!                                                                   
[   88.646760] NVRM: vmap() failed to map pages!                                                                   
[   88.647490] NVRM: vmap() failed to map pages!                                                                   
[   88.648296] NVRM: vmap() failed to map pages!                                                                   
[   88.649687] NVRM: vmap() failed to map pages!                                                                   
[   88.650417] NVRM: vmap() failed to map pages!                                                                   
[   88.651145] NVRM: vmap() failed to map pages!                                                                   
[   88.651869] NVRM: vmap() failed to map pages!                                                                   
[   88.652640] NVRM: vmap() failed to map pages!                                                                   
[   88.654113] NVRM: vmap() failed to map pages!                                                                   
[   88.654845] NVRM: vmap() failed to map pages!                                                                   
[   88.655577] NVRM: vmap() failed to map pages!                                                                   
[   88.656356] NVRM: vmap() failed to map pages!                                                                   
[   88.657760] NVRM: vmap() failed to map pages!                                                                   
[   88.658492] NVRM: vmap() failed to map pages!                                                                   
[   88.659224] NVRM: vmap() failed to map pages!                                                                   
[   88.659959] NVRM: vmap() failed to map pages!                                                                   
[   88.661375] NVRM: vmap() failed to map pages!                                                                   
[   88.662103] NVRM: vmap() failed to map pages!                                                                   
[   88.662833] NVRM: vmap() failed to map pages!                                                                   
[   88.663564] NVRM: vmap() failed to map pages!                                                                   
[   88.664346] NVRM: vmap() failed to map pages!                                                                   
[   88.665814] NVRM: vmap() failed to map pages!                                                                   
[   88.666537] NVRM: vmap() failed to map pages!                                                                   
[   88.667265] NVRM: vmap() failed to map pages!                                                                   
[   88.668053] NVRM: vmap() failed to map pages!                                                                   
[   88.669442] NVRM: vmap() failed to map pages!                                                                   
[   88.670173] NVRM: vmap() failed to map pages!                                                                   
[   88.670903] NVRM: vmap() failed to map pages!                                                                   
[   88.671633] NVRM: vmap() failed to map pages!                                                                   
[   88.672413] NVRM: vmap() failed to map pages!                                                                   
[   88.673946] NVRM: vmap() failed to map pages!                                                                   
[   88.674678] NVRM: vmap() failed to map pages!                                                                   
[   88.675405] NVRM: vmap() failed to map pages!                                                                   
[   88.676182] NVRM: vmap() failed to map pages!                                                                   
[   88.677585] NVRM: vmap() failed to map pages!                                                                   
[   88.678316] NVRM: vmap() failed to map pages!                                                                   
[   88.679048] NVRM: vmap() failed to map pages!                                                                   
[   88.679777] NVRM: vmap() failed to map pages!                                                                   
[   88.680551] NVRM: vmap() failed to map pages!                                                                   
[   88.682079] NVRM: vmap() failed to map pages!                                                                   
[   88.682808] NVRM: vmap() failed to map pages!                                                                   
[   88.683537] NVRM: vmap() failed to map pages!                                                                   
[   88.684317] NVRM: vmap() failed to map pages!                                                                   
[   88.685755] NVRM: vmap() failed to map pages!                                                                   
[   88.686484] NVRM: vmap() failed to map pages!                                                                   
[   88.687213] NVRM: vmap() failed to map pages!                                                                   
[   88.687961] NVRM: vmap() failed to map pages!                                                                   
[   88.689383] NVRM: vmap() failed to map pages!                                                                   
[   88.690110] NVRM: vmap() failed to map pages!                                                                   
[   88.690842] NVRM: vmap() failed to map pages!                                                                   
[   88.691571] NVRM: vmap() failed to map pages!                                                                   
[   88.692352] NVRM: vmap() failed to map pages!                                                                   
[   88.693829] NVRM: vmap() failed to map pages!                                                                   
[   88.694552] NVRM: vmap() failed to map pages!                                                                   
[   88.695276] NVRM: vmap() failed to map pages!                                                                   
[   88.696055] NVRM: vmap() failed to map pages!                                                                   
[   88.697457] NVRM: vmap() failed to map pages!                                                                   
[   88.698189] NVRM: vmap() failed to map pages!                                                                   
[   88.698917] NVRM: vmap() failed to map pages!                                                                   
[   88.699648] NVRM: vmap() failed to map pages!                                                                   
[   88.700427] NVRM: vmap() failed to map pages!                                                                   
[   88.701909] NVRM: vmap() failed to map pages!                                                                   
[   88.702643] NVRM: vmap() failed to map pages!                                                                   
[   88.703372] NVRM: vmap() failed to map pages!                                                                   
[   88.704146] NVRM: vmap() failed to map pages!                                                                   
[   88.705540] NVRM: vmap() failed to map pages!                                                                   
[   88.706285] NVRM: vmap() failed to map pages!                                                                   
[   88.707016] NVRM: vmap() failed to map pages!                                                                   
[   88.707763] NVRM: vmap() failed to map pages!                                                                   
[   88.708536] NVRM: vmap() failed to map pages!                                                                   
[   88.710002] NVRM: vmap() failed to map pages!                                                                   
[   88.710730] NVRM: vmap() failed to map pages!                                                                   
[   88.711460] NVRM: vmap() failed to map pages!                                                                   
[   88.712240] NVRM: vmap() failed to map pages!                                                                   
[   88.713628] NVRM: vmap() failed to map pages!                                                                   
[   88.714360] NVRM: vmap() failed to map pages!                                                                   
[   88.715093] NVRM: vmap() failed to map pages!                                                                   
[   88.715825] NVRM: vmap() failed to map pages!                                                                   
[   88.716609] NVRM: vmap() failed to map pages!                                                                   
[   88.718142] NVRM: vmap() failed to map pages!                                                                   
[   88.718870] NVRM: vmap() failed to map pages!                                                                   
[   88.719604] NVRM: vmap() failed to map pages!                                                                   
[   88.720385] NVRM: vmap() failed to map pages!                                                                   
[   88.721773] NVRM: vmap() failed to map pages!                                                                   
[   88.722501] NVRM: vmap() failed to map pages!                                                                   
[   88.723225] NVRM: vmap() failed to map pages!                                                                   
[   88.723951] NVRM: vmap() failed to map pages!                                                                   
[   88.725377] NVRM: vmap() failed to map pages!                                                                   
[   88.726106] NVRM: vmap() failed to map pages!                                                                   
[   88.726838] NVRM: vmap() failed to map pages!                                                                   
[   88.727584] NVRM: vmap() failed to map pages!                                                                   
[   88.728365] NVRM: vmap() failed to map pages!                                                                   
[   88.729900] NVRM: vmap() failed to map pages!                                                                   
[   88.730632] NVRM: vmap() failed to map pages!                                                                   
[   88.731364] NVRM: vmap() failed to map pages!                                                                   
[   88.732139] NVRM: vmap() failed to map pages!                                                                   
[   88.733569] NVRM: vmap() failed to map pages!                                                                   
[   88.734300] NVRM: vmap() failed to map pages!                                                                   
[   88.735030] NVRM: vmap() failed to map pages!                                                                   
[   88.735761] NVRM: vmap() failed to map pages!                                                                   
[   88.736541] NVRM: vmap() failed to map pages!                                                                   
[   88.738020] NVRM: vmap() failed to map pages!                                                                   
[   88.738749] NVRM: vmap() failed to map pages!                                                                   
[   88.739478] NVRM: vmap() failed to map pages!                                                                   
[   88.740258] NVRM: vmap() failed to map pages!                                                                   
[   88.741648] NVRM: vmap() failed to map pages!                                                                   
[   88.742377] NVRM: vmap() failed to map pages!                                                                   
[   88.743108] NVRM: vmap() failed to map pages!                                                                   
[   88.743840] NVRM: vmap() failed to map pages!                                                                   
[   88.744624] NVRM: vmap() failed to map pages!                                                                   
[   88.746103] NVRM: vmap() failed to map pages!                                                                   
[   88.746843] NVRM: vmap() failed to map pages!                                                                   
[   88.747571] NVRM: vmap() failed to map pages!                                                                   
[   88.748352] NVRM: vmap() failed to map pages!                                                                   
[   88.749740] NVRM: vmap() failed to map pages!                                                                   
[   88.750472] NVRM: vmap() failed to map pages!                                                                   
[   88.751198] NVRM: vmap() failed to map pages!                                                                   
[   88.751922] NVRM: vmap() failed to map pages!                                                                   
[   88.753343] NVRM: vmap() failed to map pages!                                                                   
[   88.754073] NVRM: vmap() failed to map pages!                                                                   
[   88.754804] NVRM: vmap() failed to map pages!                                                                   
[   88.755534] NVRM: vmap() failed to map pages!                                                                   
[   88.756314] NVRM: vmap() failed to map pages!                                                                   
[   88.757808] NVRM: vmap() failed to map pages!                                                                   
[   88.758540] NVRM: vmap() failed to map pages!                                                                   
[   88.759273] NVRM: vmap() failed to map pages!                                                                   
[   88.760054] NVRM: vmap() failed to map pages!                                                                   
[   88.761432] NVRM: vmap() failed to map pages!                                                                   
[   88.762162] NVRM: vmap() failed to map pages!                                                                   
[   88.762894] NVRM: vmap() failed to map pages!                                                                   
[   88.763641] NVRM: vmap() failed to map pages!                                                                   
[   88.764424] NVRM: vmap() failed to map pages!                                                                   
[   88.765941] NVRM: vmap() failed to map pages!                                                                   
[   88.766666] NVRM: vmap() failed to map pages!                                                                   
[   88.767407] NVRM: vmap() failed to map pages!                                                                   
[   88.768184] NVRM: vmap() failed to map pages!                                                                   
[   88.769573] NVRM: vmap() failed to map pages!                                                                   
[   88.770304] NVRM: vmap() failed to map pages!                                                                   
[   88.771035] NVRM: vmap() failed to map pages!                                                                   
[   88.771768] NVRM: vmap() failed to map pages!                                                                   
[   88.772550] NVRM: vmap() failed to map pages!                                                                   
[   88.774032] NVRM: vmap() failed to map pages!                                                                   
[   88.774759] NVRM: vmap() failed to map pages!                                                                   
[   88.775485] NVRM: vmap() failed to map pages!                                                                   
[   88.776262] NVRM: vmap() failed to map pages!                                                                   
[   88.777739] NVRM: vmap() failed to map pages!                                                                   
[   88.778472] NVRM: vmap() failed to map pages!                                                                   
[   88.779202] NVRM: vmap() failed to map pages!                                                                   
[   88.779926] NVRM: vmap() failed to map pages!                                                                   
[   88.781347] NVRM: vmap() failed to map pages!                                                                   
[   88.782076] NVRM: vmap() failed to map pages!                                                                   
[   88.782805] NVRM: vmap() failed to map pages!                                                                   
[   88.783536] NVRM: vmap() failed to map pages!                                                                   
[   88.784318] NVRM: vmap() failed to map pages!                                                                   
[   88.785798] NVRM: vmap() failed to map pages!                                                                   
[   88.786545] NVRM: vmap() failed to map pages!                                                                   
[   88.787277] NVRM: vmap() failed to map pages!                                                                   
[   88.788058] NVRM: vmap() failed to map pages!                                                                   
[   88.789438] NVRM: vmap() failed to map pages!                                                                   
[   88.790164] NVRM: vmap() failed to map pages!                                                                   
[   88.790893] NVRM: vmap() failed to map pages!                                                                   
[   88.791625] NVRM: vmap() failed to map pages!                                                                   
[   88.792404] NVRM: vmap() failed to map pages!                                                                   
[   88.793877] NVRM: vmap() failed to map pages!                                                                   
[   88.794601] NVRM: vmap() failed to map pages!                                                                   
[   88.795327] NVRM: vmap() failed to map pages!                                                                   
[   88.796105] NVRM: vmap() failed to map pages!                                                                   
[   88.797504] NVRM: vmap() failed to map pages!                                                                   
[   88.798237] NVRM: vmap() failed to map pages!                                                                   
[   88.798968] NVRM: vmap() failed to map pages!                                                                   
[   88.799699] NVRM: vmap() failed to map pages!                                                                   
[   88.800483] NVRM: vmap() failed to map pages!                                                                   
[   88.801964] NVRM: vmap() failed to map pages!                                                                   
[   88.802695] NVRM: vmap() failed to map pages!                                                                   
[   88.803422] NVRM: vmap() failed to map pages!                                                                   
[   88.804197] NVRM: vmap() failed to map pages!                                                                   
[   88.805583] NVRM: vmap() failed to map pages!                                                                   
[   88.806313] NVRM: vmap() failed to map pages!                                                                   
[   88.807061] NVRM: vmap() failed to map pages!                                                                   
[   88.807790] NVRM: vmap() failed to map pages!                                                                   
[   88.808564] NVRM: vmap() failed to map pages!                                                                   
[   88.810037] NVRM: vmap() failed to map pages!                                                                   
[   88.810767] NVRM: vmap() failed to map pages!                                                                   
[   88.811497] NVRM: vmap() failed to map pages!                                                                   
[   88.812277] NVRM: vmap() failed to map pages!                                                                   
[   88.813713] NVRM: vmap() failed to map pages!                                                                   
[   88.814445] NVRM: vmap() failed to map pages!                                                                   
[   88.815176] NVRM: vmap() failed to map pages!                                                                   
[   88.815907] NVRM: vmap() failed to map pages!                                                                   
[   88.817348] NVRM: vmap() failed to map pages!                                                                   
[   88.818074] NVRM: vmap() failed to map pages!                                                                   
[   88.818801] NVRM: vmap() failed to map pages!                                                                   
[   88.819533] NVRM: vmap() failed to map pages!                                                                   
[   88.820316] NVRM: vmap() failed to map pages!                                                                   
[   88.821810] NVRM: vmap() failed to map pages!                                                                   
[   88.822535] NVRM: vmap() failed to map pages!                                                                   
[   88.823260] NVRM: vmap() failed to map pages!                                                                   
[   88.823987] NVRM: vmap() failed to map pages!                                                                   
[   88.825488] NVRM: vmap() failed to map pages!                                                                   
[   88.826234] NVRM: vmap() failed to map pages!                                                                   
[   88.826965] NVRM: vmap() failed to map pages!                                                                   
[   88.827698] NVRM: vmap() failed to map pages!                                                                   
[   88.828477] NVRM: vmap() failed to map pages!                                                                   
[   88.829960] NVRM: vmap() failed to map pages!                                                                   
[   88.830693] NVRM: vmap() failed to map pages!                                                                   
[   88.831426] NVRM: vmap() failed to map pages!                                                                   
[   88.832200] NVRM: vmap() failed to map pages!                                                                   
[   88.833585] NVRM: vmap() failed to map pages!                                                                   
[   88.834317] NVRM: vmap() failed to map pages!                                                                   
[   88.835050] NVRM: vmap() failed to map pages!                                                                   
[   88.835781] NVRM: vmap() failed to map pages!                                                                   
[   88.836569] NVRM: vmap() failed to map pages!                                                                   
[   88.838035] NVRM: vmap() failed to map pages!                                                                   
[   88.838764] NVRM: vmap() failed to map pages!                                                                   
[   88.839493] NVRM: vmap() failed to map pages!                                                                   
[   88.840272] NVRM: vmap() failed to map pages!                                                                   
[   88.841662] NVRM: vmap() failed to map pages!                                                                   
[   88.842394] NVRM: vmap() failed to map pages!                                                                   
[   88.843126] NVRM: vmap() failed to map pages!                                                                   
[   88.843857] NVRM: vmap() failed to map pages!                                                                   
[   88.844636] NVRM: vmap() failed to map pages!                                                                   
[   88.846131] NVRM: vmap() failed to map pages!                                                                   
[   88.846856] NVRM: vmap() failed to map pages!                                                                   
[   88.847584] NVRM: vmap() failed to map pages!                                                                   
[   88.848365] NVRM: vmap() failed to map pages!                                                                   
[   88.849758] NVRM: vmap() failed to map pages!                                                                   
[   88.850489] NVRM: vmap() failed to map pages!                                                                   
[   88.851213] NVRM: vmap() failed to map pages!                                                                   
[   88.851938] NVRM: vmap() failed to map pages!                                                                   
[   88.853359] NVRM: vmap() failed to map pages!                                                                   
[   88.854088] NVRM: vmap() failed to map pages!                                                                   
[   88.854818] NVRM: vmap() failed to map pages!                                                                   
[   88.855549] NVRM: vmap() failed to map pages!                                                                   
[   88.856341] NVRM: vmap() failed to map pages!                                                                   
[   88.857821] NVRM: vmap() failed to map pages!                                                                   
[   88.858551] NVRM: vmap() failed to map pages!                                                                   
[   88.859285] NVRM: vmap() failed to map pages!                                                                   
[   88.860065] NVRM: vmap() failed to map pages!                                                                   
[   88.861494] NVRM: vmap() failed to map pages!                                                                   
[   88.862224] NVRM: vmap() failed to map pages!                                                                   
[   88.862954] NVRM: vmap() failed to map pages!                                                                   
[   88.863684] NVRM: vmap() failed to map pages!                                                                   
[   88.864463] NVRM: vmap() failed to map pages!                                                                   
[   88.865943] NVRM: vmap() failed to map pages!                                                                   
[   88.866667] NVRM: vmap() failed to map pages!                                                                   
[   88.867396] NVRM: vmap() failed to map pages!                                                                   
[   88.868174] NVRM: vmap() failed to map pages!                                                                   
[   88.869610] NVRM: vmap() failed to map pages!                                                                   
[   88.870338] NVRM: vmap() failed to map pages!                                                                   
[   88.871069] NVRM: vmap() failed to map pages!                                                                   
[   88.871799] NVRM: vmap() failed to map pages!                                                                   
[   88.872580] NVRM: vmap() failed to map pages!                                                                   
[   88.874110] NVRM: vmap() failed to map pages!                                                                   
[   88.874836] NVRM: vmap() failed to map pages!                                                                   
[   88.875561] NVRM: vmap() failed to map pages!                                                                   
[   88.876355] NVRM: vmap() failed to map pages!                                                                   
[   88.877741] NVRM: vmap() failed to map pages!                                                                   
[   88.878472] NVRM: vmap() failed to map pages!                                                                   
[   88.879216] NVRM: vmap() failed to map pages!                                                                   
[   88.879941] NVRM: vmap() failed to map pages!                                                                   
[   88.881361] NVRM: vmap() failed to map pages!                                                                   
[   88.882089] NVRM: vmap() failed to map pages!                                                                   
[   88.882818] NVRM: vmap() failed to map pages!                                                                   
[   88.883548] NVRM: vmap() failed to map pages!                                                                   
[   88.884327] NVRM: vmap() failed to map pages!                                                                   
[   88.885806] NVRM: vmap() failed to map pages!                                                                   
[   88.886535] NVRM: vmap() failed to map pages!                                                                   
[   88.887264] NVRM: vmap() failed to map pages!                                                                   
[   88.887999] NVRM: vmap() failed to map pages!                                                                   
[   88.889410] NVRM: vmap() failed to map pages!                                                                   
[   88.890137] NVRM: vmap() failed to map pages!                                                                   
[   88.890868] NVRM: vmap() failed to map pages!                                                                   
[   88.891599] NVRM: vmap() failed to map pages!                                                                   
[   88.892381] NVRM: vmap() failed to map pages!                                                                   
[   88.893839] NVRM: vmap() failed to map pages!                                                                   
[   88.894562] NVRM: vmap() failed to map pages!                                                                   
[   88.895287] NVRM: vmap() failed to map pages!                                                                   
[   88.896076] NVRM: vmap() failed to map pages!                                                                   
[   88.897459] NVRM: vmap() failed to map pages!                                                                   
[   88.898189] NVRM: vmap() failed to map pages!                                                                   
[   88.898918] NVRM: vmap() failed to map pages!                                                                   
[   88.899649] NVRM: vmap() failed to map pages!                                                                   
[   88.900429] NVRM: vmap() failed to map pages!                                                                   
[   88.901895] NVRM: vmap() failed to map pages!                                                                   
[   88.902627] NVRM: vmap() failed to map pages!                                                                   
[   88.903353] NVRM: vmap() failed to map pages!                                                                   
[   88.904127] NVRM: vmap() failed to map pages!                                                                   
[   88.905504] NVRM: vmap() failed to map pages!                                                                   
[   88.906252] NVRM: vmap() failed to map pages!                                                                   
[   88.907005] NVRM: vmap() failed to map pages!                                                                   
[   88.907732] NVRM: vmap() failed to map pages!   
```

The cmd  dmesg |grep -i xid  output nothing.

The cmd dmesg |grep -i nvidia gave me:

```
 dburke@Lucy:~$ dmesg |grep -i nvidia
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    9.888306] agpgart: Detected NVIDIA nForce2 chipset            
[    9.893547] agpgart-nvidia 0000:00:00.0: AGP aperture is 32M @ 0xe0000000
[   10.839874] nvidia: module license 'NVIDIA' taints kernel.               
[   11.115426] nvidia 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, high) -> IRQ 16
[   11.117566] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.10  Sat Jan 24 19:49:38 PST 2009
[   20.242512] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge                                         
[   20.242529] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode                     
[   20.242587] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode                             
[   48.777821] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge                                         
[   48.777842] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode                     
[   48.777909] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode
[   76.309042] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
[   76.309062] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
[   76.309126] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode
```


Could this be why my xgl isn't enabled?

```
dburke@Lucy:~$ apt-cache policy xserver-xgl
W: Unable to locate package xserver-xgl
```

The cmd glxinfo |grep direct :

```
dburke@Lucy:~$ glxinfo |grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

---

### Post by DyBurke on 2009-06-26
Nobody is even going to brainstorm?  Please.  Ideas.  Anything that will keep progress going.... Gah!

---

### Post by ivanvajar on 2009-06-26
You need to enable drivers in System/Administration/Hardware drivers
You are using VESA drivers at this point and it will not do. Jaunty has a nice option in System/Administration/NVIDIA x server settings, but you need to enable proprietary drivers first.

---

### Post by DyBurke on 2009-06-26
> **ivanvajar said:**
> You need to enable drivers in System/Administration/Hardware drivers
You are using VESA drivers at this point and it will not do. Jaunty has a nice option in System/Administration/NVIDIA x server settings, but you need to enable proprietary drivers first.


Did you read my post?  I activated the nvidia driver using the System>Administration/Hardware Drivers already.  It says it's activated.  The cmd lshw shows that my graphics device is indeed using the "nvidia" driver, as does my xorg config.

The only thing that says I'm not using the "nvidia" driver is compiz-check and nvidia-settings when I run it.  Maybe it's set to nvidia, but since the xserver crashes so many times it searches for a driver available that will work or otherwise just ends up defaulting to the "vesa" driver in order to run in low graphics mode?

Thanks for trying, but I don't think that's going to help.  I've tried it with many different variables... :(

---

### Post by 4Orbs on 2009-06-26
If it were me, the next step would be to force nvidia to write a new xorg.conf by entering in terminal (root is necessary):
```
sudo nvidia-xconfig
```
But before doing that I would set the screen resolution and refresh rate back to Auto or Default, and turn off desktop effects.

Reboot after entering command. Maybe fixed, maybe not.

---

### Post by DyBurke on 2009-06-26
> **4Orbs said:**
> If it were me, the next step would be to force nvidia to write a new xorg.conf by entering in terminal:
```
nvidia-xconfig
```But before doing that I would set the screen resolution and refresh rate back to Auto or Default, and turn off desktop effects.

Reboot. Maybe fixed, maybe not.


How would I set the screen resolution and refresh rate to Auto or Default?  Do you know the syntax?  Sorry, I'm still new to the scene. :P

btw, I updated my post with more info if that helps.

---

### Post by 4Orbs on 2009-06-26
Edited my post too. I was just guessing that you may have changed your resolution before activating the driver. You would have done that from the Admin->Preferences->Display menu. If you are still set at whatever resolution was default after installation, then it shouldn't be a problem. If you don't have the Auto or Default option in the Display settings, I believe Ubuntu defaults to the highest resolution available (with the nv driver).

---

### Post by DyBurke on 2009-06-26
> **4Orbs said:**
> Edited my post too. I was just guessing that you may have changed your resolution before activating the driver. You would have done that from the Admin->Preferences->Display menu. If you are still set at whatever resolution was default after installation, then it shouldn't be a problem. If you don't have the Auto or Default option in the Display settings, I believe Ubuntu defaults to the highest resolution available (with the nv driver).

After running "Display" I receive the message, "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"  If I select yes, it takes me to nvidia-settings and I can't the previous error message telling me that I'm not using the nvidia driver.  If I select no, Display runs and has no Auto or Default options.  The resolution at startup was 800x600.  Through my tinkering I've managed to get it to 1024x768, but the refresh rate is set at 0hz and has no other options available.


I ran sudo nvidia-xconfig within the gui and got:

```
dburke@Lucy:~$ sudo nvidia-xconfig                                                                      
[sudo] password for dburke:                                                                             

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout; using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

My xorg.config now looks like this:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Sat Jan 24 20:04:42 PST 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

I will restart the xserver and see what happens, then post back.  If that doesn't work, maybe stopping gdm and the xserver before doing that is a good idea?  I think I've done that, but I would be willing to try again.  Don't know why I got all the errors from nvidia-xconfig, but most of them seem irrelivant to my problem.

---

### Post by 4Orbs on 2009-06-26
It looks ok. After reboot you should be able to change resolution with the nvidia Settings Mgr as root. If it does work, check out the effects before changing from the default resolution imposed by the driver.

---

### Post by DyBurke on 2009-06-26
Bah!  It didn't work. :(  Should I try stopping the xserver and gdm before running nvidia-xconfig?  Hm.  Not sure what to do.

In any case, thank you so much 4Orbs.  Just giving me ideas is really helping me widdle possibilities down.

btw, I tried to add the following section to my xorg.config to see if I could get the xserver restart keyboard shortcut functionality back, but that doesn't seem to be working, either.  Maybe xserver isn't using xorg.conf, or I messed up the syntax?  

```
Section "ServerFlags"
    Option         "DontZap" "false"
EndSection
```




Uuuug.......

---

### Post by DyBurke on 2009-06-26
> **4Orbs said:**
> It looks ok. After reboot you should be able to change resolution with the nvidia Settings Mgr as root. If it does work, check out the effects before changing from the default resolution imposed by the driver.


Still gives me the message, "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

:(

What I really don't understand is why compiz-check thinks I'm using the vesa driver?  lshw, Hardware Drivers and my xorg.conf say I'm using "nvidia".  Fishy, indeed.  I would assume that's related to me being in "low-graphics mode", but I don't actually know.

---

### Post by 4Orbs on 2009-06-26
Your Ubuntu is installed on real partitions, not Wubi or Virtualbox? You can't activate the drivers in a vm.

---

### Post by 4Orbs on 2009-06-26
I don't use the nvidia Settings Mgr because I can never get the Login Screen resolution to agree with my desktop resolution. It looks to me like you have the nvidia driver activated. I think just editing the xorg.conf and rebooting should get you running smooth. If you want to rename your current /etc/X11/xorg.conf to xorg.conf-backup2 then paste the below as the new xorg.conf (as root) it might work. But first change the "Modes" line resolutions to those you know work with your nvidia card. The first entry should be the highest res and it will also be the default resolution after you reboot.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
SubSection "Display"
Depth 24
Modes "1152x864" "1024x768" "800x600"
EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



```

---

### Post by DyBurke on 2009-06-26
> **4Orbs said:**
> Your Ubuntu is installed on real partitions, not Wubi or Virtualbox? You can't activate the drivers in a vm.


haha No, I'm not running it in a vm.  It's on a real partition. :)

---

### Post by DyBurke on 2009-06-26
> **4Orbs said:**
> I don't use the nvidia Settings Mgr because I can never get the Login Screen resolution to agree with my desktop resolution. It looks to me like you have the nvidia driver activated. I think just editing the xorg.conf and rebooting should get you running smooth. If you want to rename your current /etc/X11/xorg.conf to xorg.conf-backup2 then paste the below as the new xorg.conf (as root) it might work. But first change the "Modes" line resolutions to those you know work with your nvidia card. The first entry should be the highest res and it will also be the default resolution after you reboot.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
SubSection "Display"
Depth 24
Modes "1152x864" "1024x768" "800x600"
EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection



```


Still no luck. :(  The only resolutions I included were 1024x768 and 800x600, which I know for a fact my card and monitor can do, not to mention I'm able to switch between those resolutions now.

I'm thinking I need to look more towards boot and see what's happening.  I'm pretty new to unix based systems so it's difficult to find info on the boot for me, but if you have any suggestions for cmds that will give me more info to look through, that would be amazing.  Thanks again for all the effort you're putting into this 4Orbs. :)

---

### Post by 4Orbs on 2009-06-26
So, to clarify... you still have to log in to low graphics mode, but you can switch between the two resolutions you included in the conf file? When you go to the Hardware Drivers Mgr, does it show the driver is activated but not in use?

---

### Post by DyBurke on 2009-06-27
> **4Orbs said:**
> So, to clarify... you still have to log in to low graphics mode, but you can switch between the two resolutions you included in the conf file? When you go to the Hardware Drivers Mgr, does it show the driver is activated but not in use?


I still have to log in to low graphics mode, yes.  Regardless of whether or not the resolutions were specified in the xorg config, I was able to switch between 1024x768 and 800x600.  That has always been possible.  But because I can't get it not to start up in low graphics mode, I can't get desktop effects enabled and can't specify any more resolutions in xorg.conf or use nvidia-settings to configure anything, nor can I use System>Preferences>Display to configure my settings since it says my card doesn't have the proper extentions. 

Hardware Drivers shows the nvidia (version 96) driver as activated and in use.  It is the only driver option available through that app.

Too me, it's all very baffling....

When it asks if I would like to start this one session in low graphics mode, there is also an option to troubleshoot the error.  It gives me options to look at the same files I've been looking at Xorg.0.log, xorg.conf, etc.  But it seems to be pretty different logs and oddly enough, logs without errors it seems.  I can't find anything that looks like something went wrong!  GAH!@ I'm about to update and post the results of those logs.

What appears to be the first log recorded:

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Lucy 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 27 08:29:44 2009
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

(--) PCI:*(0@2:0:0) nVidia Corporation NV18 [GeForce4 MX - nForce GPU] rev 163, Mem @ 0xe2000000/16777216, 0xd0000000/134217728, 0xd8000000/524288, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) NVIDIA GLX Module  96.43.10  Sat Jan 24 20:04:30 PST 2009
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
(II) NVIDIA dlloader X Driver  96.43.10  Sat Jan 24 19:52:47 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX Integrated GPU at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.1f.00.08.09
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX Integrated GPU at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     FNI (CRT-0)
(--) NVIDIA(0): FNI (CRT-0): 300.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (63, 75); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
 ddxSigGiveUp: Closing log
```
What appears to be the first time xserver tries to start?

```
 3144 2744
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Lucy 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Sat Jun 27 08:30:00 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
3144 2744
```Don't know how relevant these ones are, but here they are...

lspci-wnn:

```
00:00.0 Host bridge [0600]: nVidia Corporation nForce2 IGP2 [10de:01e0] (rev a2)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=32M]
    Capabilities: [40] AGP version 2.0
        Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
        Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP+ GART64- 64bit- FW- Rate=x4
    Capabilities: [60] HyperTransport: Host or Secondary Interface
        Command: WarmRst+ DblEnd-
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
        Link Config: MLWI=8bit MLWO=8bit LWI=8bit LWO=8bit
        Revision ID: 0.16
    Kernel driver in use: agpgart-nvidia
    Kernel modules: nvidia-agp

00:00.1 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 1 [10de:01eb] (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.2 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 4 [10de:01ee] (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.3 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 3 [10de:01ed] (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.4 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 2 [10de:01ec] (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.5 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 5 [10de:01ef] (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.0 ISA bridge [0601]: nVidia Corporation nForce2 ISA Bridge [10de:0060] (rev a4)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [48] HyperTransport: Slave or Primary Interface
        Command: BaseUnitID=1 UnitCnt=15 MastHost- DefDir-
        Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC+ TXO- <CRCErr=0
        Link Config 0: MLWI=8bit MLWO=8bit LWI=8bit LWO=8bit
        Link Control 1: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO+ <CRCErr=0
        Link Config 1: MLWI=8bit MLWO=8bit LWI=8bit LWO=8bit
        Revision ID: 0.00

00:01.1 SMBus [0c05]: nVidia Corporation nForce2 SMBus (MCP) [10de:0064] (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: I/O ports at e400 [size=32]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller [10de:0067] (rev a4) (prog-if 10)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at e5080000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller [10de:0067] (rev a4) (prog-if 10)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 20
    Region 0: Memory at e5083000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ohci_hcd

00:02.2 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller [10de:0068] (rev a4) (prog-if 20)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin C routed to IRQ 22
    Region 0: Memory at e5086000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=0080
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller [0200]: nVidia Corporation nForce2 Ethernet Controller [10de:0066] (rev a1)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at e5087000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at d000 [size=8]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable+ DSel=0 DScale=0 PME-
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:05.0 Multimedia audio controller [0401]: nVidia Corporation nForce Audio Processing Unit [10de:006b] (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (250ns min, 3000ns max)
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at e5000000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce2 AC97 Audio Controler (MCP) [10de:006a] (rev a1)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (500ns min, 1250ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at d400 [size=256]
    Region 1: I/O ports at d800 [size=128]
    Region 2: Memory at e5081000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:08.0 PCI bridge [0604]: nVidia Corporation nForce2 External PCI Bridge [10de:006c] (rev a3)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: e4000000-e4ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:09.0 IDE interface [0101]: nVidia Corporation nForce2 IDE [10de:0065] (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: Device [f509:904d]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    Region 4: I/O ports at f000 [size=16]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: pata_amd

00:1e.0 PCI bridge [0604]: nVidia Corporation nForce2 AGP [10de:01e8] (rev a2)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    Memory behind bridge: e2000000-e3ffffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

01:07.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Linksys Device [1737:0013]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 10
    Region 0: Memory at e4010000 (32-bit, non-prefetchable) [size=8K]
    Kernel modules: ssb

01:08.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20]
    Subsystem: Conexant Systems, Inc. Device [14f1:2000]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at e4000000 (32-bit, non-prefetchable) [size=64K]
    Region 1: I/O ports at c000 [size=8]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:00.0 VGA compatible controller [0300]: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] [10de:01f0] (rev a3)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:904d]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 248 (1250ns min, 250ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Region 2: Memory at d8000000 (32-bit, prefetchable) [size=512K]
    [virtual] Expansion ROM at d8080000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [44] AGP version 2.0
        Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
        Command: RQ=32 ArqSz=0 Cal=0 SBA- AGP+ GART64- 64bit- FW- Rate=x4
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb, rivafb

```xrandr-verbose:

```
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 (0x44) normal (normal) 0mm x 0mm
    Identifier: 0x43
    Timestamp:  91924
    Subpixel:   no subpixels
    Clones:    
    CRTC:       0
    CRTCs:      0
    Panning:    0x0+0+0
    Tracking:   0x0+0+0
    Border:     0/0/0/0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  1024x768 (0x44)    0.0MHz *current
        h: width  1024 start    0 end    0 total 1024 skew    0 clock    0.0KHz
        v: height  768 start    0 end    0 total  768           clock    0.0Hz
  800x600 (0x45)    0.0MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock    0.0KHz
        v: height  600 start    0 end    0 total  600           clock    0.0Hz
  640x480 (0x46)    0.0MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock    0.0KHz
        v: height  480 start    0 end    0 total  480           clock    0.0Hz
```



I didn't even think about the possibility of xrandr being somewhat of a culprit.  Likely?

---

### Post by 4Orbs on 2009-06-27
Hello DyBurke. Hope you are enjoying this Saturday. I'm just kinda watching the thread and wishing an Ubu-guru would drop in and offer some magical fix for your problem. Have you tried this: when you get to the "low graphics mode" error screen, select the xfix option (try to fix xorg automatically).

---

### Post by QIII on 2009-06-27
Just as an aside, folks...

I reported a bug on this quite some time ago.

Same card.  Same driver.

Still a problem in Karmic.

Added a bug.

Disable the driver and live without advanced desktop effects.

---

### Post by 4Orbs on 2009-06-27
I guess the easy answer is to just buy a new computer... but I really love my old snail. And it's still faster than my reflexes.

---

### Post by DyBurke on 2009-06-27
> **4Orbs said:**
> Hello DyBurke. Hope you are enjoying this Saturday. I'm just kinda watching the thread and wishing an Ubu-guru would drop in and offer some magical fix for your problem. Have you tried this: when you get to the "low graphics mode" error screen, select the xfix option (try to fix xorg automatically).


Hey, 4Orbs.  I'm having a great day; I hope the same for you. :)  Unfortunately, I've tried to have it automatically reconfigure it, but alas, no change. :(   

Thank you again for all the help you've given me.  Here's to hoping that Ubu-guru shows up. :P

---

### Post by DyBurke on 2009-06-27
> **QIII said:**
> Just as an aside, folks...

I reported a bug on this quite some time ago.

Same card.  Same driver.

Still a problem in Karmic.

Added a bug.

Disable the driver and live without advanced desktop effects.


:(   Thanks for the info.

---

### Post by DyBurke on 2009-06-27
> **4Orbs said:**
> I guess the easy answer is to just buy a new computer... but I really love my old snail. And it's still faster than my reflexes.


haha I know how that is. :)

---

