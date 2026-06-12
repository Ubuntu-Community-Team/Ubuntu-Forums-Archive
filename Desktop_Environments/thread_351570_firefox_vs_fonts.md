---
title: "firefox vs fonts"
date: 2007-02-02
forum: Desktop Environments
---

### Post by numerodix on 2007-02-02
I had a working dapper install until a few days ago when I decided to upgrade to Edgy. Unfortunately the upgrade totally hosed my system, but at least I started with a clean slate on Edgy. Everything works beautifully, except the fonts. Gnome and KDE fonts both render pretty well, even though they're not perfect. But Firefox is really struggling. In the past I've always been able to trace this bug back to the dpi, but here I've played with the dpi from 75 up to 120 and the fonts still look the same in Firefox.

See the screenshots. One is from Edgy, the other is from another Gentoo box (since I no longer have the Dapper install to show you), showing what it's supposed to look like.

The first is part of my google home page, the other is [http://www.xtratime.org/forum/search.php?do=getdaily](http://www.xtratime.org/forum/search.php?do=getdaily).

I'm not very fluent in debian, but I've tried to reconfigure xorg and fontconfig, as per some suggestion in a thread I saw, which didn't fix it. Nor did setting the dpi, playing with font settings in gnome etc. I checked Xorg.0.log, and apparently the font paths were all wrong, so I fixed that, but the problem persists.

I'm still getting these warnings in the xorg log and I don't know what they mean:
> (WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype/freefont".
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype/msttcorefonts".
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype/ttf-bitstream-vera".
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype/ttf-dejavu".

I have a full backup of the old Dapper install and when I checked those paths, there were no fonts.dir files in there.

The full log: [http://pastebin.com/873442](http://pastebin.com/873442)
The config: [http://pastebin.com/873447](http://pastebin.com/873447)

EDIT:
> ii  msttcorefonts              1.2ubuntu3        Installer for Microsoft TrueType core fonts
ii  ttf-arabeyes            1.1-6          Arabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-ukai         0.1.20060513-1 "AR PL ZenKai Uni" Chinese Unicode TrueType
ii  ttf-arphic-uming        0.1.20060513-1 "AR PL ShanHeiSun Uni" Chinese Unicode TrueT
ii  ttf-baekmuk             2.2-1ubuntu1   Baekmuk series TrueType fonts
ii  ttf-bengali-fonts       0.4.7.1        Free TrueType fonts for the Bengali language
ii  ttf-bitstream-vera      1.10-6         The Bitstream Vera family of free TrueType f
ii  ttf-dejavu              2.7-2          Bitstream Vera fonts with additional charact
ii  ttf-devanagari-fonts    0.4.7.1        Free TrueType fonts for languages using the
ii  ttf-freefont            20060501cvs-6  Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-gentium             1.02-2ubuntu1  Gentium TrueType font
ii  ttf-gujarati-fonts      0.4.7.1        Free TrueType fonts for the Gujarati languag
ii  ttf-indic-fonts         0.4.7.1        Metapackage for free Indian language fonts
ii  ttf-kannada-fonts       0.4.7.1        Free TrueType fonts for the Kannada language
ii  ttf-kochi-gothic        1.0.20030809-4 Kochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho        1.0.20030809-4 Kochi Subst Mincho Japanese TrueType font wi
ii  ttf-lao                 0.0.20060226-2 TrueType font for Lao language
ii  ttf-malayalam-fonts     0.4.7.1        Free TrueType fonts for the Malayalam langua
ii  ttf-mgopen              1.1-2          Magenta Open Truetype fonts
ii  ttf-opensymbol          2.0.4-0ubuntu4 The OpenSymbol TrueType font
ii  ttf-oriya-fonts         0.4.7.1        Free TrueType fonts for the Oriya language
ii  ttf-punjabi-fonts       0.4.7.1        Free TrueType fonts for the Punjabi language
ii  ttf-tamil-fonts         0.4.7.1        Free TrueType fonts for the Tamil language
ii  ttf-telugu-fonts        0.4.7.1        Free TrueType fonts for the Telugu language
ii  ttf-thai-tlwg           0.4.4-0ubuntu1 Thai fonts in TrueType format

---

### Post by kerry_s on 2007-02-02
That's nothing to worry about, the new xorg auto checks for fonts. You can get rid of the warnings by removing the font paths in xorg.conf.

sudo gedit /etc/X11/xorg.conf

remove all the font paths, see pic->

---

### Post by numerodix on 2007-02-02
> **kerry_s said:**
> That's nothing to worry about, the new xorg auto checks for fonts. You can get rid of the warnings by removing the font paths in xorg.conf.

sudo gedit /etc/X11/xorg.conf

remove all the font paths, see pic->

Okay, but that doesn't make the fonts look right. See the screenshots and compare.

---

### Post by kerry_s on 2007-02-02
Okay, im guessing the 1 on the right is the good 1 and the 1 on the left is what you got now. Are using a fonts.conf? I've attached the 1 i'm using rename it to .fonts.conf and put it in your home account. then log out and back in.

---

### Post by numerodix on 2007-02-02
Hm, no it still looks the same :confused:  In fact some fonts just look very wrong indeed. DejaVu Sans is the one I use almost all the time, it's a nice font, but here it's awful.

---

### Post by kerry_s on 2007-02-02
Try this, download the attachment and extract it to /usr/share/fonts/truetype/ttf-dejavu

then reboot your system.

---

### Post by numerodix on 2007-02-02
Hm, those messages are gone now, for all the dirs, but the fonts still are messed up.

---

### Post by kerry_s on 2007-02-02
Try these->

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig
sudo fc-cache -v
fc-cache -f

Are sure you put the .fonts.conf in your /home/you/?

---

### Post by numerodix on 2007-02-02
> **kerry_s said:**
> Try these->

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig
sudo fc-cache -v
fc-cache -f

This didn't do anything either :(

> **kerry_s said:**
> Are sure you put the .fonts.conf in your /home/you/?

Yes, of course.

---

### Post by kerry_s on 2007-02-02
Can you post a shoot of your font setup in firefox? Like this->
Also try renaming your.mozilla to .mozilla.old and see if the stock settings are doing the same thing.

---

### Post by numerodix on 2007-02-02
> **kerry_s said:**
> Can you post a shoot of your font setup in firefox? Like this->
Also try renaming your.mozilla to .mozilla.old and see if the stock settings are doing the same thing.

Here are two. One from openoffice, and notice how incredibly bad both Bitstream Vera and DejaVu Sans look. The other is from Firefox.

---

### Post by kerry_s on 2007-02-02
Uncheck the allow websites to chose there own fonts, you want to use your fonts, also set a minumum font size say like 16, i usally keep it the same as my size cause i don't want it going smaller than the size i want.

---

### Post by numerodix on 2007-02-02
> **kerry_s said:**
> Uncheck the allow websites to chose there own fonts, you want to use your fonts, also set a minumum font size say like 16, i usally keep it the same as my size cause i don't want it going smaller than the size i want.

But that's no good, I don't want to force using my fonts all the time, I've never had to do that to get good fonts before. I just don't understand why they look so messed up.

---

### Post by kerry_s on 2007-02-02
> **numerodix said:**
> But that's no good, I don't want to force using my fonts all the time, I've never had to do that to get good fonts before. I just don't understand why they look so messed up.

Why would you not want to use the fonts you like? Sites tend to choose the first compatible font. If they choose a bitmap font you get that crappy look like yours has. They don't choose the best looking. Fonts are a personal preference.
Also what kind of monitor?
What dpi are you using now?(cause 16 is like huge, i'm guessing your set around 75)
How are you setting your dpi, in xorg.conf?

I just redid all my fonts a couple a days ago so they work right with this xorg. In dapper with the old xorg it was manually set. With the new xorg it's suppose to be more flexible and automatic, which is a good thing, the problem is all those manual settings are still around. So you get a mix of both settings sometimes conflicting. It took me alot of googling and reading to get most of it right. Here's what my xorg.0.log looks like->

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux Linux1 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  2 12:22:58 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "HP"
(**) |   |-->Device "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3116 card 1106,3116 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1462,7380 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1462,7380 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1462,7380 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1462,738c rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0185 card 1554,1115 rev a4 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 164, Mem @ 0xe0000000/24, 0xd8000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[8] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[8] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "crt,crt"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "31.468-71.0"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "56.0-85.0"
(**) NVIDIA(0): Option "MetaModes" "1280x1024, 1280x1024"
(**) NVIDIA(0): Option "UseEdidDpi" "false"
(**) NVIDIA(0): Option "DPI" "120 x 120"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "crt,crt"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 4000 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.40.08
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 4000 at PCI:1:0:0:
(--) NVIDIA(0):     HP HWPD5259A (CRT-0)
(--) NVIDIA(0):     Gateway VX920 (CRT-1)
(--) NVIDIA(0): HP HWPD5259A (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Gateway VX920 (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
(**) NVIDIA(0): DPI set to (120, 120); computed from "DPI" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[1] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[7] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

