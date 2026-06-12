---
title: "Blank screen of death"
date: 2005-11-06
forum: Desktop Environments
---

### Post by awtomlinson on 2005-11-06
I can no longer log in using either Gnome or Failsafe Gnome.  When I log in, I get a blank screen with only my mouse cursor.  I can move the cursor around, but can't access anything else, either via the mouse or keyboard shortcut keys.  Nothing has changed on my system, except I installed xine and vlc.  I can only log in via the Failsafe Terminal.  When I do a sudo startx from the failsafe terminal, I get the following error:

Xauth:  creating new authority file /home/myname/.serverauth.9086
X: Warning:  process set to priority -1 instead of requested priority 0
Fatal Server Error

Server is already active for display 0
If this server is no longer running, remove /tmp/.XO-lock & start again

So, I removed /tmp/.XO-lock, but the same issue occurs.  someone, please help!!!

---

### Post by Ampersand on 2005-11-07
One thing you could try would be pressing Ctrl, Alt and + to cycle through resolutions after you log in. Then there's always
```
sudo dpkg-reconfigure xserver-xorg
```

If these don't work, log in at a terminal and run

```
 cat /var/log/Xorg.0.log | less
```

and scroll through it to see if there are any lines starting with (EE). If there are, copy them out, then post them here.

---

### Post by awtomlinson on 2005-11-10
[QUOTE=Ampersand]One thing you could try would be pressing Ctrl, Alt and + to cycle through resolutions after you log in. Then there's always
```
sudo dpkg-reconfigure xserver-xorg
```

If these don't work, log in at a terminal and run

```
 cat /var/log/Xorg.0.log | less
```

and scroll through it to see if there are any lines starting with (EE). If there are, copy them out, then post them here.[/QUOTE]

ctrl, alt and + did nothing.  the screen isn't blank anymore, but its stuck on the gnome splash (ubuntu) screen.  nothing in my Xorg.0.log file began with (EE).  remember, nothing has changed, except i installed vlc, xine, and dvdshrink anad dvddecrypter in wine.  i have posted the Xorg.0.og file in a previous thread, now it is considerably longer, and i don't know why.  my system specs:

amd athlon xp 3200+ processor
1 gb kingston ram
nvidia 5600 ultra video card
sony 17 inch trinitron monitor

i'm using the nv video driver, not a proprietary nvidia driver.  i will post my Xorg.0.log file next.

---

