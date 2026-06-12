---
title: "need help with tv-out on nvidia geforce3 ti 200"
date: 2006-04-22
forum: Desktop Environments
---

### Post by heed on 2006-04-22
I'm using a GeForce 3 Ti 200,
NVidia driver 1.0-7667

first, i tried the instructions here: [http://www.cs.rit.edu/~css8044/?q=mythtv#nvidia]("http://www.cs.rit.edu/~css8044/?q=mythtv#nvidia")

but that concerns me now since using that I installed twm window manager:confused: 
That didn't help with the tvout issues at all.

Then I tried this:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
and then this:
[http://www.ubuntuforums.org/showthread.php?t=98456](http://www.ubuntuforums.org/showthread.php?t=98456)

But it still is doing the same thing.

I know that the svideo out works, since I see everything on the tv from the bios to where the system boots through the graphical bootup screen (where it shows what it's doing), then it dies and I don't see anything else on the tv.

Any help would be greatly appreciated, since using it with the tv is the main reason I installed linux (myth is next!).](*,) 


Here's a copy of the pertinent parts of the xorg.conf & log:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
    Load    "type1"
    Load    "vbe"
EndSection

Section "Device"
    Identifier    "card0"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option        "TVStandard"        "PAL-D"
    Option        "TVOutFormat"        "SVIDEO"
#    Option        "TVOverScan"        "0.5"
    Option        "RenderAccel"        "1"
    Option        "ConnectedMonitor"    "TV"
EndSection

Section "Monitor"
    Identifier    "tv0"
#    Option        "DPMS"
    HorizSync    30-50
    VertRefresh    60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "card0"
    Monitor        "tv0"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "DRI"
    Mode    0666
EndSection  
```

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux denpc 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
    Before reporting problems, check http://wiki.X.Org
    to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T

(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 22 13:55:52 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "tv0"
(**) |   |-->Device "card0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.2
    X.Org Video Driver: 0.7
    X.Org XInput driver : 0.4
    X.Org Server Extension : 0.2
    X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0741 card 1043,815c rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1043,810e rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1043,810d rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1043,810e rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1043,810e rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1043,810e rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1043,810e rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1039,0900 rev 90 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0201 card 107d,2861 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xd4000000 - 0xdbffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xdc000000 - 0xe3ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV20 [GeForce3 Ti 200] rev 163, Mem @ 0xd4000000/24, 0xdc000000/26, 0xe0000000/19
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xe5003000 - 0xe5003fff (0x1000) MX[B]
    [1] -1    0    0xe5002000 - 0xe5002fff (0x1000) MX[B]
    [2] -1    0    0xe5001000 - 0xe5001fff (0x1000) MX[B]
    [3] -1    0    0xe5000000 - 0xe5000fff (0x1000) MX[B]
    [4] -1    0    0xe5004000 - 0xe5004fff (0x1000) MX[B]
    [5] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [6] -1    0    0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
    [7] -1    0    0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
    [8] -1    0    0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
    [9] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [10] -1    0    0x0000e400 - 0x0000e47f (0x80) IX[B]
    [11] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[B]
    [12] -1    0    0x00004000 - 0x0000400f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xe5003000 - 0xe5003fff (0x1000) MX[B]
    [1] -1    0    0xe5002000 - 0xe5002fff (0x1000) MX[B]
    [2] -1    0    0xe5001000 - 0xe5001fff (0x1000) MX[B]
    [3] -1    0    0xe5000000 - 0xe5000fff (0x1000) MX[B]
    [4] -1    0    0xe5004000 - 0xe5004fff (0x1000) MX[B]
    [5] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [6] -1    0    0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
    [7] -1    0    0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
    [8] -1    0    0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
    [9] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [10] -1    0    0x0000e400 - 0x0000e47f (0x80) IX[B]
    [11] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[B]
    [12] -1    0    0x00004000 - 0x0000400f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xe5003000 - 0xe5003fff (0x1000) MX[B]
    [6] -1    0    0xe5002000 - 0xe5002fff (0x1000) MX[B]
    [7] -1    0    0xe5001000 - 0xe5001fff (0x1000) MX[B]
    [8] -1    0    0xe5000000 - 0xe5000fff (0x1000) MX[B]
    [9] -1    0    0xe5004000 - 0xe5004fff (0x1000) MX[B]
    [10] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [11] -1    0    0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
    [12] -1    0    0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
    [13] -1    0    0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [17] -1    0    0x0000e400 - 0x0000e47f (0x80) IX[B]
    [18] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[B]
    [19] -1    0    0x00004000 - 0x0000400f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 6.8.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.7667
    Module class: XFree86 Server Extension
    ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.2
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.1.0
    ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.7667
    Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:03:12 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xe5003000 - 0xe5003fff (0x1000) MX[B]
    [6] -1    0    0xe5002000 - 0xe5002fff (0x1000) MX[B]
    [7] -1    0    0xe5001000 - 0xe5001fff (0x1000) MX[B]
    [8] -1    0    0xe5000000 - 0xe5000fff (0x1000) MX[B]
    [9] -1    0    0xe5004000 - 0xe5004fff (0x1000) MX[B]
    [10] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [11] -1    0    0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
    [12] -1    0    0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
    [13] -1    0    0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [16] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [17] -1    0    0x0000e400 - 0x0000e47f (0x80) IX[B]
    [18] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[B]
    [19] -1    0    0x00004000 - 0x0000400f (0x10) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[B](B)
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xe5003000 - 0xe5003fff (0x1000) MX[B]
    [6] -1    0    0xe5002000 - 0xe5002fff (0x1000) MX[B]
    [7] -1    0    0xe5001000 - 0xe5001fff (0x1000) MX[B]
    [8] -1    0    0xe5000000 - 0xe5000fff (0x1000) MX[B]
    [9] -1    0    0xe5004000 - 0xe5004fff (0x1000) MX[B]
    [10] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[B]O
    [11] -1    0    0xe0000000 - 0xe007ffff (0x80000) MX[B](B)
    [12] -1    0    0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
    [13] -1    0    0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [19] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[B]
    [20] -1    0    0x0000e400 - 0x0000e47f (0x80) IX[B]
    [21] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[B]
    [22] -1    0    0x00004000 - 0x0000400f (0x10) IX[B]
    [23] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [24] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TVStandard" "PAL-D"
(**) NVIDIA(0): Option "TVOutFormat" "S-VIDEO"
(**) NVIDIA(0): Option "RenderAccel" "1"
(**) NVIDIA(0): Option "TVOverScan" "0.5"
(**) NVIDIA(0): Enabling experimental RENDER acceleration
(**) NVIDIA(0): Unknown TVOutFormat value.  Known values are "SVIDEO" and
(**) NVIDIA(0):      "COMPOSITE"
(**) NVIDIA(0): TV Standard string: "PAL-D"
(--) NVIDIA(0): Linear framebuffer at 0xDC000000
(--) NVIDIA(0): MMIO registers at 0xD4000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce3 Ti 200
(--) NVIDIA(0): VideoBIOS: 03.20.00.19.00
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(0): tv0: Using hsync range of 30.00-50.00 kHz
(II) NVIDIA(0): tv0: Using vrefresh value of 60.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)

snip

(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(==) NVIDIA(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:

snip

(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled

snip

(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) NVIDIA(0): Setting mode "800x600"

  
```

---

