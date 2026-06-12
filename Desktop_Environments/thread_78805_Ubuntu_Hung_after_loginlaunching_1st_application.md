---
title: "Ubuntu Hung after login/launching 1st application"
date: 2005-10-18
forum: Desktop Environments
---

### Post by guccica on 2005-10-18
Hi all,
would like to have opinion of u all on Ubuntu hung after the login or 1st application launch.

Below is details of the issues::

situation 1::
--------------
1) Login using user name and password.
2) Desktop shown.
3) Ubuntu hung ::

a) after a while
b) after launching any application such as fire fox, ..etc

situation 2::
-------------
1) at the login page, click language
2) Ubuntu Hung

Help needed::
1) How to solve teh problem? What action should i do inorder to findout the reason?
2) By any chances can i know how to launch KDE? 

FYI, i am newbie for Ubuntu as well as open source Operating System.

Please advice. thanks a lotttttt :P

---

### Post by guccica on 2005-10-19
Hie...anyone please help~~~ Cant even start expereince to use it since it hung at starting.....
:(

---

### Post by Murgle on 2005-10-19
Im not sure what could be causing that but I can answer you question about kde, if you have it installed then from the login screen there is a session option.  click that and select kde.  if you don't have it installed and still can't login hit Ctrl + Alt + F1 and that will take you to a terminal, Ctrl + Alt + F7 to return to the login screen.  once you are at the terminal login and then type sudo apt-get update and then sudo apt-get install kubuntu-desktop and be prepaired for along wait while it downloads alot of files

---

### Post by angkor on 2005-10-19
Are you able to go to the console when gnome hangs?

You can try to do so with Ctrl+Alt+F1

---

### Post by guccica on 2005-10-21
Hi, sorry for late response. Thanks for guidance.

However, i still not able to use ubuntu's gnome.
I unable to change mode to console while it hung. Soemtimes i can login to the desktop, however it sure will hang while the 1st application is launch. Any ideal on solving this?
By any chances can i know is it hardware's driver error or ubuntu issues?

thanks. please advice

---

### Post by Murgle on 2005-10-21
the solution is to go to the console befor you log in, with Ctrl + Alt + F1.  then log in a your user and type cat /var/log/Xorg.0.log.  Tell us what you see, that might give us a clue as to what is wrong

---

### Post by guccica on 2005-11-12
Thanks for reply. Here is the content of /var/log/Xorg.0.log from my machine.
Part 1::

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux guccica 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 12 19:24:22 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "StudioWorks"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
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
(II) PCI: 00:00:0: chip 8086,2570 card 8086,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 8086,524c rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 8086,524c rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 8086,524c rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 8086,524c rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 8086,524c rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 8086,524c rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 8086,524c rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 8086,524c rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 8086,e000 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0181 card 0000,0000 rev c1 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 1186,1300 card 1186,1300 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1131,7130 card 185b,c100 rev 01 class 04,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4800000 - 0xf47fffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0206 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 193, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe9e0000/17
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff

(II) Active PCI resource ranges:
	[0] -1	0	0xfeaff800 - 0xfeaffbff (0x400) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaff800 - 0xfeaffbff (0x400) MX[B]
	[1] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[2] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[3] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[4] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[15] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeaffbff (0x400) MX[B]
	[6] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
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
(II) LoadModule: "nv"
(II) Loading /usr/X11R6/lib/modules/drivers/nv_drv.o
(II) Module nv: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.1
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
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro4 NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 280 NVS, Quadro4 380 XGL, Quadro NVS 50 PCI, GeForce4 448 Go,
	GeForce4 MX Integrated GPU, GeForce3, GeForce3 Ti 200,
	GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600, GeForce4 Ti 4400,
	0x0252, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, 0x0313, GeForce FX 5600SE,
	0x0316, 0x0317, GeForce FX Go5600, GeForce FX Go5650,
	Quadro FX Go700, 0x031D, 0x031E, 0x031F, GeForce FX 5200,
	GeForce FX 5200 Ultra, GeForce FX 5200, GeForce FX 5200SE,
	GeForce FX Go5200, GeForce FX Go5250, GeForce FX 5500,
	GeForce FX 5100, GeForce FX Go5200 32M/64M, 0x0329,
	Quadro NVS 280 PCI, Quadro FX 500/600 PCI, GeForce FX Go53xx Series,
	GeForce FX Go5100, 0x032F, GeForce FX 5900 Ultra, GeForce FX 5900,
	GeForce FX 5900XT, GeForce FX 5950 Ultra, Quadro FX 700,
	GeForce FX 5900ZT, Quadro FX 3000, GeForce FX 5700 Ultra,
	GeForce FX 5700, GeForce FX 5700LE, GeForce FX 5700VE, 0x0345,
	GeForce FX Go5700, GeForce FX Go5700, 0x0349, 0x034B,
	Quadro FX Go1000, Quadro FX 1100, 0x034F, GeForce 6800 Ultra,
	GeForce 6800, GeForce 6800 LE, 0x0043, GeForce 6800 GT, 0x0049,
	Quadro FX 4000, 0x00C0, GeForce 6800, GeForce 6800 LE,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400, 0x00CD,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, 0x0142, 0x0143,
	GeForce Go 6600, GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, 0x0147,
	GeForce Go 6600, 0x0149, 0x014B, 0x014C, 0x014D, Quadro FX 540,
	GeForce 6200, 0x0160, GeForce 6200 TurboCache(TM), 0x0162, 0x0163,
	GeForce Go 6200, 0x0163, GeForce Go 6250, GeForce Go 6200,
	GeForce Go 6250, 0x0169, 0x016B, 0x016C, 0x016D, 0x016E, 0x0210,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, 0x0220, 0x0221,
	0x0222, 0x0228

---

### Post by guccica on 2005-11-12
part 2

(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce4 MX 440 with AGP8X found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeaffbff (0x400) MX[B]
	[6] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeaffbff (0x400) MX[B]
	[6] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[7] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[8] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[9] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[10] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce4 MX 440 with AGP8X"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE8000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/X11R6/lib/modules/libi2c.a
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GSM  Model: 3af6  Serial#: 16843009
(II) NV(0): Year: 2001  Week: 12
(II) NV(0): EDID Version: 1.1
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.714/0.286 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 28  vert.: 21
(II) NV(0): Gamma: 2.60
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): redX: 0.619 redY: 0.347   greenX: 0.276 greenY: 0.608
(II) NV(0): blueX: 0.142 blueY: 0.060   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 720  vsize 405  refresh: 70  vid: 51771
(II) NV(0): #1: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NV(0): #2: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) NV(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #4: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) NV(0): #5: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #6: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 36.0 MHz   Image Size:  260 x 195 mm
(II) NV(0): h_active: 640  h_sync: 696  h_sync_end 752 h_blank_end 832 h_border: 0
(II) NV(0): v_active: 480  v_sync: 481  v_sync_end 484 v_blanking: 509 v_border: 0
(II) NV(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 54 kHz, PixClock max 60 MHz
(II) NV(0): Monitor name: StudioWorks 5
(II) NV(0): Monitor name: 52V
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 65536 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): StudioWorks: Using default hsync range of 30.00-54.00 kHz
(II) NV(0): StudioWorks: Using default vrefresh range of 50.00-120.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(WW) (1024x768,StudioWorks) mode clock 65MHz exceeds DDC maximum 60MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1280x768,StudioWorks) mode clock 80.14MHz exceeds DDC maximum 60MHz
(WW) (1280x800,StudioWorks) mode clock 83.46MHz exceeds DDC maximum 60MHz
(WW) (1152x768,StudioWorks) mode clock 64.995MHz exceeds DDC maximum 60MHz
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using mode "720x450" (no mode of this name)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan

(**) NV(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(--) NV(0): Display dimensions: (280, 210) mm
(--) NV(0): DPI set to (92, 92)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfeaff800 - 0xfeaffbff (0x400) MX[B]
	[8] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[9] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[10] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[11] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[12] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[33] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe8000000,0x4000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
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
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
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
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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

please advice on what should i do. my gnome keep on hung :(
thanks a lot

---

### Post by guccica on 2005-11-12
refer to the log file above, Is it the problem of Ubuntu hung cause by hardware detection?
thanks.

---

### Post by Juzz on 2005-11-13
It should be marked with FATAL, if it was something hardware related - as far as I can tell the only thing those errors mean is that you won't have 3D hardware acceleration.
If it was hardware then you wouldn't get as far as the graphical login.

what does this command output from the console:

```
ls -la ~/.ICE*
```

Do you get the message about Gnome console only lasting 10 seconds or less?

---