### Post by awtomlinson on 2005-11-10
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:
36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 10 00:11:43 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SONY HMD-A20"
(**) |   |-->Device "NVIDIA Corporation NV31 [GeForce FX 5600 Ultra]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fon
ts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(II) PCI: 00:00:0: chip 10de,01e0 card 147b,1c00 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 147b,1c00 rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 147b,1c00 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 147b,1c00 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 147b,1c00 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 147b,1c00 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 147b,1c00 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 147b,1c00 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 147b,1c00 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 147b,1c00 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,006e card 147b,1c00 rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 02:00:0: chip 10de,0311 card 270f,1944 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x00009000 - 0x0000afff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
[0] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NV31 [GeForce FX 5600 Ultra] rev 161, Mem @ 0xd8000000/24, 0xd0000000/27
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [1] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [2] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [3] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [4] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [5] -1  0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [6] -1  0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [7] -1  0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [8] -1  0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [9] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [10] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [11] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [12] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [13] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [14] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [15] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [1] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [2] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [3] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [4] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [5] -1  0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [6] -1  0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [7] -1  0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [8] -1  0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [9] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [10] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [11] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [12] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [13] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [14] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [15] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
 [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [6] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [7] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [8] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [9] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [10] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [11] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [12] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [13] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [14] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [19] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [20] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [21] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(WW) Ignoring request to load module GLcore
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
(II) Primary Device is: PCI 02:00:0
(--) Chipset GeForce FX 5600 Ultra found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [6] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [7] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [8] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [9] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [10] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [11] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [12] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [13] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [14] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [19] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [20] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [21] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
[2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [6] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]

---

### Post by awtomlinson on 2005-11-10
Part II:

[7] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [8] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [9] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [10] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [11] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [12] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [13] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [14] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [22] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [23] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [24] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [25] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [26] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [27] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5600 Ultra"
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
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xD8000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
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
(II) NV(0): Manufacturer: SNY  Model: 1370  Serial#: 5660506
(II) NV(0): Year: 2001  Week: 29
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate  Composite
(II) NV(0): Max H-Image Size [cm]: horiz.: 33  vert.: 24
(II) NV(0): Gamma: 2.50
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.605
(II) NV(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 720x400@88Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@87Hz (interlaced)
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) NV(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NV(0): Ranges: V min: 48  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 200 MHz
(II) NV(0): Monitor name: SONY HMD-A200
(II) NV(0): Serial No: 5660506
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): SONY HMD-A20: Using default hsync range of 30.00-70.00 kHz
(II) NV(0): SONY HMD-A20: Using default vrefresh range of 48.00-120.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
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
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
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
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) NV(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) NV(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) NV(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
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
(**) NV(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) NV(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) NV(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
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
(--) NV(0): Display dimensions: (330, 240) mm
(--) NV(0): DPI set to (98, 108)
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
        [0] 0   0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
[1] 0   0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B]
        [2] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [8] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [9] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [10] -1 0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [11] -1 0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [12] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [13] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [14] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [15] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [16] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [17] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [23] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [24] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [25] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [26] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [27] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [28] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [29] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xd0000000,0x8000000)
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

---

### Post by awtomlinson on 2005-11-10
o.k.  previously using ctrl+alt+backspace would only freeze up the mouse cursor, but now it works, and i get the following errors:

symbol _glxgetActive from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved

symbol _glxgetActive from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved

(EE) failed to initialize GLX extension (NVIDIA X driver not found)

xauth:  error in locking authority file /home/myloginname/.Xauthority

---

### Post by rjwood on 2005-11-10
I have had this happen to me twice once from k3b and once from one of the other cd programs.

from the terminal in your home directory```
ls -a
``` 
look for the xauthority file and remove it
```
rm (name of file)
``` 
type exit to get out of the terminal
and log in

---

### Post by awtomlinson on 2005-11-10
i already did a:

sudo rm .Xauthority in my home directory, and it didn't work

---

### Post by rjwood on 2005-11-10
```
sudo apt-get install nvidia-glx
```

---

### Post by awtomlinson on 2005-11-10
[QUOTE=rjwood]```
sudo apt-get install nvidia-glx
```[/QUOTE]

i will try this when i get home, but i had installed this previously, and i have not uninstalled it, so will this help?  when i boot up my pc, i get the nvidia logo, and then i get the ubuntu gui login screen (gdm).  when i enter my login name and password, i get the grey screen with only my mouse cursor.  sometimes i get the gnome (ubuntu) splash screen on top of the blank/grey screen.  but, again, the blank/grey screen remains, and i can only move my mouse cursor.

---

### Post by rjwood on 2005-11-10
by any chance have you installed enlightenment or xcompmgr?

---

### Post by awtomlinson on 2005-11-10
[QUOTE=rjwood]by any chance have you installed enlightenment or xcompmgr?[/QUOTE]

nope, i have installed neither.  don't even know what xcompmgr is.

---

### Post by rjwood on 2005-11-10
well then I would do first

sudo nvidia-glx-config enable

if that doesn't work try

```
sudo dpkg-reconfigure xserver-xorg
``` 

and go through that process. I would just accept the automatic settings.

I would also remove the xine and vlc and maybe even the wine one step at a time.
until you see which one is causing the problem.

---

### Post by awtomlinson on 2005-11-10
[QUOTE=rjwood]well then I would do first

sudo nvidia-glx-config enable

if that doesn't work try

```
sudo dpkg-reconfigure xserver-xorg
``` 

