---
title: "XORG: Cannot make Cedarview + DisplayLink work together in 12.04"
date: 2016-01-22
forum: Desktop Environments
---

### Post by Nyyr on 2016-01-22
Hello,

I have an All-in-one PC with touch screen display and an USB DisplayLink touch screen connected. I want to use both displays but
when I start Xorg with DisplayLink as the first screen, desktop appears on it but the integrated display (cedarview graphics) stays black.
When I start Xorg with integrated display as the first screen, then the DisplayLink display stays in text mode (some booting messages).

Any idea how to make it work together?
(Ubuntu 12.04 with kernel 3.2.0-97-generic)

Xorg config:

```
Section "Device"
        Option      "DRIDisableVSync"   "False"
        Identifier  "Card0"
        Driver      "pvr"
        BusID       "PCI:0:2:0"
        Option      "SoftEXA"           "Off"
        Option      "FlipChain"         "On"
EndSection

Section "Monitor"
        Identifier      "IntegratedMonitor"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "IntegratedMonitor"
        DefaultDepth    16
EndSection

Section "ServerLayout"
        Identifier  "default screen"
        Option      "AIGLX"             "Off"
        Screen      "Screen0"
        Screen      "DisplayLinkScreen0"
EndSection


Section "Device"
        Identifier  "DisplayLinkDevice0"
        Driver      "displaylink"
        Option      "fbdev" "/dev/fb0"
        BusID       "USB"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor0"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen0"
        Device          "DisplayLinkDevice0"
        Monitor         "DisplayLinkMonitor0"
        DefaultDepth    16
        SubSection "Display"
                Depth   16
                Modes   "800x480"
        EndSubSection
EndSection

Section "ServerFlags"
        Option          "DefaultServerLayout"   "default screen"
EndSection
```

grep udl dmesg:

```
[    3.599933] udlfb: DisplayLink USB Display - serial #L11C039411
[    3.599945] udlfb: vid_17e9&pid_0211&rev_0172 driver's dlfb_data struct at f31b9800
[    3.599952] udlfb: console enable=1
[    3.599956] udlfb: fb_defio enable=1
[    3.599961] udlfb: shadow enable=1
[    3.601567] udlfb: vendor descriptor length:17 data:17 5f 01 0015 05 00 01 03 00 04
[    3.601578] udlfb: DL chip limited to 700000 pixel modes
[    3.601744] udlfb: allocated 4 65024 byte urbs
[    3.756327] udlfb: 800x480 valid mode
[    3.756337] udlfb: Reallocating framebuffer. Addresses will change!
[    3.757692] udlfb: 800x480 valid mode
[    3.757701] udlfb: set_par mode 800x480
[    3.761429] udlfb: open /dev/fb0 user=0 fb_info=f73ed000 count=1
[    3.762115] udlfb: set_par mode 800x480
[    3.774319] udlfb: set_par mode 800x480
[    3.778577] udlfb: DisplayLink USB device /dev/fb0 attached. 800x480 resolution. Using 1504K framebuffer memory
[    3.778678] usbcore: registered new interface driver udlfb
[    3.858134] udlfb: set_par mode 800x480
[    3.922755] udlfb: set_par mode 800x480
[    8.281762] udlfb: released /dev/fb0 user=0 count=0
[    8.294140] udlfb: open /dev/fb0 user=1 fb_info=f73ed000 count=1
```

Xorg.0.log (integrated screen first):

