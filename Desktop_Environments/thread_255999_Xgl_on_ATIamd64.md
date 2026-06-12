---
title: "Xgl on ATI/amd64"
date: 2006-09-12
forum: Desktop Environments
---

### Post by briansrapier on 2006-09-12
I know this subject gets a lot of play on these forums, but I cannot seem to find a fix for my issues...

I have a laptop with an ATI radeon mobility M10 (9700) graphics card that I want to get Xgl working on. My main goal is to have as much of the 'eye candy' working for our sales guys to take to an upcoming trade show.

I have tried a number of Howtos, both on this site and elsewhere and seem to have had the most progress with this one:

[http://www.ubuntuforums.org/showthread.php?t=219336](http://www.ubuntuforums.org/showthread.php?t=219336)

But, the best I get is a blank screen on login. I can hear the normal sounds associated with logging in, but no graphics. Xorg works fine under the normal login (which I am now using to enter this post). 

SOURCES.LIST:
-------------
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
---
EOF
---

Here is the xorg.conf:

XORG.CONF
---------
...
Section "Module"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "type1"
        Load    "vbe"
EndSection
...
Section "Device"
Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
EndSection
...
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
...
Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option  "Composite"     "Enable"
EndSection
---
EOF
---

Here's 'startxgl.sh'

STARTXGL.SH
-----------
/usr/bin/Xgl :1 -ac -accel xv -accel glx:pbuffer -fullscreen &
DISPLAY=:1
exec gnome-session
---
EOF
---

My .drirc:

.DRIRC
------
<driconf>
        <device screen="1" driver="r200">
                <application name="Default">
                        <option name="allow_large_textures" value="2" />
                </application>
        </device>
</driconf>
---
EOF
---

And lastly, my Xorg.0.log:

XORG.0.LOG
----------
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux itt-3dlt2 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64
Build Date: 16 March 2006
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 12 10:56:01 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
...
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
...
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7
...
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 4.0.3
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 6.5.8
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) ATI: ATI driver (version 6.5.8) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
        ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
        ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
 ...(LIST OF SUPPORTED CARDS)...
(II) Primary Device is: PCI 01:00:0
(--) Chipset ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP) found
...
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Reloading /usr/lib/xorg/modules/drivers/radeon_drv.so
...
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xfeaf0000
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP)" (ChipID = 0x4e50)
(--) RADEON(0): Linear framebuffer at 0xf0000000
(--) RADEON(0): BIOS at 0xfeac0000
(II) RADEON(0): AGP card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.2.0 and kernel module version 1.24.0
(II) RADEON(0): AGP Fast Write disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(II) RADEON(0): Connector0: DDCType-0, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0):
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=46909632846912; xclk=21600
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: Samsung LTN154X1 WXGA
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Valid mode using on-chip RMX: 800x600
(II) RADEON(0): Valid mode using on-chip RMX: 640x480
(II) RADEON(0): Total number of valid FP mode(s) found: 3
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   68.90  1024 1288 1328 1408  768 800 803 816
(**) RADEON(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"   68.90  800 1288 1328 1408  600 800 803 816
(**) RADEON(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   68.90  640 1288 1328 1408  480 800 803 816
(**) RADEON(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x350"   68.90  640 1288 1328 1408  350 800 803 816
(**) RADEON(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x400"   68.90  640 1288 1328 1408  400 800 803 816
(**) RADEON(0):  Default mode "720x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "720x400"   68.90  720 1288 1328 1408  400 800 803 816
(**) RADEON(0):  Default mode "832x624": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"   68.90  832 1288 1328 1408  624 800 803 816
(**) RADEON(0):  Default mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   68.90  1280 1288 1328 1408  768 800 803 816
(**) RADEON(0):  Default mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   68.90  1280 1288 1328 1408  800 800 803 816
(**) RADEON(0):  Default mode "1152x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1152x768"   68.90  1152 1288 1328 1408  768 800 803 816
(==) RADEON(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
        of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
...
(**) RADEON(0): RADEONScreenInit f0000000 0
(**) RADEON(0): Map: 0xf0000000, 0x08000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x6fb930)
(**) RADEON(0): Read: 0x00240009 0x0002005c 0x00000000
(**) RADEON(0): Read: rd=9, fd=92, pd=2
(**) RADEON(0): RADEONSaveMode returns 0x6fb930
(II) RADEON(0): Dynamic Clock Scaling Disabled
(WW) RADEON(0): Enabling DRM support

        *** Direct rendering support is highly experimental for Radeon 9500
        *** and newer cards. The 3d mesa driver is not provided in this tree.
        *** A very experimental (and incomplete) version is available from Mesa CVS.
        *** Additional information can be found on [http://r300.sourceforge.net](http://r300.sourceforge.net)
        *** This message has been last modified on 2005-08-07.

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0x10005000
(II) RADEON(0): [drm] mapped SAREA 0x10005000 to 0x2aaab54bd000
(II) RADEON(0): [drm] framebuffer handle = 0xf0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x1f004e09 [AGP 0x1039/0x0755; Card 0x1002/0x4e50]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xe0000000
(II) RADEON(0): [agp] Ring mapped at 0x2aaab54bf000
(II) RADEON(0): [agp] ring read ptr handle = 0xe0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0x2aaab55c0000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xe0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0x2aaab55c1000
(II) RADEON(0): [agp] GART texture map handle = 0xe0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0x2aaab57c1000
(II) RADEON(0): [drm] register handle = 0xfeaf0000
(II) RADEON(0): [dri] Visual configs initialized
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() :
(**) RADEON(0):   mem_size         : 0x08000000
(**) RADEON(0):   agp_size         : 0x006fb7d0
(**) RADEON(0):   agp_base         : 0x006fb7d0
(**) RADEON(0):   MC_FB_LOCATION   : 0xf7fff000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1024x768       68.90  1024 1288 1328 1408   768  800  803  816 (24,32)
1024x768       68.90  1024 1288 1328 1408   768  800  803  816 (24,32)
(**) RADEON(0): Pitch = 8388736 bytes (virtualX = 1024, displayWidth = 1024)
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x6fc2e0
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x6fc2e0)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION   : 0xf7fff000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20187c7c
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Will use back buffer at offset 0xc00000
(II) RADEON(0): Will use depth buffer at offset 0xf00000
(II) RADEON(0): Will use 112640 kb for textures at offset 0x1200000
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(**) RADEON(0): DRI Finishing init !
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 217
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xf7fff000 is: 0xf7fff000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20187c7c
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 128
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
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
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 32
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
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) RADEON(0): RADEONSaveScreen(2)
---
EOF
---

---