and go through that process. I would just accept the automatic settings.

I would also remove the xine and vlc and maybe even the wine one step at a time.
until you see which one is causing the problem.[/QUOTE]

yesterday, i did the sudo dpkg-reconfigure xserver-xorg & it didn't help.  when i first installed breezy when it was originally released, i did the sudo nvidia-glx-config enable.  should i do this again?

---

### Post by awtomlinson on 2005-11-12
o.k.  i uninstalled nvidia-glx and reinstalled it.  then i did

sudo nvidia-glx-config enable

the same issue occurs.  i've had breezy since its official release, and i've had a total of 2-3 weeks of downtime due to xorg issues.  that's more than half of the time that breezy has been out.  i'm ready to go back to hoary, or can anyone help with trashing xorg and using xfree86 on breezy?  i loath breezy, i'm getting jealous about how stable my winxp partition is.  someone please help!!!!!!!!!!!

---

### Post by awtomlinson on 2005-11-12
anyone?!

---

### Post by awtomlinson on 2005-11-12
anyone??

---

### Post by Sutekh on 2005-11-13
This sounds scarily like my issue.  

What happens when you change the console... ie 'Alt Ctl F7' and 'Alt Ctl F8'??  Try this at the GDM login screen, before attempting to log on.

---

### Post by awtomlinson on 2005-11-13
[QUOTE=Sutekh]This sounds scarily like my issue.  

What happens when you change the console... ie 'Alt Ctl F7' and 'Alt Ctl F8'??  Try this at the GDM login screen, before attempting to log on.[/QUOTE]

i will try this in a few hours.  were you able to resolve the issue?

---

### Post by Sutekh on 2005-11-13
I'm still trying to no avail.  Not the news you want to hear!  

For me I'm pretty sure that my computer is trying to run GNOME on console 8, but not getting anywhere.  Because of this I can't log into GNOME from console 7 (the one that comes up by default).  I can't kill the process on console 8 either.  

I have alot of the symptoms you have: Fatal server error - .X0-lock, Xauthority.  The main difference I can see is that your Xorg.log actually has some errors, I only have warnings.

[MY blank screen of death]("http://ubuntuforums.org/showthread.php?t=88175")

---

### Post by awtomlinson on 2005-11-18
Sutekh, when I change the console... ie 'Alt Ctl F7' and 'Alt Ctl F8' from either the GDM or when I get the black/blank screen of death, the following occurs:

sometimes I seem to be running 3 separate sessions, sometimes 2.  I cycle through the GDM screen or the screen of death if I have logged in already, and the other screen is the startup screen, when all of the Linux services are starting, such as ntp, cups, etc.  this screen will freeze on "Checking Battery State" even though I'm not using a laptop, but a desktop.  on this screen, Ctrl+Del+Backspace does not do anything.

Someone, anyone, please HELP!!

---

### Post by awtomlinson on 2005-11-18
sorry, don't know if its running different sessions or different consoles.  also, i meant Ctrl+Alt+Backspace, not Ctrl+Del+Backspace

---

### Post by awtomlinson on 2005-11-20
o.k. i am able to boot into the gui with the live cd.  so, i want to copy my xorg.log file from the boot cd to my installed breezy partition.  how can i email this to myself and copy and paste the file?  lynx does not seem to work well.

---

### Post by Sutekh on 2005-11-20
[QUOTE=awtomlinson]o.k. i am able to boot into the gui with the live cd.  so, i want to copy my xorg.log file from the boot cd to my installed breezy partition.  how can i email this to myself and copy and paste the file?  lynx does not seem to work well.[/QUOTE]

Do you want to open xorg.log to copy the text? Try gedit
```

gedit /var/log/xorg.0.log
```
Do you have any removable media (USB, SD Cards)?  That would be an easy way too.
You could also mount your breezy partition then copy the file across.
```

sudo fdisk -l 
```
will list all your available partitions. Then 

