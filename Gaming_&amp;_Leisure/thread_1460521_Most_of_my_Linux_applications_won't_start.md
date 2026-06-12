---
title: "Most of my Linux applications won't start"
date: 2010-04-22
forum: Gaming &amp; Leisure
---

### Post by Matoro1992 on 2010-04-22
Something happened to my Ubuntu 32 bit version a while back, and now its really getting on my nerves. For some reason I can't open most of my applications for some odd reason.
For example:
What happens after I downloaded DeSmuME(Gtk)(DS emulator), I decided to open it from my tool bar. Well,  when I clicked on the app, it done nothing. It won't run or anything!

I know it doesn't seem much, but that is exactly what happened. How do I open up applications and it actually runs? This happens with other games to. Is my computer hacked or glitched or old or what?

---

### Post by kiplingw on 2010-04-22
Hey Matoro. What do you see on the terminal when you try running it from that?

---

### Post by Bölvaður on 2010-04-22
open terminal (from menu or alt+f2 and type gnome-terminal)
what does this return?
```
desmume
```
try type the names of your other programs to see what errors come up. There might be something that have changed on your system. Perhaps by something you've installed or happened by updates perhaps... we dont care we are only here to help to fix your problems.

---

### Post by Matoro1992 on 2010-04-24
> **Bölvaður said:**
> open terminal (from menu or alt+f2 and type gnome-terminal)
what does this return?
```
desmume
```
try type the names of your other programs to see what errors come up. There might be something that have changed on your system. Perhaps by something you've installed or happened by updates perhaps... we dont care we are only here to help to fix your problems.
When I typed 'desmume' in the terminal,
I got this...
> (desmume:4401): GdkGLExt-WARNING **: Window system doesn't support OpenGL.
That is odd, that never happened to me in the past. My 'OpenGL' worked just fine in the past. I wonder why it stopped working all of a sudden. Is there anyway I can re-activate this again?

---

### Post by hikaricore on 2010-04-24
You porbably need to reinstall your video drivers.
Have you installed any updates recently?  Installing kernel updates can sometimes bork your drivers if you've installed them manually.
You may want to post more info about your system and which version of ubuntu you're using.

---

### Post by kiplingw on 2010-04-24
What does running glxinfo from the terminal say? Copy and paste here.

Kip

---

### Post by Matoro1992 on 2010-04-24
I typed in 'glxinfo' in the terminal and this is what it provided:
> name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

Um, is this bad? :confused: What should I do to fix it?

---

### Post by kiplingw on 2010-04-24
Ok, like hikaricore said, there is definitely something up with your video drivers. What does running...

```
$ lspci | grep -i vga
```

...on the terminal say?

Kip

---

### Post by Matoro1992 on 2010-04-24
I got this:
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)


---

### Post by kiplingw on 2010-04-24
Do you have xserver-xorg-video-intel package installed?

```
$ sudo aptitude install xserver-xorg-video-intel
```

That package should provide the driver for your card.

---

### Post by Matoro1992 on 2010-04-24
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Nothing happened after that. After that was installed, I tried opening 'desmume' in the terminal, I end up getting this again:
> (desmume:32652): GdkGLExt-WARNING **: Window system doesn't support OpenGL.

---

### Post by kiplingw on 2010-04-24
Interesting, so it was already installed. Paste us the contents of /var/log/Xorg.0.log

---

### Post by Matoro1992 on 2010-04-24
Ok, when in '/var/log/Xorg.0.log' in my terminal, I got this:
> bash: /var/log/Xorg.0.log: Permission denied
Wha?
-
But when I paste that in my google chrome browser, I got this (I can't put in a text editor, because it exeeds the limit)(I'm going to delete this after you check this out, just to avoid spam):

> 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Zeilph-laptop 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 24 11:33:55 2010
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

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 3, Mem @ 0xdff00000/524288, 0xc0000000/268435456, 0xdfec0000/262144, I/O @ 0x0000ec38/8
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) NVIDIA GLX Module  71.86.08  Sat Jan 24 20:46:30 PST 2009
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
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) intel(0): Chipset: "915GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFF00000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
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
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Output TV has no monitor section
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1280x800
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
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x20d8 (FWATER_BLC) changed from 0x01080108 to 0x03010301
(WW) intel(0): Register 0x20dc (FWATER_BLC2) changed from 0x00000108 to 0x00000301
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x30000000 to 0x000c0c00
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710087
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x6b405140
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 489216 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1956860 kB available
(WW) intel(0): DRI2 requires UXA
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): adjusting plane->pipe mappings to allow for framebuffer compression
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000007f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000007fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000007fe21000 physical
)
(II) intel(0): 0x0062b000-0x0072afff: fake bufmgr (1024 kB)
(II) intel(0): 0x0072b000-0x0072bfff: overlay registers (4 kB, 0x000000007ff2b000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (16384 kB)
(II) intel(0): 0x02000000-0x03dfffff: exa offscreen (30720 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane B is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane A is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Failed
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
(II) Initializing built-in extension ZINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(II) intel(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
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
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event10"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device KYE Genius USB Wheel Mouse
(**) KYE Genius USB Wheel Mouse: always reports core events
(**) KYE Genius USB Wheel Mouse: Device: "/dev/input/event5"
(II) KYE Genius USB Wheel Mouse: Found 5 mouse buttons
(II) KYE Genius USB Wheel Mouse: Found x and y relative axes
(II) KYE Genius USB Wheel Mouse: Configuring as mouse
(**) KYE Genius USB Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) KYE Genius USB Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "KYE Genius USB Wheel Mouse" (type: MOUSE)
(**) KYE Genius USB Wheel Mouse: (accel) keeping acceleration scheme 1
(**) KYE Genius USB Wheel Mouse: (accel) filter chain progression: 2.00
(**) KYE Genius USB Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) KYE Genius USB Wheel Mouse: (accel) set acceleration profile 0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.3 kHz)
(II) intel(0): EDID vendor "QDS", prod id 20
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x007bf000 (pgoffset 1983)
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.

---

### Post by kiplingw on 2010-04-24
Ok, it looks like the nvidia driver is trying to load. Uninstall any package containing the name nvidia. Then reinstall the intel package I showed you earlier and finally reboot.

---

### Post by Matoro1992 on 2010-04-24
Well this sucks. My Ubuntu computer exploded when I rebooted it. Ok, not really. Basically when I restarted my computer, the Ubuntu  loading screen came out just fine. After it was done loading all the way, it normally switches to the log in screen. Well, in the log in screen part, the graphics or whatever got jammed up or mixed up it looks like. And it stood froze. I couldn't find a way to get rid of it. 
I guess its time for me to re-install the Linux operating system back again. Oh well, thats ok. I just lost a couple of files like my music and videos I made. I can always make new ones.

Well, I guess thanks for helping me. Idk. I think I need to spend some time away from the computer and focus more time of my school work. :)

---

### Post by kiplingw on 2010-04-24
Hey Matoro. The machine wouldn't boot after you removed the nvidia driver and re-installed the intel one? I am sorry to hear that, but you can try going into the recovery mode to get into the console. From there, you can still get access to the X log via /var/log/Xorg.0.log.

---

### Post by hikaricore on 2010-04-25
You should be able to easily recover any files, besides re-installation isn't the only option in this case...
It doesn't really sound like that big of a deal, you could probably still access tty terminals and fix it at the very least.

---

### Post by kiplingw on 2010-04-25
I agree. You'll probably learn more if you try to fix it. But if you have to focus on school, then that is a higher priority.

---

