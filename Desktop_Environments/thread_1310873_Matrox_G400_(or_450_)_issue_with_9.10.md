---
title: "Matrox G400 (or 450 ?) issue with 9.10"
date: 2009-11-02
forum: Desktop Environments
---

### Post by destroyedlolo on 2009-11-02
Hi all,

I have a dual monitor card installed on a old PC which is identified as 

```
(--) PCI:*(0:1:0:0) 102b:0525:102b:0641 Matrox Graphics, Inc. MGA G400/G450 rev 130, Mem @ 0xd8000000/33554432, 0xda000000/16384, 0xdb000000/8388608, BIOS @ 0x????????/131072
```Unfortunately, I can't enable **compiz**, and "preferences/display" shows only 1 screen which is "unknown".

_**Compiz**_ :

I had a look on the internet, all speaking about Ubuntu older than 9.10.
Some said I have to modify /etc/X11/xorg.conf. It seems I have to modify the Depth from 24 to 16 but ... **where ? **I can't put it in /etc/X11/xorg.conf because the corresponding directive has to be enclosed in a section ... which I don't have.

Some others pages said I have also to upload the driver from Matrox but the like is gone.

[U]**Dual screen :**

[/U]Why it's still unknown ?
I connected only 1 screen up to now, is a second screen created when I'll connect a second one or do I have to change something ?

Thanks for your help.

Laurent

PS: Xorg.log bellow

```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux chose 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=659e89c0-926e-40ec-98e6-17b106fc10a9 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  1 22:08:33 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 102b:0525:102b:0641 Matrox Graphics, Inc. MGA G400/G450 rev 130, Mem @ 0xd8000000/33554432, 0xda000000/16384, 0xdb000000/8388608, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default mga Device 0"
        Driver    "mga"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default mga Screen 0"
        Device    "Builtin Default mga Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default mga Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default mga Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default mga Device 0"
(==) No monitor specified for screen "Builtin Default mga Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
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
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.4.11
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
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
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
    mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
    mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
    mgag200 eW Nuvoton, mgag400, mgag550
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(--) MGA(0): Chipset: "mgag400" (G450)
(--) MGA(0): Linear framebuffer at 0xD8000000
(--) MGA(0): MMIO registers at 0xDA000000
(--) MGA(0): Pseudo-DMA transfer window at 0xDB000000
(II) MGA(0): Creating default Display subsection in Screen section
    "Builtin Default mga Screen 0" for depth/fbbpp 24/32
(==) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using HW cursor
(==) MGA(0): Using XAA acceleration
(--) MGA(0): Video BIOS info block at offset 0x07720
(==) MGA(0): VideoRAM: 32768 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:E-EDID segment register" registered at address 0x60.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C monitor info
(II) MGA(0): Manufacturer: DEL  Model: 730b  Serial#: 911884620
(II) MGA(0): Year: 1998  Week: 34
(II) MGA(0): EDID Version: 1.1
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MGA(0): Sync:  Separate
(II) MGA(0): Max Image Size [cm]: horiz.: 30  vert.: 23
(II) MGA(0): Gamma: 2.85
(II) MGA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MGA(0): redX: 0.625 redY: 0.340   greenX: 0.285 greenY: 0.605
(II) MGA(0): blueX: 0.150 blueY: 0.065   whiteX: 0.281 whiteY: 0.311
(II) MGA(0): Supported established timings:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@75Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported standard timings:
(II) MGA(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) MGA(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) MGA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) MGA(0): Supported detailed timing:
(II) MGA(0): clock: 28.3 MHz   Image Size:  250 x 184 mm
(II) MGA(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) MGA(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) MGA(0): Serial No: 85270L6ZAL88
(II) MGA(0): Monitor name: DELL D1028LR
(II) MGA(0): Ranges: V min: 48 V max: 120 Hz, H min: 30 H max: 69 kHz,
(II) MGA(0): EDID (in hex):
(II) MGA(0):     00ffffffffffff0010ac0b734c415a36
(II) MGA(0):     22080101081e17b9e800b2a057499b26
(II) MGA(0):     10484fa54a0061594559818031590101
(II) MGA(0):     010101010101100bd0b4205e6310126c
(II) MGA(0):     6208fab80000001a000000ff00383532
(II) MGA(0):     37304c365a414c38380a000000fc0044
(II) MGA(0):     454c4c2044313032384c520a000000fd
(II) MGA(0):     0030781e45ff000a2020202020200080
(II) MGA(0): end of monitor info
(II) MGA(0): EDID vendor "DEL", prod id 29451
(II) MGA(0): Using EDID range info for horizontal sync
(II) MGA(0): Using EDID range info for vertical refresh
(II) MGA(0): Printing DDC gathered Modelines:
(II) MGA(0): Modeline "720x350"x0.0   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MGA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) MGA(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) MGA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MGA(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 17 MHz
(--) MGA(0): Max pixel clock is 600 MHz
(II) MGA(0): <default monitor>: Using hsync range of 30.00-69.00 kHz
(II) MGA(0): <default monitor>: Using vrefresh range of 48.00-120.00 Hz
(II) MGA(0): Estimated virtual size for aspect ratio 1.3043 is 1280x1024
(II) MGA(0): Clock range:  17.75 to 600.00 MHz
(II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "1280x960" (hsync out of range)
(II) MGA(0): Not using default mode "640x480" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1360x768" (width too large for virtual size)
(II) MGA(0): Not using default mode "1360x768" (width too large for virtual size)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) MGA(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) MGA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x600" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1280x1024 (pitch 1280)
(**) MGA(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) MGA(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) MGA(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) MGA(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) MGA(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) MGA(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) MGA(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) MGA(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) MGA(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) MGA(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) MGA(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) MGA(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) MGA(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) MGA(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) MGA(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) MGA(0): Modeline "1024x768"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) MGA(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MGA(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) MGA(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) MGA(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MGA(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) MGA(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) MGA(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) MGA(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) MGA(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) MGA(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) MGA(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) MGA(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) MGA(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) MGA(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MGA(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MGA(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) MGA(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) MGA(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) MGA(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) MGA(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) MGA(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) MGA(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) MGA(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) MGA(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) MGA(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MGA(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) MGA(0): *Driver mode "720x350": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "720x350"x70.1   28.32  720 738 846 900  350 388 390 449 +hsync -vsync (31.5 kHz)
(**) MGA(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) MGA(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) MGA(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) MGA(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) MGA(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) MGA(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) MGA(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) MGA(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) MGA(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) MGA(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) MGA(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) MGA(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MGA(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) MGA(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) MGA(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) MGA(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) MGA(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MGA(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) MGA(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) MGA(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) MGA(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MGA(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) MGA(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MGA(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) MGA(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MGA(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) MGA(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MGA(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) MGA(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) MGA(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) MGA(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) MGA(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) MGA(0): Display dimensions: (300, 230) mm
(**) MGA(0): DPI set to (108, 113)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 16 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(II) MGA(0): [drm] bpp: 32 depth: 24
(II) MGA(0): [drm] Sarea 2200+664: 2864
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "mga" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) MGA(0): [drm] Using the DRM lock SAREA also for drawables.
(II) MGA(0): [drm] framebuffer handle = 0xd8000000
(II) MGA(0): [drm] added 1 reserved context for kernel
(II) MGA(0): X context handle = 0x1
(II) MGA(0): [drm] installed DRM signal handler
(II) MGA(0): [dri] visual configs initialized
(II) MGA(0): Memory manager initialized to (0,0) (1280,2047)
(II) MGA(0): Largest offscreen area available: 1280 x 1023
(II) MGA(0): Reserved back buffer at offset 0xa00000
(II) MGA(0): Reserved depth buffer at offset 0xf00000
(II) MGA(0): Reserved 12288 kb for textures at offset 0x1400000
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    Solid filled trapezoids
    8x8 mono pattern filled rectangles
    8x8 mono pattern filled trapezoids
    Indirect CPU to Screen color expansion
    Screen to Screen color expansion
    Solid Lines
    Dashed Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        9 256x256 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(II) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(II) MGA(0): [DRI] installation complete
(II) MGA(0): [drm] Mapped 128 DMA buffers
(II) MGA(0): [drm] dma control initialized, using IRQ 10
(II) MGA(0): Direct rendering enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/mga_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
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
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.

```

