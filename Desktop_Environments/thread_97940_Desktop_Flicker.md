---
title: "Desktop Flicker"
date: 2005-12-02
forum: Desktop Environments
---

### Post by lwinkenb on 2005-12-02
I have a really bad flicker that occurs when I move the mouse.  Basically, a bunch of horizontal lines run up and down the screen when I move the mouse, but when the mouse is not moving -- everything looks fine.  I also noticed that the flicker occurs when something processor intensive is happening (like when I open up Firefox).

I am sure that my screen resolution/refresh is correct because it is the same resolution and refresh rate that I am running in Windows XP.  

I ran **dpkg-reconfigure xserver-xorg**, and made sure the correct video card was being selected, and it was (S3 VIRGE).  Does anyone have any ideas on what the problem could be?  The flicker is bad enough where the desktop is unusable.

---

### Post by RAOF on 2005-12-02
Man, you get all sorts of cool errors browsing these forums.

First thing I'd try in fixing yours is running dpkg-reconfigure xserver-xorg again, and selecting the vesa driver - no acceleration, no fancy X architecture, just a plain draw-stuff-to-the-screen driver.  If that works, I'd suggest you post your /etc/X11/xorg.conf, and we can pick over it and see whether there's anything obvious wrong ;)

---

### Post by lwinkenb on 2005-12-02
I tried changing the driver from "s3virge" to "vesa", but then my monitor just shuts off when I try to start gdm.  Here is what my xorg.conf file looks like:

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "S3 Inc. 86c325 [ViRGE]"
        Driver          "s3virge"
        BusID           "PCI:0:15:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "MAG LT776"
        Option          "DPMS"
        HorizSync       31-60
        VertRefresh     60-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86c325 [ViRGE]"
        Monitor         "MAG LT776"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "8$        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "8$        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by RAOF on 2005-12-02
[QUOTE=lwinkenb]I tried changing the driver from "s3virge" to "vesa", but then my monitor just shuts off when I try to start gdm.  Here is what my xorg.conf file looks like:
[/QUOTE]
Hm.  What does /var/log/Xorg.0.log look like in that case?

Anyway, maybe try commenting out (with a '#' at the start of the line) some of the modules?  I'd try dri & glx first.  Also commenting out the "UseFBDev", and possibly the BusID lines.  Try one at a time, pretty much in the order presented.

---

### Post by lwinkenb on 2005-12-02
> Hm. What does /var/log/Xorg.0.log look like in that case?
Here it is:
```

Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  2 02:07:46 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "MAG LT776"
(**) |   |-->Device "S3 Inc. 86c325 [ViRGE]"
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
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10ec,8169 card 1385,311a rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 5333,5631 card 0000,0000 rev 06 class 03,00,00 hdr 00
(II) PCI: 00:13:0: chip 1103,0004 card 0000,0000 rev 01 class 01,80,00 hdr 80
(II) PCI: 00:13:1: chip 1103,0004 card 0000,0000 rev 01 class 01,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0080 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:15:0) S3 Inc. 86c325 [ViRGE] rev 6, Mem @ 0xd4000000/26
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd9000000 - 0xd90000ff (0x100) MX[B]
	[1] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[2] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[4] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[5] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[6] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd9000000 - 0xd90000ff (0x100) MX[B]
	[1] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[2] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[4] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[5] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[6] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[7] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[8] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[9] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd9000000 - 0xd90000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[11] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
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
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
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
(II) LoadModule: "vesa"
(II) Loading /usr/X11R6/lib/modules/drivers/vesa_drv.o
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
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
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:0f:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd9000000 - 0xd90000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[9] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[10] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[11] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd9000000 - 0xd90000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[8] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[9] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[10] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 1.2
(II) VESA(0): VESA VBE Total Mem: 4096 kB
(II) VESA(0): VESA VBE OEM: S3 Incorporated. 86C325
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 101 (640x480)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 12
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 102 (800x600)
	ModeAttributes: 0x1f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 103 (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 104 (1024x768)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 105 (1024x768)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 4
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 106 (1280x1024)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 107 (1280x1024)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 2
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 109 (132x25)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0xb800
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 122
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 10a (132x43)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 32
	WinSize: 32
	WinASegment: 0xb800
	WinBSegment: 0xb800
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 112
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
Mode: 10d (320x200)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 1
	RsvdFieldPosition: 15
	DirectColorModeInfo: 0
Mode: 10e (320x200)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
*Mode: 10f (320x200)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
Mode: 110 (640x480)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 1
	RsvdFieldPosition: 15
	DirectColorModeInfo: 0
Mode: 111 (640x480)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
*Mode: 112 (640x480)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
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
Mode: 113 (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 1
	RsvdFieldPosition: 15
	DirectColorModeInfo: 0
Mode: 114 (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
*Mode: 115 (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
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
Mode: 116 (1024x768)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0004886
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 1
	RsvdFieldPosition: 15
	DirectColorModeInfo: 0

(II) VESA(0): Total Memory: 64 64KB banks (4096kB)
(II) VESA(0): MAG LT776: Using hsync range of 31.00-60.00 kHz
(II) VESA(0): MAG LT776: Using vrefresh range of 60.00-75.00 Hz
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (75, 75)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd9000000 - 0xd90000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[8] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[9] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[10] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 1.2
(II) VESA(0): VESA VBE Total Mem: 4096 kB
(II) VESA(0): VESA VBE OEM: S3 Incorporated. 86C325
(II) VESA(0): virtual address = 0xb7d09000,
	physical address = 0xa0000, size = 65536
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
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

```

I tried commenting out the the lines you suggested one by one, but the results were the same each time (the same flicker).

---

### Post by zvodd on 2005-12-15
I get the same flickering problem with my Kubuntu box, and Unbuntu (when i had it installed) and it appears to be a very commen problem, this issue needs much more attention.

---

### Post by ddaahh on 2006-07-10
Hi,

I just tumbled over the same problem in (k)ubuntu 6.06 and a S3 Virge DX .

My solution was to adjust the configured video memory from 1 (wrong) to 4 (correct) MB. It's very easy to do this with the display setup of KDE.


Dirk

---

