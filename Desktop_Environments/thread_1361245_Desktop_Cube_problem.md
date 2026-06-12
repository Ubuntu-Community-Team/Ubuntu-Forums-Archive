---
title: "Desktop Cube problem"
date: 2009-12-21
forum: Desktop Environments
---

### Post by gabo.cr on 2009-12-21
I have issues between Compiz Fusion and the Extra Visual Effects in Ubuntu.
When I activate the Desktop Cube with Compiz Setting Manager the Extra Desktop Effects deactivate and then the Desktop Cube won't work.
I have a Dell Inspiron 1525, 3 GB Ram. The video card is not Nvidia.
I didn't have this problem with Ubuntu 8.04, but I do with Karmic.

I wanted to try Karmic because some of the video issues from Hardy get fixed with 9.10.

I ran out of ideas about what to do.
Anybody?

---

### Post by gabo.cr on 2009-12-21
I ran the Compiz Check and this is what I get:

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 
```


Do I have to install something else to make this work?

---

### Post by andrea000 on 2009-12-22
open a terminal.applications>accessories>terminal and type
> compiz

post the output from that

---

### Post by gabo.cr on 2009-12-29
This is what I get:

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

---

### Post by RedSingularity on 2009-12-29
Do you know what video card you have?

---

### Post by gabo.cr on 2009-12-29
This is what I have:

lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

Is my problem a bug already reported?
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433488)

---

### Post by lrcaballero on 2009-12-29
do the following:

System/Preferences/CCSM
go to Effects make sure Animations Add-On is Checked
Click on Animations - also make sure is checked
go to effect settings make sure that Random Animations for All events is checked (should be your first option. go back now select desktop and make sure rotate cube is checked....

Good luck

Luis

---

### Post by gabo.cr on 2009-12-29
> System/Preferences/CCSM
go to Effects make sure Animations Add-On is Checked
Click on Animations - also make sure is checked
go to effect settings make sure that Random Animations for All events is checked (should be your first option. go back now select desktop and make sure rotate cube is checked....

I tried that, but I have the same problem...
The Visual Effects under Appearance work fine until I activate the Cube.
That's when the Visual Effects go back to "None" and the Cube does not work.
Avant Windows Navigator also disappears when I do that.

I never had this problem with Hardy... I'm starting to miss Hardy.
:(

---

### Post by RedSingularity on 2009-12-30
Post the output of you xorg file.


cat /etc/X11/xorg.conf

---

### Post by gabo.cr on 2009-12-30
I don't have that file, apparently this file is not in 9.10. 
I tried creating one using the following command but it didn't work:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```


There is another way, but it takes more work.
It is a solution given by "pietjanjaap" in [this post]("http://ubuntuforums.org/showpost.php?p=8407028&postcount=9").

If I have to do this I will, but I want to make sure that I'm not just "throwing commands" to my computer to see if it works.
You know what I mean :roll:

---

### Post by gabo.cr on 2009-12-30
Is this the file we need?
(I'm sorry, this file is very big)
:rolleyes:

> 
/var/log/Xorg.0.log

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux gabo-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=ebc39bae-9d21-4b7a-bdf5-21515a6d51ba ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 30 15:56:00 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a02:1028:022f Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000eff8/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
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
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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
	compiled for 1.6.4, module version = 1.0.0
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
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Builtin Default intel Screen 0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output DVI1 has no monitor section
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output DVI1 disconnected
(II) intel(0): Output TV1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x800
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device Dell WMI hotkeys
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event7"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
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
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
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
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event9"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) PS/2 Mouse: initialized for relative axes.
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event10"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): EDID vendor "LPL", prod id 769
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): EDID vendor "LPL", prod id 769
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): EDID vendor "LPL", prod id 769
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): EDID vendor "LPL", prod id 769
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): EDID vendor "LPL", prod id 769
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): EDID vendor "LPL", prod id 769
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 301  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.5 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1392 h_blank_end 1512 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 832 v_border: 0
(II) intel(0):  W654G&#128;154W01
(II) intel(0):  $2=Eh&#139;§ÿ
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff00320c010300000000
(II) intel(0): 	00110103802115780ab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	0101010101017e1d00e8502020304030
(II) intel(0): 	36004bcf100000197e1d00e850202030
(II) intel(0): 	403036004bcf10000000000000fe0057
(II) intel(0): 	36353447803135345730310a000000fe
(II) intel(0): 	0024323d45688ba7ff01010a202000a1
(II) intel(0): EDID vendor "LPL", prod id 769
(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1280x800"x0.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   75.50  1280 1344 1392 1512  800 803 809 832 -hsync -vsync (49.9 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output TV1
```

---

### Post by Syndri on 2009-12-30
Integrated Graphics :(
eww i tried to get it working for me once with one of those cards
im sorry to say this but  i highly doubt u will get it up and running

---

### Post by gabo.cr on 2009-12-30
I was working fine on Hardy.
I hope that won't happen with Lucid Lynx !

---

### Post by RedSingularity on 2009-12-31
If you want to try creating the xorg file look at [this](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

---

### Post by gabo.cr on 2009-12-31
Thank you for that link!
Those instructions are a lot easier.
I did it, I now have the file in /etc/X11/xorg.conf

So, here is the output:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
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
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "record"
	Load  "glx"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
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

```

I still have the problem, I ran compiz in terminal and I also tried to activate the cube, but it is not working, but at least I have the file now.

---

### Post by RedSingularity on 2009-12-31
Well it seems that your intel driver is in fact activated.  That means that you probably cant use the accelerated graphics required by the cube with you current card.

---

### Post by gabo.cr on 2009-12-31
It is working now !!

The solution was scattered in different places.
This is what I did:
After creating the "xorg.conf" file, I typed this command in Terminal:

```
gstreamer-properties
```

A window opened, on the video tab I changed the Default Output Plugin to "X Window System (No Xv)".

Then I edited the "compiz" file, I opened it like this:

```
sudo gedit /usr/bin/compiz
```

I "commented" the following lines using "#".
Like this:

> # blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2a02 " # Intel GM965
#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)

And it works !
Finally
Thank you everyone for your patience, I hope this works for somebody else.
 
:lolflag:

---

