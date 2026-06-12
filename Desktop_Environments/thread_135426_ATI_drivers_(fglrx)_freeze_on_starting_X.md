---
title: "ATI drivers (fglrx) freeze on starting X"
date: 2006-02-23
forum: Desktop Environments
---

### Post by david-r-emett on 2006-02-23
I have tried several methods of getting these drivers to work, including:
[http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")
[http://ubuntuforums.org/showthread.php?t=75378]("http://ubuntuforums.org/showthread.php?t=75378")

Everything I try results in a corrupted screen with a little cross in the middle when starting X. The system doesnt respond to the mouse or any key combinations.

I have an X800 Pro and am using Ubuntu Breezy 5.10 i386 with kernel version 2.6.12-10-386.

I'm currently trying the method described at [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

Any help would be appreciated.

/etc/X11/xorg.conf is:
```

Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  #FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  #FontPath "/usr/share/X11/fonts/CID"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  # paths to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
  #FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"

  # Load "extmod" but omit DGA extension
  # (the DGA extension is broken in the fglrx driver)
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection

  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"

  Load "glx"
  Load "GLcore"
  Load "dri"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  Option "CoreKeyboard"
  Option "XkbRules" "xorg"
  Option "XkbModel" "pc105"
  Option "XkbLayout" "gb"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  Option "CorePointer"
  Option "Device" "/dev/input/mice"
  Option "Protocol" "ExplorerPS/2"
  Option "Buttons" "7"
  Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
  Identifier "ATI"
  Driver "fglrx" # this is the important bit

  # If X refuses to use the screen resolution you asked for,
  # uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC" ##

  # === Video Overlay for the Xv extension ===
  Option "VideoOverlay" "on"

  # === OpenGL Overlay ===
  # Note: When OpenGL Overlay is enabled, Video Overlay
  #       will be disabled automatically
  Option "OpenGLOverlay" "off"

  # === Use internal AGP GART support? ===
  # If OpenGL acceleration doesn't work, try using "yes" here
  # and disable the kernel agpgart driver.
  Option "UseInternalAGPGART" "no"

  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Samsung 959NF"
  Option "DPMS"
  HorizSync 30-110
  VertRefresh 50-160
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI"
  Monitor "Samsung 959NF"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  Screen "Default Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
EndSection

Section "DRI"
  Mode 0666
EndSection

```

/var/log/Xorg.0.log:
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux bobsleigh 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:13:15 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 24 00:20:50 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig Screen 0" (0)
(**) |   |-->Monitor "aticonfig Monitor 0"
(**) |   |-->Device "ATI Graphics Adapter 0"
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
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
A bunch of PCI stuff with (II)s (cut to save characters)
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
A bunch of Bus stuff with (II)s (cut to save characters)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x4a49) rev 0, Mem @ 0xe8000000/27, 0xfdff0000/16, I/O @ 0xbc00/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x4a69) rev 0, Mem @ 0xe0000000/27, 0xfdfe0000/16
A bunch of resource ranges with (II)s (cut to save characters)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
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
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
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
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.22.5
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
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9550 (M12 4E56), RADEON 9500 (R300 4144),
	RADEON 9600 TX (R300 4146), FireGL Z1 (R300 4147),
	RADEON 9700 PRO (R300 4E44), RADEON 9500 PRO/9700 (R300 4E45),
	RADEON 9600 TX (R300 4E46), FireGL X1 (R300 4E47),
	RADEON 9800 SE (R350 4148), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), MOBILITY RADEON X300 (M22 5460),
	MOBILITY RADEON X600 (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	RADEON X800 XL (R430 554D), RADEON X800 (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.22.5
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.22g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb  7 2006 19:32:18
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.22.1-driver-lnx-244115
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON X800 PRO (R420 4A49) found
(II) resource ranges after xf86ClaimFixedResources() call:
	... (cut to save characters)
(II) fglrx(0): pEnt->device->identifier=0x8212948
(II) resource ranges after probing:
	... (cut to save characters)
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON X800 PRO (R420 4A49)" (Chipset = 0x4a49)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe8000000
(--) fglrx(0): MMIO registers at 0xfdff0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.2
(II) fglrx(0): VESA VBE OEM Vendor: 
(II) fglrx(0): VESA VBE OEM Product: è
(II) fglrx(0): VESA VBE OEM Product Rev: 
(WW) fglrx(0): GetVBEMode failed
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/X11R6/lib/modules/linux/libdrm.a
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR3
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)

```

---

### Post by Ampersand on 2006-02-24
For a start, does it work if you use the vesa driver?

---

### Post by david-r-emett on 2006-02-24
yes, it seems to work okay with "vesa" and "ati"

---

