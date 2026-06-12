---
title: "3d Desktop questions"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by super.rad on 2007-04-06
I want to make my ubuntu (edgy) look more fancy, i was thinking of installing beryl or compiz but have a few questions, (my graphics card is a Nvidia 7600 GS)
1. Are either of them stable or are both still beta?
2. Which is less likely to give me problems? (crashing, xserver not loading, etc)
3. Which is easier to use?
4. Are their anyother alternatives to beryl or compiz?
5. Is there anyway i can find out if i have the newest nvidia drivers installed and working?

Thanks

---

### Post by SendDerek on 2007-04-06
Good news is, this question won't be a problem in a little while.  Compiz and Beryl just merged into one project again!

1.)  I believe they're both still in beta.
2.)  I've *heard* that compiz is a little more stable.
3.)  I personally believe that beryl is very intuitive and easy to use.
4.)  There's Sun's Looking Glass and [Metisse]("http://insitu.lri.fr/metisse/screenshots/")
5.)  There's always the new program called Envy.  Envy will automagically download and install the latest drivers for you card, but honestly there's probably an easier way to make sure you have the lastest drivers.

I hope that helps.  I'm no beryl or compiz guru, but I've ran both beryl (recently) and compiz (way back when).

---

### Post by super.rad on 2007-04-06
thanks, im downloading envy now

---

### Post by super.rad on 2007-04-06
i have tried using envy to update the nvidia driver and also tried doing it manually but whenever i reboot after installing it tells me xserver failed to load and i have to set the driver back to "nv" i thought i had saved the log file but obviously not as i cant find it now but the error is something about the nvidia kernel and no screen found? can anyone help me with this?

---

### Post by dougfractal on 2007-04-06
What's you nvidia card

lspci | grep "VGA"

nvidia have just made a few more cards legacy.
You may need to download from nvidia the archive 9631.

[http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)


./NVIDIA*9631* --kernel-source-path=/usr/src/linux-headers-`uname -r`

---

### Post by super.rad on 2007-04-06
```
em@em-ubuntu:~$ lspci | grep "VGA"
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0392 (rev a1)
```

the card is a Nvidia 7600 GS

---

### Post by super.rad on 2007-04-06
ok i have updated to the newest nvidia driver, turned out i had to remove the packages (nvidia-glx, linux-restricted-modules-common) and then download and install them again

---

### Post by super.rad on 2007-04-06
i tried installing beryl from the [this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29") but when i reboot it fails to load xserver, this is the log file i get
> X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux em-ubuntu 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr  7 01:10:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA 7600"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
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
(II) PCI: 00:00:0: chip 1002,5950 card 103c,2a24 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 103c,2a24 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a24 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a24 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a24 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a24 rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a24 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 103c,2a24 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,2a25 rev 02 class 04,01,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0392 card 107d,2a52 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 14f1,8800 card 0070,9002 rev 05 class 04,00,00 hdr 80
(II) PCI: 02:01:2: chip 14f1,8802 card 0070,9002 rev 05 class 04,80,00 hdr 80
(II) PCI: 02:01:4: chip 14f1,8804 card 0070,9002 rev 05 class 04,80,00 hdr 80
(II) PCI: 02:03:0: chip 10ec,8139 card 103c,2a24 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1106,3044 card 103c,2a24 rev 80 class 0c,00,10 hdr 00
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
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf6000000 - 0xf8ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xfcffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0392) rev 161, Mem @ 0xf6000000/24, 0xd0000000/28, 0xf7000000/24, I/O @ 0xef00/7
(--) PCI: (2:1:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xfb000000/24
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
(II) PCI I/O resource overlap reduced 0x00004100 from 0x0000411f to 0x000040ff
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xffffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfcffe000 - 0xfcffe7ff (0x800) MX[B]
	[1] -1	0	0xfcfff000 - 0xfcfff0ff (0x100) MX[B]
	[2] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[3] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[4] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[6] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[16] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[17] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[18] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[19] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[20] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[22] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[23] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[24] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfcffe000 - 0xfcffe7ff (0x800) MX[B]
	[1] -1	0	0xfcfff000 - 0xfcfff0ff (0x100) MX[B]
	[2] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[3] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[4] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[5] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[6] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[7] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[16] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[17] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[18] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[19] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[20] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[22] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[23] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[24] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
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
	[4] -1	0	0xfcffe000 - 0xfcffe7ff (0x800) MX[B]
	[5] -1	0	0xfcfff000 - 0xfcfff0ff (0x100) MX[B]
	[6] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[7] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[10] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[11] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[12] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[13] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[22] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[23] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[24] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[25] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[28] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[31] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
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
	compiled for 4.0.2, module version = 1.0.9746
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
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
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
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
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
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
	[4] -1	0	0xfcffe000 - 0xfcffe7ff (0x800) MX[B]
	[5] -1	0	0xfcfff000 - 0xfcfff0ff (0x100) MX[B]
	[6] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[7] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[10] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[11] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[12] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[13] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[22] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[23] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[24] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[25] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[28] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[31] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcffe000 - 0xfcffe7ff (0x800) MX[B]
	[5] -1	0	0xfcfff000 - 0xfcfff0ff (0x100) MX[B]
	[6] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[7] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[8] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[10] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[11] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[12] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[13] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[25] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[26] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[27] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[28] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[29] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[30] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[31] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[32] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[33] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[34] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.68
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     AOC WJ1780PI (CRT-0)
(--) NVIDIA(0): AOC WJ1780PI (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf7000000 - 0xf7ffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfcffe000 - 0xfcffe7ff (0x800) MX[B]
	[8] -1	0	0xfcfff000 - 0xfcfff0ff (0x100) MX[B]
	[9] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[10] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[11] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[12] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[13] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[14] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[15] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[16] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[17] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[18] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[19] -1	0	0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] 0	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[29] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[30] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[31] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[32] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[33] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[34] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[35] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[36] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[37] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[38] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
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
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

can anyone tell me what i've done wrong and how to fix it? thanks

---

### Post by locke.dragon on 2007-04-06
sadly, i can't tell you how to fix your box because i'm new to ubuntu and linux in general.  but i can say that i successfully installed beryl with this tutorial.

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

hope that helps!  :D

---

### Post by super.rad on 2007-04-11
thanks but i've got compiz working so decided to stick with that, might give beryl another try at some point but compiz is fine for now

---