```

sudo mkdir /mnt/temp
sudo mount /dev/**hda1** /mnt/temp 
```
will mount **hda1** or whatever partition you want to the directory /mnt/temp.  If you have trouble deciding which partition to mount, can you paste the output from the fdsik command here?



[QUOTE=awtomlinson]sometimes I seem to be running 3 separate sessions, sometimes 2. I cycle through the GDM screen or the screen of death if I have logged in already, and the other screen is the startup screen, when all of the Linux services are starting, such as ntp, cups, etc. this screen will freeze on "Checking Battery State" even though I'm not using a laptop, but a desktop. on this screen, Ctrl+Del+Backspace does not do anything. [/QUOTE]

That's exactly what was happening on my PC.  In the end I got fed up and reinstalled!  That "loading screen" on console 8 is still there and I think that that's normal, as it is there if GDM is running and is not if I stop GDM.  If anyone else would like to try this to verify for us.

I think the problem I had that my user's GNOME settings were munged.  I could log into GNOME with a new user and had no problems.  Looking back I think an easier fix would have been to transfer my files from my original user to the new one.  

Have you tried creating a new user and logging in to see what happens??

---

### Post by spartas on 2005-11-20
If I saw this thread earlier, I possibly could have helped you (I've had that happen at least 3 times so far; but then again I like running the latest and greatest).

If you get that again, remove your hidden .gnome, .gnome2, and .gnome2_private directories.  This will remove any customizations you've made to gnome (panels, sessions, ...), but at least you will be able to login.

---

### Post by awtomlinson on 2005-11-21
thanks spartas, i'll try that.  if this does not work, sutekh, can you tell me how to move all of my current login files to the newly created login name?

---

### Post by Sutekh on 2005-11-22
Yeah go for the hidden gnome directories first and see what happens.


To create a new user, I just tried this, you will need to log into a console or the failsafe terminal, then following the [Ubuntu Wiki – Add Users HOWTO]("https://wiki.ubuntu.com/AddUsersHowto"):
```

sudo adduser <newuser>

```
Then you should be able to log into GNOME with that new user.  This new user won’t have the same privileges that your old user, so here's what I did.  In a terminal I entered
```

newuser@ubuntu:~$ groups olduser
olduser : olduser adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
newuser@ubuntu:~$

```
This lists all the groups that my olduser belonged to.  So that the new user has all the privileges as the old one I used the following commands
```

newuser@ubuntu:~$ sudo adduser newuser adm
Adding user `newuser' to group `adm'...
Done.
newuser@ubuntu:~$ sudo adduser newuser dialout
Adding user `newuser' to group `dialout'...
Done.
...

```
This puts the newuser into the groups that the olduser was in, yours may be different to mine.  If you need to try this and are unsure just post what 
```

groups olduser

```
spits out.

I also tried this method in the Ubuntu guide but it didn't seem to have any effect, maybe I needed to reboot, but didn't.  [Ubuntuguide - Allow More Sudoers]("http://ubuntuguide.org/#allowmoresudoers")

To the matter of copying files, when I've had to do this I've only kept files and folders that were not hidden ones.  With the exception of customised .bashrc, .bash_aliases, firefox bookmarks, etc.  

Once you can log in with the new user, you can either use sudo commands in the terminal, or [browse nautilus as root]("http://www.ubuntuguide.org/#browsefilesfoldersasrootnautilus") to copy your files.  Which ever you find easier.  I'd probably only copy your documents and forget settings/customisations as they sound like the problem.

Don't delete your old user until you are sure you have everything you need.

Hope all this makes sense and works for you, and you get back into GNOME!


P.S. Were you mounting a Windows NTFS partition in Ubuntu?  If not, don't bother reading on.

Did that "loading screen", the one with the checking battery state and such, have a Mounting local filesystems part at the top? And did it fail because of the NTFS partition?  Mine did before when I had problems, but now after a re-install it is fine.

---

### Post by awtomlinson on 2005-11-22
deleting the hidden .gnome, gnome_private, .gnome2, and .gnome2_private directories did not solve the issue.  i did create a new user, and i am able to log in now, but i have many other issues, and i don't think that they're related to user privileges.  i have the following issues:

1.  can't open a terminal, receive an "error creating child process for this terminal" error
2.  can't run the update manager
3.  can't access the volume control, receive a "no volume control elements and/or devices" error
4.  i mounted my /home partition, but some of the directories are displayed as an unknown filetype, much like a windows file is displayed

Sutekh:
Did that "loading screen", the one with the checking battery state and such, have a Mounting local filesystems part at the top? And did it fail because of the NTFS partition?  Mine did before when I had problems, but now after a re-install it is fine.[/QUOTE]

i'm not sure about this, but i will check when i get home.  if this is the case, how can i set ubuntu to not automatically mount the ntfs partition?

---

### Post by awtomlinson on 2005-11-23
so, in other words, i can't do anything, because i can't open a terminal.  sounds like i definitely need to reinstall.  but, which directories in my /home directory should i ensure that i delete so this issue does not occur when i reinstall ubuntu?

---

### Post by Burning Bronx on 2005-11-23
Reinstalling is a bit of a double edge solution as you would lose your customizations and sooner or later you may get the same problem. Have you tried searching the bugzilla database? I suggest you do that and/or if you don't find a solution - post this bug. It sounds way too scary to be left unfixed.

---

### Post by awtomlinson on 2005-11-23
could someone please search the bugzilla database?  i can't do it until tonight.  this is killing me, i've been ubuntuless for around 3 weeks now.

---

### Post by awtomlinson on 2005-11-23
checked bugzilla for the checking battery state error and the terminal child process error, and neither were in the database.  what next?

---

### Post by awtomlinson on 2005-11-23
sorry, guess i will post these issues on bugzilla

---

### Post by Sutekh on 2005-11-23
> **awtomlinson]...
1.  can't open a terminal, receive an "error creating child process for this terminal" error
...[/QUOTE]

Does this error have at the end a  (permissiond denied) or a (no such file or directory)?

[QUOTE=awtomlinson]...
2. can't run the update manager
...[/QUOTE]

When you say this I'm taking it to mean Synaptic.  Do you get any kind of error messsage.  I'd say run it from a terminal to see what you get, but obviously you can't do that.  So first gotta get that terminal up.

[QUOTE=awtomlinson]...
3.  can't access the volume control, receive a "no volume control elements and/or devices" error
...[/QUOTE]

I found this error on google quite a bit said:**
> removing and replacing the volume panel[/URL], in another case it was fixed by
[Remove removing gnome mixer applet settings]("http://fcp.fedoranews.org/modules/newbb/viewtopic.php?topic_id=16357&forum=23"), still in another it was resolved by
[editing the gnome2/session file]("http://gnomesupport.org/forums/viewtopic.php?t=10077").

Maybe one of those solutions could help.

As a matter of interest when you deleted .gnome, .gnome2, etc folders, did you do that for the new user?

[QUOTE=awtomlinson]...
4. i mounted my /home partition, but some of the directories are displayed as an unknown filetype, much like a windows file is displayed
...

I don't have anything to offer on this point yet, sorry.

---

### Post by awtomlinson on 2005-11-23
the terminal error was just as i typed it, nothing following it.  i deleted the .gnome, .gnome2, .gnome_private, and .gnome2_private folders only for my original account.  i can't open synaptic or the update manager.  when i select either, i am prompted for my password, which i enter, then nothing happens, they do not open.

---

### Post by Sutekh on 2005-11-23
Can you change to a console (don't bother quitting GNOME, if you are using it currently), using Alt+Ctl+F2, log in as the new user, and check which groups the new user is in... just type in groups at the prompt.  What do you get?

---

### Post by awtomlinson on 2005-11-23
sutekh, i did this and added the new user to all of the groups that my previous user belonged to.  i logged out, & tried to log back in as the new user.  the same issues occured, so i rebooted.  the same issues still occur.  this is mind boggling, as the terminal and sound issues never occurred before with my old user account.  again, the only changes that i made were to install xine & vlc.  i've had my fill of this, so i'm definitely going to reinstall.  my question is, what hidden directories in my /home partition do i need to delete once i've mounted it under the fresh install?  i most definitely don't want this to happen ever again.

---

### Post by awtomlinson on 2005-11-23
sutekh, i was checking the ntfs mount as you suggested earlier.  there were no errors on the ntfs partition mount, but i do have the following error:

Setting up general console font...oryed with error m [ok]

following this are several other startup processes that are fine, ending with the Checking Battery State freeze.

---

### Post by Sutekh on 2005-11-23
Ok fair enough, you've held out longer than I did!  It can be very frustrating.  

I don't know what folders are causing the problem.  When I re-installed, I re-formatted my / and my /home partition, so they all went.  This will be a problem if you've got a lot of data, and nowhere to store it during the re-install.    

I'm not sure if there are any issues with re-installing and using the same user name.  Will the installer write over configuration files? or leave everything?  Sorry I can't be more help there.

---

### Post by Sutekh on 2005-11-23
[QUOTE=awtomlinson]sutekh, i was checking the ntfs mount as you suggested earlier.  there were no errors on the ntfs partition mount, but i do have the following error:

Setting up general console font...oryed with error m [ok]

following this are several other startup processes that are fine, ending with the Checking Battery State freeze.[/QUOTE]

On my new install of Breezy, I still have that "loading screen" and it has those startup processes up to the checking battery state.  I don't have any problems now, so I don't think that is a problem.

Excuse the bluriness in the pic, I couldn't use the flash.  This is from my fresh install, working with no problems.  GNOME on Alt Ctl F7 and this screen on Alt Ctl F8.

---

### Post by awtomlinson on 2005-11-23
o.k. so which hidden folders in my /home partition should i delete so i don't screw up the fresh install?

---

### Post by Sutekh on 2005-11-23
That's just it, I don't know which ones are stuffing things up for you.  You could possibly use the installer, and make a new user, then copy your data from the old user to the new one.

---

### Post by awtomlinson on 2005-11-24
o.k.  i'm just gonna reinstall & delete all hidden folders

---

### Post by Sutekh on 2005-11-24
Good luck and fingers crossed.

---

### Post by awtomlinson on 2005-11-24
well, i did a fresh install and all is well.  i didn't even have the issues that i had on the original fresh install with xfs and totem.  everything works.  i haven't mounted my /home partition yet, but i will delete all hidden directories just to make sure.  however, my major issue is again that some of my directories on my /home partition show as an unknown file type & the file size is unknown.  the directories must be the same size as they were before they were unrecognized because i have the same amount of free space on the /home partition as i did before this issue occured.  does anyone know how i can recover the data from these directories?  they are very important.  sutekh, thank you and everyone else who helped.

---

### Post by Sutekh on 2005-11-24
Well I don't know how much I helped in the end, since you had to re-install, but I guess it's the thought that counts.  I found it very hard NOT to re-install, as it takes around three-quarters of an hour to get things going again.  Compared to a horrible 3 hours with WinXP.

When you say you haven't mounted /home yet, do you mean that the installer created another separate /home?

Still not sure what's happening with those unknown filetype folders of yours...  Do you get any kind of error?  Or is this unknown filetype and size displayed in a browser?  If you get some kind of error, paste it fully here... makes it easier to look for answers.

---

### Post by awtomlinson on 2005-11-25
yes, the reinstall created a new /home on my root partition.  i have my original /home on another partition.  there is no error for the unknown file types, the size of the file is also unknown.  these are actually supposed to be directories, not files.  the true file size remains as they were originally, as my free hard drive space is unchanged since this issue.  when i do mount this /home partition, it is very slow to access via the new breezy install.  it freezes on almost every file or directory that i try to access.

---