```
[    16.109]
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    16.109] X Protocol Version 11, Revision 0
[    16.109] Build Operating System: Linux 2.6.42-76-generic i686 Ubuntu
[    16.109] Current Operating System: Linux terminal2 3.2.0-97-generic #137-Ubuntu SMP Thu Dec 17 21:14:00 UTC 2015 i686
[    16.109] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-97-generic root=/dev/mapper/vg_00-lv_root ro nomodeset
[    16.109] Build Date: 12 February 2015  02:51:26PM
[    16.109] xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    16.109] Current version of pixman: 0.30.2
[    16.109]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    16.109] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.109] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 22 15:12:09 2016
[    16.123] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.124] (**) Option "defaultserverlayout" "default screen"
[    16.124] (**) ServerLayout "default screen"
[    16.124] (**) |-->Screen "Screen0" (0)
[    16.124] (**) |   |-->Monitor "IntegratedMonitor"
[    16.124] (**) |   |-->Device "Card0"
[    16.125] (**) |-->Screen "DisplayLinkScreen0" (1)
[    16.125] (**) |   |-->Monitor "DisplayLinkMonitor0"
[    16.125] (**) |   |-->Device "DisplayLinkDevice0"
[    16.125] (**) Option "AIGLX" "Off"
[    16.125] (==) Automatically adding devices
[    16.125] (==) Automatically enabling devices
[    16.125] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.125]    Entry deleted from font path.
[    16.126] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.126]    Entry deleted from font path.
[    16.126] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.126]    Entry deleted from font path.
[    16.126] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.126]    Entry deleted from font path.
[    16.126] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.126]    Entry deleted from font path.
[    16.126] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    16.126]    Entry deleted from font path.
[    16.126] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    16.126] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.126] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.126] (II) Loader magic: 0x3705a0
[    16.126] (II) Module ABI versions:
[    16.126]    X.Org ANSI C Emulation: 0.4
[    16.126]    X.Org Video Driver: 11.0
[    16.126]    X.Org XInput driver : 16.0
[    16.126]    X.Org Server Extension : 6.0
[    16.127] (--) PCI:*(0:0:2:0) 8086:0be2:8086:2012 rev 11, Mem @ 0xd0500000/1048576, I/O @ 0x000030d0/8
[    16.127] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.127] (II) LoadModule: "extmod"
[    16.129] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.129] (II) Module extmod: vendor="X.Org Foundation"
[    16.129]    compiled for 1.11.3, module version = 1.0.0
[    16.129]    Module class: X.Org Server Extension
[    16.129]    ABI class: X.Org Server Extension, version 6.0
[    16.129] (II) Loading extension MIT-SCREEN-SAVER
[    16.129] (II) Loading extension XFree86-VidModeExtension
[    16.129] (II) Loading extension XFree86-DGA
[    16.129] (II) Loading extension DPMS
[    16.129] (II) Loading extension XVideo
[    16.129] (II) Loading extension XVideo-MotionCompensation
[    16.129] (II) Loading extension X-Resource
[    16.129] (II) LoadModule: "dbe"
[    16.130] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.130] (II) Module dbe: vendor="X.Org Foundation"
[    16.130]    compiled for 1.11.3, module version = 1.0.0
[    16.130]    Module class: X.Org Server Extension
[    16.130]    ABI class: X.Org Server Extension, version 6.0
[    16.130] (II) Loading extension DOUBLE-BUFFER
[    16.130] (II) LoadModule: "glx"
[    16.131] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.131] (II) Module glx: vendor="X.Org Foundation"
[    16.131]    compiled for 1.11.3, module version = 1.0.0
[    16.131]    ABI class: X.Org Server Extension, version 6.0
[    16.131] (**) AIGLX disabled
[    16.131] (II) Loading extension GLX
[    16.131] (II) LoadModule: "record"
[    16.131] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.131] (II) Module record: vendor="X.Org Foundation"
[    16.131]    compiled for 1.11.3, module version = 1.13.0
[    16.131]    Module class: X.Org Server Extension
[    16.131]    ABI class: X.Org Server Extension, version 6.0
[    16.131] (II) Loading extension RECORD
[    16.131] (II) LoadModule: "dri"
[    16.132] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.132] (II) Module dri: vendor="X.Org Foundation"
[    16.132]    compiled for 1.11.3, module version = 1.0.0
[    16.132]    ABI class: X.Org Server Extension, version 6.0
[    16.132] (II) Loading extension XFree86-DRI
[    16.132] (II) LoadModule: "dri2"
[    16.133] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.133] (II) Module dri2: vendor="X.Org Foundation"
[    16.133]    compiled for 1.11.3, module version = 1.2.0
[    16.133]    ABI class: X.Org Server Extension, version 6.0
[    16.133] (II) Loading extension DRI2
[    16.133] (II) LoadModule: "pvr"
[    16.135] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    16.136] (II) Module PVR: vendor="X.Org Foundation"
[    16.136]    compiled for 1.11.3, module version = 1.7.10922
[    16.136]    Module class: X.Org Video Driver
[    16.136]    ABI class: X.Org Video Driver, version 11.0
[    16.136] (II) LoadModule: "displaylink"
[    16.137] (II) Loading /usr/lib/xorg/modules/drivers/displaylink_drv.so
[    16.138] (II) Module displaylink: vendor="X.Org Foundation"
[    16.138]    compiled for 1.11.3, module version = 0.0.1
[    16.138]    ABI class: X.Org Video Driver, version 11.0
[    16.138] (II) pvr: Driver for PowerVR chipsets: PowerVR SGX
[    16.138] (II) DL: driver for : displaylink
[    16.138] (++) using VT number 8

[    16.153] drmOpenDevice: node name is /dev/dri/card0
[    16.153] drmOpenDevice: open result is 9, (OK)
[    16.153] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.153] drmOpenDevice: node name is /dev/dri/card0
[    16.153] drmOpenDevice: open result is 9, (OK)
[    16.153] drmOpenByBusid: drmOpenMinor returns 9
[    16.153] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.154] drmOpenDevice: node name is /dev/dri/card0
[    16.154] drmOpenDevice: open result is 9, (OK)
[    16.154] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.154] drmOpenDevice: node name is /dev/dri/card0
[    16.154] drmOpenDevice: open result is 9, (OK)
[    16.154] drmOpenByBusid: drmOpenMinor returns 9
[    16.154] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.156] drmOpenDevice: node name is /dev/dri/card0
[    16.156] drmOpenDevice: open result is 9, (OK)
[    16.156] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.156] drmOpenDevice: node name is /dev/dri/card0
[    16.156] drmOpenDevice: open result is 9, (OK)
[    16.156] drmOpenByBusid: drmOpenMinor returns 9
[    16.156] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.156] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    16.156] (WW) Falling back to old probe method for displaylink
[    16.156] (II) Loading sub module "fbdevhw"
[    16.156] (II) LoadModule: "fbdevhw"
[    16.157] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.157] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.157]    compiled for 1.11.3, module version = 0.0.2
[    16.157]    ABI class: X.Org Video Driver, version 11.0
[    16.158] drmOpenDevice: node name is /dev/dri/card0
[    16.158] drmOpenDevice: open result is 10, (OK)
[    16.158] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.158] drmOpenDevice: node name is /dev/dri/card0
[    16.158] drmOpenDevice: open result is 10, (OK)
[    16.158] drmOpenByBusid: drmOpenMinor returns 10
[    16.158] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.158] drmOpenDevice: node name is /dev/dri/card0
[    16.158] drmOpenDevice: open result is 11, (OK)
[    16.158] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.158] drmOpenDevice: node name is /dev/dri/card0
[    16.158] drmOpenDevice: open result is 11, (OK)
[    16.158] drmOpenByBusid: drmOpenMinor returns 11
[    16.158] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    16.158] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.161] drmOpenDevice: node name is /dev/dri/card0
[    16.161] drmOpenDevice: open result is 12, (OK)
[    16.161] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.161] drmOpenDevice: node name is /dev/dri/card0
[    16.161] drmOpenDevice: open result is 12, (OK)
[    16.161] drmOpenByBusid: drmOpenMinor returns 12
[    16.161] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    16.161] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.161] drmOpenDevice: node name is /dev/dri/card0
[    16.161] drmOpenDevice: open result is 12, (OK)
[    16.161] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.161] drmOpenDevice: node name is /dev/dri/card0
[    16.162] drmOpenDevice: open result is 12, (OK)
[    16.162] drmOpenByBusid: drmOpenMinor returns 12
[    16.162] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    16.162] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.504] drmOpenDevice: node name is /dev/dri/card0
[    16.504] drmOpenDevice: open result is 12, (OK)
[    16.504] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    16.504] drmOpenDevice: node name is /dev/dri/card0
[    16.504] drmOpenDevice: open result is 12, (OK)
[    16.504] drmOpenByBusid: drmOpenMinor returns 12
[    16.504] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    16.504] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    16.853] (II) pvr(0): source head @cdv-v1.0.2
[    16.853] (II) pvr(0): Creating default Display subsection in Screen section
        "Screen0" for depth/fbbpp 16/16
[    16.853] (**) pvr(0): Depth 16, (--) framebuffer bpp 16
[    16.853] (==) pvr(0): RGB weight 565
[    16.853] (==) pvr(0): Default visual is TrueColor
[    16.853] (**) pvr(0): Option "FlipChain" "On"
[    16.853] (**) pvr(0): Option "SoftEXA" "Off"
[    16.853] (**) pvr(0): Option "DRIDisableVSync" "False"
[    16.853] (II) pvr(0): Flipchain enabled
[    16.892] (II) pvr(0): Output VGA1 using monitor section IntegratedMonitor
[    17.304] (II) pvr(0): Output DVI1 has no monitor section
[    17.305] (II) pvr(0): Output DP1 has no monitor section
[    17.350] (II) pvr(0): Output DVI2 has no monitor section
[    17.355] (II) pvr(0): Output eDP1 has no monitor section
[    17.355] (II) pvr(0): found backlight control interface /sys/class/backlight/acpi_video0
[    17.392] (II) pvr(0): EDID for output VGA1
[    17.804] (II) pvr(0): EDID for output DVI1
[    17.804] (II) pvr(0): Manufacturer: ELO  Model: 1002  Serial#: 508
[    17.804] (II) pvr(0): Year: 2015  Week: 38
[    17.804] (II) pvr(0): EDID Version: 1.3
[    17.804] (II) pvr(0): Digital Display Input
[    17.804] (II) pvr(0): Max Image Size [cm]: horiz.: 22  vert.: 14
[    17.804] (II) pvr(0): Gamma: 2.20
[    17.804] (II) pvr(0): DPMS capabilities: Off
[    17.804] (II) pvr(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    17.804] (II) pvr(0): First detailed timing is preferred mode
[    17.804] (II) pvr(0): redX: 0.592 redY: 0.340   greenX: 0.310 greenY: 0.579
[    17.804] (II) pvr(0): blueX: 0.150 blueY: 0.128   whiteX: 0.308 whiteY: 0.324
[    17.804] (II) pvr(0): Supported established timings:
[    17.804] (II) pvr(0): 640x480@60Hz
[    17.804] (II) pvr(0): 800x600@60Hz
[    17.804] (II) pvr(0): 1024x768@60Hz
[    17.804] (II) pvr(0): Manufacturer's mask: 0
[    17.804] (II) pvr(0): Supported detailed timing:
[    17.804] (II) pvr(0): clock: 83.5 MHz   Image Size:  217 x 136 mm
[    17.804] (II) pvr(0): h_active: 1280  h_sync: 1352  h_sync_end 1480 h_blank_end 1680 h_border: 0
[    17.804] (II) pvr(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 831 v_border: 0
[    17.804] (II) pvr(0): Serial No: I15H000508
[    17.804] (II) pvr(0): Monitor name: ELO ET1002L
[    17.804] (II) pvr(0): Ranges: V min: 60 V max: 60 Hz, H min: 31 H max: 60 kHz, PixClock max 85 MHz
[    17.804] (II) pvr(0): Supported detailed timing:
[    17.805] (II) pvr(0): clock: 27.0 MHz   Image Size:  217 x 136 mm
[    17.805] (II) pvr(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    17.805] (II) pvr(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    17.805] (II) pvr(0): Supported detailed timing:
[    17.805] (II) pvr(0): clock: 74.2 MHz   Image Size:  217 x 136 mm
[    17.805] (II) pvr(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    17.805] (II) pvr(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    17.805] (II) pvr(0): Number of EDID sections to follow: 1
[    17.805] (II) pvr(0): EDID (in hex):
[    17.805] (II) pvr(0):       00ffffffffffff00158f0210fc010000
[    17.805] (II) pvr(0):       2619010380160e782a85bc97574f9426
[    17.805] (II) pvr(0):       204e5321080001010101010101010101
[    17.805] (II) pvr(0):       0101010101019e20009051201f304880
[    17.805] (II) pvr(0):       3600d9880000001c000000ff00493135
[    17.805] (II) pvr(0):       483030303530380a2020000000fc0045
[    17.805] (II) pvr(0):       4c4f204554313030324c0a20000000fd
[    17.805] (II) pvr(0):       003c3c1f3c08000a2020202020200131
[    17.805] (II) pvr(0): Printing probed modes for output DVI1
[    17.805] (II) pvr(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    17.805] (II) pvr(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.805] (II) pvr(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.805] (II) pvr(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.806] (II) pvr(0): EDID for output DP1
[    17.850] (II) pvr(0): EDID for output DVI2
[    17.856] (II) pvr(0): EDID for output eDP1
[    17.856] (II) pvr(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "640x480" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "896x672" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "928x696" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "960x720" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "720x450" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "800x512" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "960x540" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "960x600" (doublescan mode not supported)
[    17.856] (II) pvr(0): Not using default mode "1024x768" (doublescan mode not supported)
[    17.856] (II) pvr(0): Printing probed modes for output eDP1
[    17.857] (II) pvr(0): Modeline "1920x1080"x60.2  144.00  1920 2016 2080 2176  1080 1088 1092 1100 (66.2 kHz)
[    17.857] (II) pvr(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
[    17.857] (II) pvr(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    17.857] (II) pvr(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    17.857] (II) pvr(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
[    17.857] (II) pvr(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[    17.857] (II) pvr(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.857] (II) pvr(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    17.857] (II) pvr(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    17.857] (II) pvr(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.857] (II) pvr(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    17.857] (II) pvr(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    17.857] (II) pvr(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.857] (II) pvr(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.857] (II) pvr(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.857] (II) pvr(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.857] (II) pvr(0): Output VGA1 disconnected
[    17.857] (II) pvr(0): Output DVI1 connected
[    17.857] (II) pvr(0): Output DP1 disconnected
[    17.857] (II) pvr(0): Output DVI2 disconnected
[    17.857] (II) pvr(0): Output eDP1 connected
[    17.857] (II) pvr(0): Using fuzzy aspect match for initial modes
[    17.857] (II) pvr(0): Output DVI1 using initial mode 1024x768
[    17.857] (II) pvr(0): Output eDP1 using initial mode 1024x768
[    17.857] (II) pvr(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.857] (--) pvr(0): Virtual size is 1920x1080 (pitch 3840)
[    17.857] (**) pvr(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    17.857] (II) pvr(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.857] (**) pvr(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    17.857] (II) pvr(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.857] (**) pvr(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    17.857] (II) pvr(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.857] (**) pvr(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
[    17.857] (II) pvr(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    17.857] (==) pvr(0): DPI set to (96, 96)
[    17.857] (II) Loading sub module "fb"
[    17.857] (II) LoadModule: "fb"
[    17.858] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.858] (II) Module fb: vendor="X.Org Foundation"
[    17.858]    compiled for 1.11.3, module version = 1.0.0
[    17.858]    ABI class: X.Org ANSI C Emulation, version 0.4
[    17.858] (II) pvr(0): [pvr] Software copy threshold : 0B
[    17.858] (II) pvr(0): [pvr] Software solid threshold : 0B
[    17.858] (II) pvr(0): [pvr] Software composite threshold : 0B
[    17.858] (II) pvr(0): [pvr] Pixmap pool size: 0B
[    17.858] (II) Loading sub module "exa"
[    17.858] (II) LoadModule: "exa"
[    17.859] (II) Loading /usr/lib/xorg/modules/libexa.so
[    17.859] (II) Module exa: vendor="X.Org Foundation"
[    17.859]    compiled for 1.11.3, module version = 2.5.0
[    17.859]    ABI class: X.Org Video Driver, version 11.0
[    17.859] PVRPreInit: done
[    17.859] (II) UnloadModule: "displaylink"
[    17.859] (II) Unloading displaylink
[    17.859] (II) UnloadModule: "fbdevhw"
[    17.859] (II) Unloading fbdevhw
[    17.859] (II) pvr(0): [DRI2] Setup complete
[    17.859] (II) pvr(0): [DRI2]   DRI driver: pvr
[    17.860] (II) EXA(0): Driver allocated offscreen pixmaps
[    17.860] (II) EXA(0): Driver registered support for the following operations:
[    17.860] (II)         Solid
[    17.860] (II)         Copy
[    17.860] (II)         Composite (RENDER acceleration)
[    17.874] (==) pvr(0): Backing store disabled
[    17.874] (==) pvr(0): Silken mouse enabled
[    17.874] (==) pvr(0): DPMS enabled
[    17.874] (II) pvr(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.874] (II) pvr(0): max backlight 15
[    17.874] (II) pvr(0): active backlight 15
[    17.875] (==) pvr(0): Direct rendering enabled
[    17.875] (II) pvr(0): Enable XVideo
[    20.671] (II) pvr(0): hotplug detection enabled
[    20.671] (--) RandR disabled
[    20.671] (II) Initializing built-in extension Generic Event Extension
[    20.671] (II) Initializing built-in extension SHAPE
[    20.671] (II) Initializing built-in extension MIT-SHM
[    20.671] (II) Initializing built-in extension XInputExtension
[    20.671] (II) Initializing built-in extension XTEST
[    20.671] (II) Initializing built-in extension BIG-REQUESTS
[    20.671] (II) Initializing built-in extension SYNC
[    20.671] (II) Initializing built-in extension XKEYBOARD
[    20.671] (II) Initializing built-in extension XC-MISC
[    20.671] (II) Initializing built-in extension SECURITY
[    20.671] (II) Initializing built-in extension XINERAMA
[    20.671] (II) Initializing built-in extension XFIXES
[    20.671] (II) Initializing built-in extension RENDER
[    20.671] (II) Initializing built-in extension RANDR
[    20.671] (II) Initializing built-in extension COMPOSITE
[    20.671] (II) Initializing built-in extension DAMAGE
[    20.727] (II) AIGLX: Loaded and initialized swrast
[    20.727] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    20.728] (II) pvr(0): Setting screen physical size to 270 x 203
[    23.316] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.323] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.323] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.323] (II) LoadModule: "evdev"
[    23.324] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.325] (II) Module evdev: vendor="X.Org Foundation"
[    23.325]    compiled for 1.11.3, module version = 2.7.0
[    23.325]    Module class: X.Org XInput Driver
[    23.325]    ABI class: X.Org XInput driver, version 16.0
[    23.325] (II) Using input driver 'evdev' for 'Power Button'
[    23.325] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.325] (**) Power Button: always reports core events
[    23.325] (**) evdev: Power Button: Device: "/dev/input/event2"
[    23.325] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.325] (--) evdev: Power Button: Found keys
[    23.325] (II) evdev: Power Button: Configuring as keyboard
[    23.325] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    23.325] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.325] (**) Option "xkb_rules" "evdev"
[    23.325] (**) Option "xkb_model" "pc105"
[    23.325] (**) Option "xkb_layout" "cz"
[    23.331] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    23.333] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    23.333] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.333] (II) Using input driver 'evdev' for 'Video Bus'
[    23.333] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.333] (**) Video Bus: always reports core events
[    23.333] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    23.333] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.333] (--) evdev: Video Bus: Found keys
[    23.333] (II) evdev: Video Bus: Configuring as keyboard
[    23.333] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3/event3"
[    23.333] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.333] (**) Option "xkb_rules" "evdev"
[    23.333] (**) Option "xkb_model" "pc105"
[    23.333] (**) Option "xkb_layout" "cz"
[    23.335] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.335] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.335] (II) Using input driver 'evdev' for 'Power Button'
[    23.335] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.335] (**) Power Button: always reports core events
[    23.335] (**) evdev: Power Button: Device: "/dev/input/event0"
[    23.335] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.335] (--) evdev: Power Button: Found keys
[    23.335] (II) evdev: Power Button: Configuring as keyboard
[    23.335] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    23.335] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    23.335] (**) Option "xkb_rules" "evdev"
[    23.335] (**) Option "xkb_model" "pc105"
[    23.335] (**) Option "xkb_layout" "cz"
[    23.337] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    23.337] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    23.337] (II) Using input driver 'evdev' for 'Sleep Button'
[    23.337] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.337] (**) Sleep Button: always reports core events
[    23.337] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    23.337] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    23.337] (--) evdev: Sleep Button: Found keys
[    23.337] (II) evdev: Sleep Button: Configuring as keyboard
[    23.337] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    23.337] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    23.337] (**) Option "xkb_rules" "evdev"
[    23.337] (**) Option "xkb_model" "pc105"
[    23.337] (**) Option "xkb_layout" "cz"
[    23.339] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event10)
[    23.339] (II) No input driver specified, ignoring this device.
[    23.339] (II) This device may have been added with another device file.
[    23.339] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event8)
[    23.339] (II) No input driver specified, ignoring this device.
[    23.339] (II) This device may have been added with another device file.
[    23.340] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event9)
[    23.340] (II) No input driver specified, ignoring this device.
[    23.340] (II) This device may have been added with another device file.
[    23.341] (II) config/udev: Adding input device EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface (/dev/input/event4)
[    23.341] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Applying InputClass "evdev pointer catchall"
[    23.341] (II) Using input driver 'evdev' for 'EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface'
[    23.341] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.341] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: always reports core events
[    23.341] (**) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Device: "/dev/input/event4"
[    23.341] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Vendor 0x4e7 Product 0x50
[    23.341] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found 1 mouse buttons
[    23.341] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found absolute axes
[    23.341] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found x and y absolute axes
[    23.341] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found absolute touchscreen
[    23.341] (II) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Configuring as touchscreen
[    23.341] (**) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: YAxisMapping: buttons 4 and 5
[    23.341] (**) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.342] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.3/1-6.3:1.0/input/input4/event4"
[    23.342] (II) XINPUT: Adding extended input device "EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface" (type: TOUCHSCREEN, id 10)
[    23.342] (II) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: initialized for absolute axes.
[    23.342] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) keeping acceleration scheme 1
[    23.342] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) acceleration profile 0
[    23.342] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) acceleration factor: 2.000
[    23.342] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) acceleration threshold: 4
[    23.343] (II) config/udev: Adding input device EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface (/dev/input/js0)
[    23.343] (II) No input driver specified, ignoring this device.
[    23.343] (II) This device may have been added with another device file.
[    23.343] (II) config/udev: Adding input device EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface (/dev/input/mouse0)
[    23.344] (II) No input driver specified, ignoring this device.
[    23.344] (II) This device may have been added with another device file.
[    23.344] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/event5)
[    23.344] (**) Genius       Optical Mouse: Applying InputClass "evdev pointer catchall"
[    23.345] (II) Using input driver 'evdev' for 'Genius       Optical Mouse'
[    23.345] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.345] (**) Genius       Optical Mouse: always reports core events
[    23.345] (**) evdev: Genius       Optical Mouse: Device: "/dev/input/event5"
[    23.345] (--) evdev: Genius       Optical Mouse: Vendor 0x458 Product 0x3a
[    23.345] (--) evdev: Genius       Optical Mouse: Found 3 mouse buttons
[    23.345] (--) evdev: Genius       Optical Mouse: Found scroll wheel(s)
[    23.345] (--) evdev: Genius       Optical Mouse: Found relative axes
[    23.345] (--) evdev: Genius       Optical Mouse: Found x and y relative axes
[    23.345] (II) evdev: Genius       Optical Mouse: Configuring as mouse
[    23.345] (II) evdev: Genius       Optical Mouse: Adding scrollwheel support
[    23.345] (**) evdev: Genius       Optical Mouse: YAxisMapping: buttons 4 and 5
[    23.345] (**) evdev: Genius       Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.345] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.2/1-8.2.1/1-8.2.1:1.0/input/input5/event5"
[    23.345] (II) XINPUT: Adding extended input device "Genius       Optical Mouse" (type: MOUSE, id 11)
[    23.345] (II) evdev: Genius       Optical Mouse: initialized for relative axes.
[    23.346] (**) Genius       Optical Mouse: (accel) keeping acceleration scheme 1
[    23.346] (**) Genius       Optical Mouse: (accel) acceleration profile 0
[    23.346] (**) Genius       Optical Mouse: (accel) acceleration factor: 2.000
[    23.346] (**) Genius       Optical Mouse: (accel) acceleration threshold: 4
[    23.346] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/mouse1)
[    23.346] (II) No input driver specified, ignoring this device.
[    23.346] (II) This device may have been added with another device file.
[    23.347] (II) config/udev: Adding input device CHICONY Compaq USB Keyboard (/dev/input/event6)
[    23.347] (**) CHICONY Compaq USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.347] (II) Using input driver 'evdev' for 'CHICONY Compaq USB Keyboard'
[    23.347] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.347] (**) CHICONY Compaq USB Keyboard: always reports core events
[    23.348] (**) evdev: CHICONY Compaq USB Keyboard: Device: "/dev/input/event6"
[    23.348] (--) evdev: CHICONY Compaq USB Keyboard: Vendor 0x49f Product 0x51
[    23.348] (--) evdev: CHICONY Compaq USB Keyboard: Found keys
[    23.348] (II) evdev: CHICONY Compaq USB Keyboard: Configuring as keyboard
[    23.348] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.2/1-8.2.3/1-8.2.3.2/1-8.2.3.2:1.0/input/input6/event6"
[    23.348] (II) XINPUT: Adding extended input device "CHICONY Compaq USB Keyboard" (type: KEYBOARD, id 12)
[    23.348] (**) Option "xkb_rules" "evdev"
[    23.348] (**) Option "xkb_model" "pc105"
[    23.348] (**) Option "xkb_layout" "cz"
[    23.349] (II) config/udev: Adding input device CHICONY Compaq USB Keyboard (/dev/input/event7)
[    23.349] (**) CHICONY Compaq USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.350] (II) Using input driver 'evdev' for 'CHICONY Compaq USB Keyboard'
[    23.350] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.350] (**) CHICONY Compaq USB Keyboard: always reports core events
[    23.350] (**) evdev: CHICONY Compaq USB Keyboard: Device: "/dev/input/event7"
[    23.350] (--) evdev: CHICONY Compaq USB Keyboard: Vendor 0x49f Product 0x51
[    23.350] (--) evdev: CHICONY Compaq USB Keyboard: Found keys
[    23.350] (II) evdev: CHICONY Compaq USB Keyboard: Configuring as keyboard
[    23.350] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.2/1-8.2.3/1-8.2.3.2/1-8.2.3.2:1.1/input/input7/event7"
[    23.350] (II) XINPUT: Adding extended input device "CHICONY Compaq USB Keyboard" (type: KEYBOARD, id 13)
[    23.350] (**) Option "xkb_rules" "evdev"
[    23.350] (**) Option "xkb_model" "pc105"
[    23.350] (**) Option "xkb_layout" "cz"
[    24.724] (II) XKB: reuse xkmfile /var/lib/xkb/server-6312AA7F541A1077FD766490800F036AD4583782.xkm
[    24.732] (II) XKB: reuse xkmfile /var/lib/xkb/server-6312AA7F541A1077FD766490800F036AD4583782.xkm

Xorg.0.log (DisplayLink screen first):

[    13.229]
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    13.229] X Protocol Version 11, Revision 0
[    13.229] Build Operating System: Linux 2.6.42-76-generic i686 Ubuntu
[    13.229] Current Operating System: Linux terminal2 3.2.0-97-generic #137-Ubuntu SMP Thu Dec 17 21:14:00 UTC 2015 i686
[    13.229] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-97-generic root=/dev/mapper/vg_00-lv_root ro nomodeset
[    13.229] Build Date: 12 February 2015  02:51:26PM
[    13.229] xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[    13.229] Current version of pixman: 0.30.2
[    13.229]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[    13.229] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.229] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 22 15:39:44 2016
[    13.230] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.231] (**) Option "defaultserverlayout" "default screen"
[    13.231] (**) ServerLayout "default screen"
[    13.231] (**) |-->Screen "DisplayLinkScreen0" (0)
[    13.231] (**) |   |-->Monitor "DisplayLinkMonitor0"
[    13.232] (**) |   |-->Device "DisplayLinkDevice0"
[    13.232] (**) |-->Screen "Screen0" (1)
[    13.232] (**) |   |-->Monitor "IntegratedMonitor"
[    13.232] (**) |   |-->Device "Card0"
[    13.232] (**) Option "AIGLX" "Off"
[    13.233] (==) Automatically adding devices
[    13.233] (==) Automatically enabling devices
[    13.233] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.233]    Entry deleted from font path.
[    13.233] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.233]    Entry deleted from font path.
[    13.233] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.233]    Entry deleted from font path.
[    13.233] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.233]    Entry deleted from font path.
[    13.233] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.233]    Entry deleted from font path.
[    13.233] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    13.233]    Entry deleted from font path.
[    13.233] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    13.233] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.233] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.233] (II) Loader magic: 0x3b05a0
[    13.233] (II) Module ABI versions:
[    13.233]    X.Org ANSI C Emulation: 0.4
[    13.233]    X.Org Video Driver: 11.0
[    13.233]    X.Org XInput driver : 16.0
[    13.233]    X.Org Server Extension : 6.0
[    13.235] (--) PCI:*(0:0:2:0) 8086:0be2:8086:2012 rev 11, Mem @ 0xd0500000/1048576, I/O @ 0x000030d0/8
[    13.235] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.235] (II) LoadModule: "extmod"
[    13.236] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.237] (II) Module extmod: vendor="X.Org Foundation"
[    13.237]    compiled for 1.11.3, module version = 1.0.0
[    13.237]    Module class: X.Org Server Extension
[    13.237]    ABI class: X.Org Server Extension, version 6.0
[    13.237] (II) Loading extension MIT-SCREEN-SAVER
[    13.237] (II) Loading extension XFree86-VidModeExtension
[    13.237] (II) Loading extension XFree86-DGA
[    13.237] (II) Loading extension DPMS
[    13.237] (II) Loading extension XVideo
[    13.237] (II) Loading extension XVideo-MotionCompensation
[    13.237] (II) Loading extension X-Resource
[    13.237] (II) LoadModule: "dbe"
[    13.237] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.237] (II) Module dbe: vendor="X.Org Foundation"
[    13.237]    compiled for 1.11.3, module version = 1.0.0
[    13.238]    Module class: X.Org Server Extension
[    13.238]    ABI class: X.Org Server Extension, version 6.0
[    13.238] (II) Loading extension DOUBLE-BUFFER
[    13.238] (II) LoadModule: "glx"
[    13.238] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.238] (II) Module glx: vendor="X.Org Foundation"
[    13.238]    compiled for 1.11.3, module version = 1.0.0
[    13.238]    ABI class: X.Org Server Extension, version 6.0
[    13.238] (**) AIGLX disabled
[    13.238] (II) Loading extension GLX
[    13.239] (II) LoadModule: "record"
[    13.239] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.239] (II) Module record: vendor="X.Org Foundation"
[    13.239]    compiled for 1.11.3, module version = 1.13.0
[    13.239]    Module class: X.Org Server Extension
[    13.239]    ABI class: X.Org Server Extension, version 6.0
[    13.239] (II) Loading extension RECORD
[    13.239] (II) LoadModule: "dri"
[    13.239] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.240] (II) Module dri: vendor="X.Org Foundation"
[    13.240]    compiled for 1.11.3, module version = 1.0.0
[    13.240]    ABI class: X.Org Server Extension, version 6.0
[    13.240] (II) Loading extension XFree86-DRI
[    13.240] (II) LoadModule: "dri2"
[    13.240] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.241] (II) Module dri2: vendor="X.Org Foundation"
[    13.241]    compiled for 1.11.3, module version = 1.2.0
[    13.241]    ABI class: X.Org Server Extension, version 6.0
[    13.241] (II) Loading extension DRI2
[    13.241] (II) LoadModule: "displaylink"
[    13.243] (II) Loading /usr/lib/xorg/modules/drivers/displaylink_drv.so
[    13.243] (II) Module displaylink: vendor="X.Org Foundation"
[    13.243]    compiled for 1.11.3, module version = 0.0.1
[    13.244]    ABI class: X.Org Video Driver, version 11.0
[    13.244] (II) LoadModule: "pvr"
[    13.245] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    13.246] (II) Module PVR: vendor="X.Org Foundation"
[    13.246]    compiled for 1.11.3, module version = 1.7.10922
[    13.246]    Module class: X.Org Video Driver
[    13.246]    ABI class: X.Org Video Driver, version 11.0
[    13.246] (II) DL: driver for : displaylink
[    13.246] (II) pvr: Driver for PowerVR chipsets: PowerVR SGX
[    13.246] (++) using VT number 8

[    13.257] (WW) Falling back to old probe method for displaylink
[    13.258] (II) Loading sub module "fbdevhw"
[    13.258] (II) LoadModule: "fbdevhw"
[    13.258] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.259] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.259]    compiled for 1.11.3, module version = 0.0.2
[    13.259]    ABI class: X.Org Video Driver, version 11.0
[    13.259] (II) Loading /usr/lib/xorg/modules/drivers/displaylink_drv.so
[    13.259] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.259] (II) DL(0): using /dev/fb0
[    13.259] drmOpenDevice: node name is /dev/dri/card0
[    13.260] drmOpenDevice: open result is 9, (OK)
[    13.260] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.260] drmOpenDevice: node name is /dev/dri/card0
[    13.260] drmOpenDevice: open result is 9, (OK)
[    13.260] drmOpenByBusid: drmOpenMinor returns 9
[    13.260] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.261] drmOpenDevice: node name is /dev/dri/card0
[    13.261] drmOpenDevice: open result is 9, (OK)
[    13.261] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.261] drmOpenDevice: node name is /dev/dri/card0
[    13.261] drmOpenDevice: open result is 9, (OK)
[    13.261] drmOpenByBusid: drmOpenMinor returns 9
[    13.261] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.263] drmOpenDevice: node name is /dev/dri/card0
[    13.263] drmOpenDevice: open result is 9, (OK)
[    13.263] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.263] drmOpenDevice: node name is /dev/dri/card0
[    13.263] drmOpenDevice: open result is 9, (OK)
[    13.263] drmOpenByBusid: drmOpenMinor returns 9
[    13.263] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.263] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    13.263] (II) DL(0): Manufacturer: VJK  Model: 5308  Serial#: 469996561
[    13.263] (II) DL(0): Year: 2011  Week: 52
[    13.263] (II) DL(0): EDID Version: 1.3
[    13.263] (II) DL(0): Digital Display Input
[    13.263] (II) DL(0): DFP 1.x compatible TMDS
[    13.263] (II) DL(0): Max Image Size [cm]: horiz.: 15  vert.: 8
[    13.263] (II) DL(0): Gamma: 2.20
[    13.263] (II) DL(0): DPMS capabilities: StandBy Suspend
[    13.263] (II) DL(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    13.263] (II) DL(0): First detailed timing is preferred mode
[    13.263] (II) DL(0): redX: 0.560 redY: 0.329   greenX: 0.349 greenY: 0.590
[    13.263] (II) DL(0): blueX: 0.149 blueY: 0.794   whiteX: 0.329 whiteY: 0.328
[    13.263] (II) DL(0): Manufacturer's mask: 0
[    13.264] (II) DL(0): Supported detailed timing:
[    13.264] (II) DL(0): clock: 29.3 MHz   Image Size:  154 x 84 mm
[    13.264] (II) DL(0): h_active: 800  h_sync: 840  h_sync_end 888 h_blank_end 928 h_border: 0
[    13.264] (II) DL(0): v_active: 480  v_sync: 493  v_sync_end 496 v_blanking: 525 v_border: 0
[    13.264] (II) DL(0): Ranges: V min: 55 V max: 65 Hz, H min: 24 H max: 41 kHz, PixClock max 55 MHz
[    13.264] (II) DL(0): Monitor name: HSD070IDW1
[    13.264] (II) DL(0): EDID (in hex):
[    13.264] (II) DL(0):        00ffffffffffff00594b08531194031c
[    13.264] (II) DL(0):        34150103810f0878ca54548f54599726
[    13.264] (II) DL(0):        cb545400000001010101010101010101
[    13.264] (II) DL(0):        010101010101720b208030e02d102830
[    13.264] (II) DL(0):        d3009a5400000018000000fd00374118
[    13.264] (II) DL(0):        2905000a202020202020000000fc0048
[    13.264] (II) DL(0):        5344303730494457310a0a0a00000010
[    13.264] (II) DL(0):        00000000000000000000000000000023
[    13.264] (**) DL(0): Depth 16, (--) framebuffer bpp 16
[    13.264] (==) DL(0): RGB weight 565
[    13.264] (==) DL(0): Default visual is TrueColor
[    13.264] (==) DL(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.264] (II) DL(0): hardware: udlfb (video memory: 752kB)
[    13.264] (**) DL(0): Option "fbdev" "/dev/fb0"
[    13.264] (II) Loading sub module "fb"
[    13.264] (II) LoadModule: "fb"
[    13.265] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.265] (II) Module fb: vendor="X.Org Foundation"
[    13.265]    compiled for 1.11.3, module version = 1.0.0
[    13.265]    ABI class: X.Org ANSI C Emulation, version 0.4
[    13.265] (II) DL(0): Output udlfb using monitor section DisplayLinkMonitor0
[    13.265] (II) DL(0): EDID for output udlfb
[    13.265] (II) DL(0): Manufacturer: VJK  Model: 5308  Serial#: 469996561
[    13.265] (II) DL(0): Year: 2011  Week: 52
[    13.265] (II) DL(0): EDID Version: 1.3
[    13.265] (II) DL(0): Digital Display Input
[    13.265] (II) DL(0): DFP 1.x compatible TMDS
[    13.265] (II) DL(0): Max Image Size [cm]: horiz.: 15  vert.: 8
[    13.265] (II) DL(0): Gamma: 2.20
[    13.265] (II) DL(0): DPMS capabilities: StandBy Suspend
[    13.265] (II) DL(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    13.265] (II) DL(0): First detailed timing is preferred mode
[    13.265] (II) DL(0): redX: 0.560 redY: 0.329   greenX: 0.349 greenY: 0.590
[    13.265] (II) DL(0): blueX: 0.149 blueY: 0.794   whiteX: 0.329 whiteY: 0.328
[    13.265] (II) DL(0): Manufacturer's mask: 0
[    13.265] (II) DL(0): Supported detailed timing:
[    13.265] (II) DL(0): clock: 29.3 MHz   Image Size:  154 x 84 mm
[    13.265] (II) DL(0): h_active: 800  h_sync: 840  h_sync_end 888 h_blank_end 928 h_border: 0
[    13.265] (II) DL(0): v_active: 480  v_sync: 493  v_sync_end 496 v_blanking: 525 v_border: 0
[    13.265] (II) DL(0): Ranges: V min: 55 V max: 65 Hz, H min: 24 H max: 41 kHz, PixClock max 55 MHz
[    13.266] (II) DL(0): Monitor name: HSD070IDW1
[    13.266] (II) DL(0): EDID (in hex):
[    13.266] (II) DL(0):        00ffffffffffff00594b08531194031c
[    13.266] (II) DL(0):        34150103810f0878ca54548f54599726
[    13.266] (II) DL(0):        cb545400000001010101010101010101
[    13.266] (II) DL(0):        010101010101720b208030e02d102830
[    13.266] (II) DL(0):        d3009a5400000018000000fd00374118
[    13.266] (II) DL(0):        2905000a202020202020000000fc0048
[    13.266] (II) DL(0):        5344303730494457310a0a0a00000010
[    13.266] (II) DL(0):        00000000000000000000000000000023
[    13.266] (II) DL(0): EDID vendor "VJK", prod id 21256
[    13.266] (II) DL(0): Using EDID range info for horizontal sync
[    13.266] (II) DL(0): Using EDID range info for vertical refresh
[    13.266] (II) DL(0): Printing DDC gathered Modelines:
[    13.266] (II) DL(0): Modeline "800x480"x0.0   29.30  800 840 888 928  480 493 496 525 -hsync -vsync (31.6 kHz)
[    13.266] (II) DL(0): EDID vendor "VJK", prod id 21256
[    13.266] (II) DL(0): EDID for output udlfb
[    13.266] (II) DL(0): Manufacturer: VJK  Model: 5308  Serial#: 469996561
[    13.266] (II) DL(0): Year: 2011  Week: 52
[    13.266] (II) DL(0): EDID Version: 1.3
[    13.266] (II) DL(0): Digital Display Input
[    13.266] (II) DL(0): DFP 1.x compatible TMDS
[    13.266] (II) DL(0): Max Image Size [cm]: horiz.: 15  vert.: 8
[    13.266] (II) DL(0): Gamma: 2.20
[    13.266] (II) DL(0): DPMS capabilities: StandBy Suspend
[    13.266] (II) DL(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    13.266] (II) DL(0): First detailed timing is preferred mode
[    13.266] (II) DL(0): redX: 0.560 redY: 0.329   greenX: 0.349 greenY: 0.590
[    13.266] (II) DL(0): blueX: 0.149 blueY: 0.794   whiteX: 0.329 whiteY: 0.328
[    13.266] (II) DL(0): Manufacturer's mask: 0
[    13.266] (II) DL(0): Supported detailed timing:
[    13.266] (II) DL(0): clock: 29.3 MHz   Image Size:  154 x 84 mm
[    13.266] (II) DL(0): h_active: 800  h_sync: 840  h_sync_end 888 h_blank_end 928 h_border: 0
[    13.266] (II) DL(0): v_active: 480  v_sync: 493  v_sync_end 496 v_blanking: 525 v_border: 0
[    13.266] (II) DL(0): Ranges: V min: 55 V max: 65 Hz, H min: 24 H max: 41 kHz, PixClock max 55 MHz
[    13.266] (II) DL(0): Monitor name: HSD070IDW1
[    13.267] (II) DL(0): EDID (in hex):
[    13.267] (II) DL(0):        00ffffffffffff00594b08531194031c
[    13.267] (II) DL(0):        34150103810f0878ca54548f54599726
[    13.267] (II) DL(0):        cb545400000001010101010101010101
[    13.267] (II) DL(0):        010101010101720b208030e02d102830
[    13.267] (II) DL(0):        d3009a5400000018000000fd00374118
[    13.267] (II) DL(0):        2905000a202020202020000000fc0048
[    13.267] (II) DL(0):        5344303730494457310a0a0a00000010
[    13.267] (II) DL(0):        00000000000000000000000000000023
[    13.267] (II) DL(0): EDID vendor "VJK", prod id 21256
[    13.267] (II) DL(0): Using hsync ranges from config file
[    13.267] (II) DL(0): Using vrefresh ranges from config file
[    13.267] (II) DL(0): Printing DDC gathered Modelines:
[    13.267] (II) DL(0): Modeline "800x480"x0.0   29.30  800 840 888 928  480 493 496 525 -hsync -vsync (31.6 kHz)
[    13.267] (II) DL(0): EDID vendor "VJK", prod id 21256
[    13.267] (II) DL(0): Printing probed modes for output udlfb
[    13.267] (II) DL(0): Modeline "800x480"x60.1   29.30  800 840 888 928  480 493 496 525 -hsync -vsync (31.6 kHz)
[    13.267] (II) DL(0): Output udlfb connected
[    13.267] (II) DL(0): Using user preference for initial modes
[    13.267] (II) DL(0): Output udlfb using initial mode 800x480
[    13.267] (II) DL(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.267] (--) DL(0): Virtual size is 800x480 (pitch 0)
[    13.267] (**) DL(0):  Driver mode "800x480": 29.3 MHz (scaled from 0.0 MHz), 31.6 kHz, 60.1 Hz
[    13.267] (II) DL(0): Modeline "800x480"x60.1   29.30  800 840 888 928  480 493 496 525 -hsync -vsync (31.6 kHz)
[    13.267] (**) DL(0): Display dimensions: (150, 80) mm
[    13.267] (**) DL(0): DPI set to (135, 152)
[    13.268] drmOpenDevice: node name is /dev/dri/card0
[    13.268] drmOpenDevice: open result is 12, (OK)
[    13.268] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.268] drmOpenDevice: node name is /dev/dri/card0
[    13.268] drmOpenDevice: open result is 12, (OK)
[    13.268] drmOpenByBusid: drmOpenMinor returns 12
[    13.268] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.268] drmOpenDevice: node name is /dev/dri/card0
[    13.268] drmOpenDevice: open result is 13, (OK)
[    13.268] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.268] drmOpenDevice: node name is /dev/dri/card0
[    13.269] drmOpenDevice: open result is 13, (OK)
[    13.269] drmOpenByBusid: drmOpenMinor returns 13
[    13.269] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    13.269] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.271] drmOpenDevice: node name is /dev/dri/card0
[    13.272] drmOpenDevice: open result is 14, (OK)
[    13.272] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.272] drmOpenDevice: node name is /dev/dri/card0
[    13.272] drmOpenDevice: open result is 14, (OK)
[    13.272] drmOpenByBusid: drmOpenMinor returns 14
[    13.272] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    13.272] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.272] (EE) pvr(1): PVRGetFrameBuffer: ERROR - no such PVR2D device: 1
[    13.272] (II) UnloadModule: "pvr"
[    13.272] (II) Unloading pvr
[    13.273] (==) DL(0): Backing store disabled
[    13.273] (==) DL(0): DPMS enabled
[    13.273] (II) DL(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.273] (--) RandR disabled
[    13.273] (II) Initializing built-in extension Generic Event Extension
[    13.273] (II) Initializing built-in extension SHAPE
[    13.273] (II) Initializing built-in extension MIT-SHM
[    13.273] (II) Initializing built-in extension XInputExtension
[    13.273] (II) Initializing built-in extension XTEST
[    13.273] (II) Initializing built-in extension BIG-REQUESTS
[    13.273] (II) Initializing built-in extension SYNC
[    13.273] (II) Initializing built-in extension XKEYBOARD
[    13.273] (II) Initializing built-in extension XC-MISC
[    13.273] (II) Initializing built-in extension SECURITY
[    13.273] (II) Initializing built-in extension XINERAMA
[    13.273] (II) Initializing built-in extension XFIXES
[    13.273] (II) Initializing built-in extension RENDER
[    13.273] (II) Initializing built-in extension RANDR
[    13.273] (II) Initializing built-in extension COMPOSITE
[    13.273] (II) Initializing built-in extension DAMAGE
[    13.337] (II) AIGLX: Loaded and initialized swrast
[    13.337] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    13.378] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.386] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    13.386] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.386] (II) LoadModule: "evdev"
[    13.387] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.387] (II) Module evdev: vendor="X.Org Foundation"
[    13.387]    compiled for 1.11.3, module version = 2.7.0
[    13.387]    Module class: X.Org XInput Driver
[    13.387]    ABI class: X.Org XInput driver, version 16.0
[    13.387] (II) Using input driver 'evdev' for 'Power Button'
[    13.387] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.387] (**) Power Button: always reports core events
[    13.387] (**) evdev: Power Button: Device: "/dev/input/event2"
[    13.387] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.389] (--) evdev: Power Button: Found keys
[    13.389] (II) evdev: Power Button: Configuring as keyboard
[    13.389] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    13.389] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    13.390] (**) Option "xkb_rules" "evdev"
[    13.390] (**) Option "xkb_model" "pc105"
[    13.390] (**) Option "xkb_layout" "cz"
[    13.395] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    13.398] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    13.398] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.398] (II) Using input driver 'evdev' for 'Video Bus'
[    13.398] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.398] (**) Video Bus: always reports core events
[    13.398] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    13.398] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    13.398] (--) evdev: Video Bus: Found keys
[    13.398] (II) evdev: Video Bus: Configuring as keyboard
[    13.398] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6"
[    13.398] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    13.398] (**) Option "xkb_rules" "evdev"
[    13.398] (**) Option "xkb_model" "pc105"
[    13.398] (**) Option "xkb_layout" "cz"
[    13.400] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.400] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.400] (II) Using input driver 'evdev' for 'Power Button'
[    13.400] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.400] (**) Power Button: always reports core events
[    13.400] (**) evdev: Power Button: Device: "/dev/input/event0"
[    13.400] (--) evdev: Power Button: Vendor 0 Product 0x1
[    13.401] (--) evdev: Power Button: Found keys
[    13.401] (II) evdev: Power Button: Configuring as keyboard
[    13.401] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    13.401] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    13.401] (**) Option "xkb_rules" "evdev"
[    13.401] (**) Option "xkb_model" "pc105"
[    13.401] (**) Option "xkb_layout" "cz"
[    13.402] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    13.402] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.402] (II) Using input driver 'evdev' for 'Sleep Button'
[    13.402] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.402] (**) Sleep Button: always reports core events
[    13.402] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    13.402] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    13.402] (--) evdev: Sleep Button: Found keys
[    13.402] (II) evdev: Sleep Button: Configuring as keyboard
[    13.403] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    13.403] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    13.403] (**) Option "xkb_rules" "evdev"
[    13.403] (**) Option "xkb_model" "pc105"
[    13.403] (**) Option "xkb_layout" "cz"
[    13.404] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event3)
[    13.404] (II) No input driver specified, ignoring this device.
[    13.404] (II) This device may have been added with another device file.
[    13.405] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event4)
[    13.405] (II) No input driver specified, ignoring this device.
[    13.405] (II) This device may have been added with another device file.
[    13.406] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event5)
[    13.406] (II) No input driver specified, ignoring this device.
[    13.406] (II) This device may have been added with another device file.
[    13.407] (II) config/udev: Adding input device EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface (/dev/input/event7)
[    13.407] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Applying InputClass "evdev pointer catchall"
[    13.407] (II) Using input driver 'evdev' for 'EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface'
[    13.407] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.407] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: always reports core events
[    13.407] (**) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Device: "/dev/input/event7"
[    13.407] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Vendor 0x4e7 Product 0x50
[    13.407] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found 1 mouse buttons
[    13.407] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found absolute axes
[    13.407] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found x and y absolute axes
[    13.407] (--) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Found absolute touchscreen
[    13.407] (II) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: Configuring as touchscreen
[    13.407] (**) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: YAxisMapping: buttons 4 and 5
[    13.407] (**) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.407] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.3/1-6.3:1.0/input/input7/event7"
[    13.407] (II) XINPUT: Adding extended input device "EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface" (type: TOUCHSCREEN, id 10)
[    13.407] (II) evdev: EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: initialized for absolute axes.
[    13.408] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) keeping acceleration scheme 1
[    13.408] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) acceleration profile 0
[    13.408] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) acceleration factor: 2.000
[    13.408] (**) EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface: (accel) acceleration threshold: 4
[    13.409] (II) config/udev: Adding input device EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface (/dev/input/js0)
[    13.409] (II) No input driver specified, ignoring this device.
[    13.409] (II) This device may have been added with another device file.
[    13.409] (II) config/udev: Adding input device EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch® USB Touchmonitor Interface (/dev/input/mouse0)
[    13.409] (II) No input driver specified, ignoring this device.
[    13.409] (II) This device may have been added with another device file.
[    13.410] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/event8)
[    13.410] (**) Genius       Optical Mouse: Applying InputClass "evdev pointer catchall"
[    13.410] (II) Using input driver 'evdev' for 'Genius       Optical Mouse'
[    13.410] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.410] (**) Genius       Optical Mouse: always reports core events
[    13.411] (**) evdev: Genius       Optical Mouse: Device: "/dev/input/event8"
[    13.411] (--) evdev: Genius       Optical Mouse: Vendor 0x458 Product 0x3a
[    13.411] (--) evdev: Genius       Optical Mouse: Found 3 mouse buttons
[    13.411] (--) evdev: Genius       Optical Mouse: Found scroll wheel(s)
[    13.411] (--) evdev: Genius       Optical Mouse: Found relative axes
[    13.411] (--) evdev: Genius       Optical Mouse: Found x and y relative axes
[    13.411] (II) evdev: Genius       Optical Mouse: Configuring as mouse
[    13.411] (II) evdev: Genius       Optical Mouse: Adding scrollwheel support
[    13.411] (**) evdev: Genius       Optical Mouse: YAxisMapping: buttons 4 and 5
[    13.411] (**) evdev: Genius       Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.411] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.2/1-8.2.1/1-8.2.1:1.0/input/input8/event8"
[    13.411] (II) XINPUT: Adding extended input device "Genius       Optical Mouse" (type: MOUSE, id 11)
[    13.411] (II) evdev: Genius       Optical Mouse: initialized for relative axes.
[    13.411] (**) Genius       Optical Mouse: (accel) keeping acceleration scheme 1
[    13.411] (**) Genius       Optical Mouse: (accel) acceleration profile 0
[    13.411] (**) Genius       Optical Mouse: (accel) acceleration factor: 2.000
[    13.411] (**) Genius       Optical Mouse: (accel) acceleration threshold: 4
[    13.412] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/mouse1)
[    13.412] (II) No input driver specified, ignoring this device.
[    13.412] (II) This device may have been added with another device file.
[    13.414] (II) config/udev: Adding input device CHICONY Compaq USB Keyboard (/dev/input/event9)
[    13.414] (**) CHICONY Compaq USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    13.414] (II) Using input driver 'evdev' for 'CHICONY Compaq USB Keyboard'
[    13.414] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.414] (**) CHICONY Compaq USB Keyboard: always reports core events
[    13.414] (**) evdev: CHICONY Compaq USB Keyboard: Device: "/dev/input/event9"
[    13.414] (--) evdev: CHICONY Compaq USB Keyboard: Vendor 0x49f Product 0x51
[    13.414] (--) evdev: CHICONY Compaq USB Keyboard: Found keys
[    13.414] (II) evdev: CHICONY Compaq USB Keyboard: Configuring as keyboard
[    13.414] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.2/1-8.2.3/1-8.2.3.2/1-8.2.3.2:1.0/input/input9/event9"
[    13.414] (II) XINPUT: Adding extended input device "CHICONY Compaq USB Keyboard" (type: KEYBOARD, id 12)
[    13.414] (**) Option "xkb_rules" "evdev"
[    13.415] (**) Option "xkb_model" "pc105"
[    13.415] (**) Option "xkb_layout" "cz"
[    13.417] (II) config/udev: Adding input device CHICONY Compaq USB Keyboard (/dev/input/event10)
[    13.417] (**) CHICONY Compaq USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    13.417] (II) Using input driver 'evdev' for 'CHICONY Compaq USB Keyboard'
[    13.417] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.417] (**) CHICONY Compaq USB Keyboard: always reports core events
[    13.417] (**) evdev: CHICONY Compaq USB Keyboard: Device: "/dev/input/event10"
[    13.417] (--) evdev: CHICONY Compaq USB Keyboard: Vendor 0x49f Product 0x51
[    13.417] (--) evdev: CHICONY Compaq USB Keyboard: Found keys
[    13.417] (II) evdev: CHICONY Compaq USB Keyboard: Configuring as keyboard
[    13.417] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.2/1-8.2.3/1-8.2.3.2/1-8.2.3.2:1.1/input/input10/event10"
[    13.417] (II) XINPUT: Adding extended input device "CHICONY Compaq USB Keyboard" (type: KEYBOARD, id 13)
[    13.417] (**) Option "xkb_rules" "evdev"
[    13.418] (**) Option "xkb_model" "pc105"
[    13.418] (**) Option "xkb_layout" "cz"
[    14.795] (II) XKB: reuse xkmfile /var/lib/xkb/server-6312AA7F541A1077FD766490800F036AD4583782.xkm
[    14.801] (II) XKB: reuse xkmfile /var/lib/xkb/server-6312AA7F541A1077FD766490800F036AD4583782.xkm
```

---

### Post by mörgæs on 2016-01-22
First of all I think you should begin with a fresh install of 15.10.

Cedarview and some other Atoms have been a problem for some time but support has increased a lot during the latest Buntu iterations.

---

### Post by Nyyr on 2016-01-26
I try 16.04 when it comes out, I definitely want only LTS version. And with 14.04 the DisplayLink monitor does not work at all....

---

### Post by mörgæs on 2016-01-27
That's interesting. So, what are you going to do until then?

---