---

### Post by tormod on 2009-11-02
Create an /etc/X11/xorg.conf like this:
```
Section "Device"
       Identifier "my-mga"
       Driver "mga"
EndSection

Section "Screen"
       Identifier "my-screen"
       Device "my-mga"
       DefaultColorDepth 16
       SubSection "Display"
               Virtual 1024 768
       EndSubSection
EndSection
```
The SubSection with the Virtual setting is not needed, but would not hurt for single-screen (or clone) setup. Remove it if you want dual-screen with a large virtual desktop.

---

### Post by destroyedlolo on 2009-11-02
Thanks Tormod,

Unfortunately, Visual effects wont start :(
Any clue ?

---

### Post by destroyedlolo on 2009-11-02
I've tried also to install driver from Matrox but doesn't work :(

---

### Post by tormod on 2009-11-02
I will have to see your logs then. The best is to file a bug, using: ubuntu-bug xserver-xorg-video-mga

EDIT: I already saw your Xorg.0.log :) But also the output from: LIBGL_DEBUG glxinfo
would be good, and .xsession-errors.

---

### Post by destroyedlolo on 2009-11-03
It's done, I've created a bug report.

Thanks

Laurent

---

### Post by tormod on 2009-11-03
Would be nice to link to the bug report for those who are interested.

EDIT: Searched for it: [https://bugs.launchpad.net/bugs/473401](https://bugs.launchpad.net/bugs/473401)

---

### Post by destroyedlolo on 2009-11-03
I was waiting for the confirmation eMail to get the number, but you were faster ;)

---

