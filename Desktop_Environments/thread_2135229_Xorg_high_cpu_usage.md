---
title: "Xorg high cpu usage"
date: 2013-04-13
forum: Desktop Environments
---

### Post by mreq on 2013-04-13
Recently I've noticed on my Xubuntu 12.04 system, that after a few hours of uptime, the CPU Usage of Xorg is ~ 20% when idling. That's way too much - on a fresh session it's bellow or ~ 1%. On my previous systems (regular Ubuntu), there was no such thing.
Is there a way how to see what exactly is Xorg doing?


```
petr@sova:~$ uptime
21:29:25 up 11:58,  1 user,  load average: 2.98, 3.28, 3.34

```


```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                 
 1709 root      20   0  236m  50m  35m S   27  0.6  36:39.07 Xorg       
```


/var/log/Xorg.0.log:


```
[     5.496] X.Org X Server 1.11.3
Release Date: 2011-12-16
[     5.496] X Protocol Version 11, Revision 0
[     5.496] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[     5.496] Current Operating System: Linux sova 3.2.0-40-generic #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013 x86_64
[     5.496] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-40-generic root=UUID=8df853de-c48d-4931-80b9-7de336f71fd3 ro quiet splash vt.handoff=7
[     5.496] Build Date: 27 February 2013  02:07:42AM
[     5.496] xorg-server 2:1.11.4-0ubuntu10.12 (For technical support please see http://www.ubuntu.com/support) 
[     5.496] Current version of pixman: 0.24.4
[     5.496]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     5.496] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.496] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 13 09:30:46 2013
[     5.498] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.498] (==) No Layout section.  Using the first Screen section.
[     5.498] (==) No screen section available. Using defaults.
[     5.498] (**) |-->Screen "Default Screen Section" (0)
[     5.498] (**) |   |-->Monitor "<default monitor>"
[     5.500] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     5.500] (==) Automatically adding devices
[     5.500] (==) Automatically enabling devices
[     5.503] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.503]     Entry deleted from font path.
[     5.503] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.503]     Entry deleted from font path.
[     5.504] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.504]     Entry deleted from font path.
[     5.505] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.505]     Entry deleted from font path.
[     5.505] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.505]     Entry deleted from font path.
[     5.505] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     5.505]     Entry deleted from font path.
[     5.505] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.505] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.505] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.505] (II) Loader magic: 0x7f0e67597b00
[     5.505] (II) Module ABI versions:
[     5.505]     X.Org ANSI C Emulation: 0.4
[     5.505]     X.Org Video Driver: 11.0
[     5.505]     X.Org XInput driver : 16.0
[     5.505]     X.Org Server Extension : 6.0
[     5.505] (--) PCI:*(0:0:2:0) 8086:0126:104d:9084 rev 9, Mem @ 0xd0000000/4194304, 0xa0000000/268435456, I/O @ 0x0000a000/64
[     5.505] (II) Open ACPI successful (/var/run/acpid.socket)
[     5.505] (II) LoadModule: "extmod"
[     5.508] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     5.508] (II) Module extmod: vendor="X.Org Foundation"
[     5.508]     compiled for 1.11.3, module version = 1.0.0
[     5.508]     Module class: X.Org Server Extension
[     5.508]     ABI class: X.Org Server Extension, version 6.0
[     5.508] (II) Loading extension MIT-SCREEN-SAVER
[     5.508] (II) Loading extension XFree86-VidModeExtension
[     5.508] (II) Loading extension XFree86-DGA
[     5.508] (II) Loading extension DPMS
[     5.508] (II) Loading extension XVideo
[     5.508] (II) Loading extension XVideo-MotionCompensation
[     5.508] (II) Loading extension X-Resource
[     5.508] (II) LoadModule: "dbe"
[     5.508] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     5.512] (II) Module dbe: vendor="X.Org Foundation"
[     5.512]     compiled for 1.11.3, module version = 1.0.0
[     5.512]     Module class: X.Org Server Extension
[     5.512]     ABI class: X.Org Server Extension, version 6.0
[     5.512] (II) Loading extension DOUBLE-BUFFER
[     5.512] (II) LoadModule: "glx"
[     5.512] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     5.563] (II) Module glx: vendor="X.Org Foundation"
[     5.563]     compiled for 1.11.3, module version = 1.0.0
[     5.563]     ABI class: X.Org Server Extension, version 6.0
[     5.563] (==) AIGLX enabled
[     5.563] (II) Loading extension GLX
[     5.563] (II) LoadModule: "record"
[     5.563] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     5.565] (II) Module record: vendor="X.Org Foundation"
[     5.565]     compiled for 1.11.3, module version = 1.13.0
[     5.565]     Module class: X.Org Server Extension
[     5.565]     ABI class: X.Org Server Extension, version 6.0
[     5.565] (II) Loading extension RECORD
[     5.565] (II) LoadModule: "dri"
[     5.565] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     5.751] (II) Module dri: vendor="X.Org Foundation"
[     5.751]     compiled for 1.11.3, module version = 1.0.0
[     5.751]     ABI class: X.Org Server Extension, version 6.0
[     5.751] (II) Loading extension XFree86-DRI
[     5.751] (II) LoadModule: "dri2"
[     5.751] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     5.753] (II) Module dri2: vendor="X.Org Foundation"
[     5.753]     compiled for 1.11.3, module version = 1.2.0
[     5.753]     ABI class: X.Org Server Extension, version 6.0
[     5.753] (II) Loading extension DRI2
[     5.753] (==) Matched intel as autoconfigured driver 0
[     5.753] (==) Matched vesa as autoconfigured driver 1
[     5.753] (==) Matched fbdev as autoconfigured driver 2
[     5.753] (==) Assigned the driver to the xf86ConfigLayout
[     5.753] (II) LoadModule: "intel"
[     5.754] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.754] (II) Module intel: vendor="X.Org Foundation"
[     5.754]     compiled for 1.11.3, module version = 2.17.0
[     5.754]     Module class: X.Org Video Driver
[     5.754]     ABI class: X.Org Video Driver, version 11.0
[     5.754] (II) LoadModule: "vesa"
[     5.754] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.760] (II) Module vesa: vendor="X.Org Foundation"
[     5.760]     compiled for 1.11.3, module version = 2.3.0
[     5.760]     Module class: X.Org Video Driver
[     5.760]     ABI class: X.Org Video Driver, version 11.0
[     5.760] (II) LoadModule: "fbdev"
[     5.760] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.767] (II) Module fbdev: vendor="X.Org Foundation"
[     5.767]     compiled for 1.11.3, module version = 0.4.2
[     5.767]     ABI class: X.Org Video Driver, version 11.0
[     5.774] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[     5.774] (II) VESA: driver for VESA chipsets: vesa
[     5.774] (II) FBDEV: driver for framebuffer: fbdev
[     5.774] (++) using VT number 7




[     5.775] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.775] (WW) Falling back to old probe method for vesa
[     5.775] (WW) Falling back to old probe method for fbdev
[     5.775] (II) Loading sub module "fbdevhw"
[     5.775] (II) LoadModule: "fbdevhw"
[     5.778] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.778] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.778]     compiled for 1.11.3, module version = 0.0.2
[     5.778]     ABI class: X.Org Video Driver, version 11.0
[     5.778] drmOpenDevice: node name is /dev/dri/card0
[     5.778] drmOpenDevice: open result is 9, (OK)
[     6.919] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     6.919] drmOpenDevice: node name is /dev/dri/card0
[     6.919] drmOpenDevice: open result is 9, (OK)
[     6.919] drmOpenByBusid: drmOpenMinor returns 9
[     6.919] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     6.919] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     6.919] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     6.919] (==) intel(0): RGB weight 888
[     6.919] (==) intel(0): Default visual is TrueColor
[     6.919] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2+)
[     6.919] (--) intel(0): Chipset: "Sandybridge Mobile (GT2+)"
[     6.919] (**) intel(0): Relaxed fencing enabled
[     6.919] (**) intel(0): Wait on SwapBuffers? enabled
[     6.919] (**) intel(0): Triple buffering? enabled
[     6.919] (**) intel(0): Framebuffer tiled
[     6.919] (**) intel(0): Pixmaps tiled
[     6.919] (**) intel(0): 3D buffers tiled
[     6.919] (**) intel(0): SwapBuffers wait enabled
[     6.919] (==) intel(0): video overlay key set to 0x101fe
[     6.975] (II) intel(0): Output eDP1 has no monitor section
[     6.975] (II) intel(0): Output VGA1 has no monitor section
[     7.211] (II) intel(0): Output HDMI1 has no monitor section
[     7.256] (II) intel(0): Output DP1 has no monitor section
[     7.312] (II) intel(0): EDID for output eDP1
[     7.312] (II) intel(0): Manufacturer: SNY  Model: 6fa  Serial#: 16843009
[     7.312] (II) intel(0): Year: 2011  Week: 34
[     7.312] (II) intel(0): EDID Version: 1.4
[     7.312] (II) intel(0): Digital Display Input
[     7.312] (II) intel(0): 6 bits per channel
[     7.312] (II) intel(0): Digital interface is DisplayPort
[     7.312] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 16
[     7.312] (II) intel(0): Gamma: 2.20
[     7.312] (II) intel(0): No DPMS capabilities specified
[     7.312] (II) intel(0): Supported color encodings: RGB 4:4:4 
[     7.312] (II) intel(0): First detailed timing is preferred mode
[     7.312] (II) intel(0): Preferred mode is native pixel format and refresh rate
[     7.312] (II) intel(0): redX: 0.602 redY: 0.336   greenX: 0.296 greenY: 0.546
[     7.312] (II) intel(0): blueX: 0.148 blueY: 0.126   whiteX: 0.313 whiteY: 0.329
[     7.312] (II) intel(0): Manufacturer's mask: 0
[     7.312] (II) intel(0): Supported standard timings:
[     7.312] (II) intel(0): #0: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[     7.312] (II) intel(0): Supported detailed timing:
[     7.312] (II) intel(0): clock: 108.0 MHz   Image Size:  291 x 164 mm
[     7.312] (II) intel(0): h_active: 1600  h_sync: 1664  h_sync_end 1728 h_blank_end 1969 h_border: 0
[     7.312] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 906 v_blanking: 915 v_border: 0
[     7.312] (II) intel(0): Supported detailed timing:
[     7.312] (II) intel(0): clock: 76.1 MHz   Image Size:  291 x 164 mm
[     7.312] (II) intel(0): h_active: 1600  h_sync: 1664  h_sync_end 1728 h_blank_end 2079 h_border: 0
[     7.312] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 906 v_blanking: 915 v_border: 0
[     7.312] (II) intel(0): Monitor name: Sony LCD
[     7.312] (II) intel(0): Ranges: V min: 39 V max: 61 Hz, H min: 36 H max: 55 kHz, PixClock max 115 MHz
[     7.312] (II) intel(0): EDID (in hex):
[     7.312] (II) intel(0):     00ffffffffffff004dd9fa0601010101
[     7.312] (II) intel(0):     22150104951d1078020f159a564b8b26
[     7.312] (II) intel(0):     205054000000a9c00101010101010101
[     7.312] (II) intel(0):     0101010101012f2a407161840f304040
[     7.312] (II) intel(0):     330023a410000018b91d40df61840f30
[     7.312] (II) intel(0):     4040330023a410000018000000fc0053
[     7.312] (II) intel(0):     6f6e79204c43440a20202020000000fd
[     7.312] (II) intel(0):     00273d24370b000a20202020202000db
[     7.312] (II) intel(0): EDID vendor "SNY", prod id 1786
[     7.312] (II) intel(0): Using EDID range info for horizontal sync
[     7.312] (II) intel(0): Using EDID range info for vertical refresh
[     7.312] (II) intel(0): Printing DDC gathered Modelines:
[     7.312] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[     7.312] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[     7.312] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[     7.312] (II) intel(0): Printing probed modes for output eDP1
[     7.312] (II) intel(0): Modeline "1600x900"x59.9  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[     7.312] (II) intel(0): Modeline "1600x900"x40.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[     7.312] (II) intel(0): EDID for output VGA1
[     7.547] (II) Quirked EDID physical size to 0x0 cm
[     7.547] (II) intel(0): EDID for output HDMI1
[     7.547] (II) intel(0): Manufacturer: SAM  Model: 5cd  Serial#: 808464435
[     7.547] (II) intel(0): Year: 2010  Week: 36
[     7.547] (II) intel(0): EDID Version: 1.3
[     7.547] (II) intel(0): Digital Display Input
[     7.547] (II) intel(0): Indeterminate output size
[     7.547] (II) intel(0): Gamma: 2.20
[     7.547] (II) intel(0): DPMS capabilities: Off
[     7.547] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     7.547] (II) intel(0): First detailed timing is preferred mode
[     7.547] (II) intel(0): redX: 0.649 redY: 0.338   greenX: 0.289 greenY: 0.609
[     7.547] (II) intel(0): blueX: 0.146 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[     7.547] (II) intel(0): Supported established timings:
[     7.547] (II) intel(0): 640x480@60Hz
[     7.547] (II) intel(0): 800x600@56Hz
[     7.547] (II) intel(0): 800x600@60Hz
[     7.547] (II) intel(0): 1024x768@60Hz
[     7.547] (II) intel(0): Manufacturer's mask: 0
[     7.547] (II) intel(0): Supported standard timings:
[     7.547] (II) intel(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[     7.547] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     7.547] (II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     7.547] (II) intel(0): #3: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     7.547] (II) intel(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     7.547] (II) intel(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     7.548] (II) intel(0): Supported detailed timing:
[     7.548] (II) intel(0): clock: 148.5 MHz   Image Size:  160 x 90 mm
[     7.548] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     7.548] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     7.548] (II) intel(0): Supported detailed timing:
[     7.548] (II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[     7.548] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[     7.548] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     7.548] (II) intel(0): Ranges: V min: 50 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[     7.548] (II) intel(0): Monitor name: SyncMaster
[     7.548] (II) intel(0): Supported detailed timing:
[     7.548] (II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[     7.548] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     7.548] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     7.548] (II) intel(0): Supported detailed timing:
[     7.548] (II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[     7.548] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     7.548] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     7.548] (II) intel(0): Supported detailed timing:
[     7.548] (II) intel(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
[     7.548] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[     7.548] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     7.548] (II) intel(0): Supported detailed timing:
[     7.548] (II) intel(0): clock: 27.0 MHz   Image Size:  160 x 90 mm
[     7.548] (II) intel(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[     7.548] (II) intel(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[     7.548] (II) intel(0): Supported detailed timing:
[     7.548] (II) intel(0): clock: 27.0 MHz   Image Size:  160 x 90 mm
[     7.548] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[     7.548] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[     7.548] (II) intel(0): Number of EDID sections to follow: 1
[     7.548] (II) intel(0): EDID (in hex):
[     7.548] (II) intel(0):     00ffffffffffff004c2dcd0533303030
[     7.548] (II) intel(0):     24140103801009782a6041a6564a9c25
[     7.548] (II) intel(0):     125054230800a9408180814081009500
[     7.548] (II) intel(0):     b30001010101023a801871382d40582c
[     7.548] (II) intel(0):     4500a05a0000001e011d007251d01e20
[     7.548] (II) intel(0):     6e285500a05a0000001e000000fd0032
[     7.548] (II) intel(0):     3c1e5111000a202020202020000000fc
[     7.548] (II) intel(0):     0053796e634d61737465720a202001be
[     7.548] (II) intel(0):     02031cf14890041f0514130312230907
[     7.548] (II) intel(0):     078301000066030c00100080011d80d0
[     7.548] (II) intel(0):     721c1620102c2580a05a0000009e011d
[     7.548] (II) intel(0):     8018711c1620582c2500a05a0000009e
[     7.548] (II) intel(0):     011d00bc52d01e20b8285540a05a0000
[     7.548] (II) intel(0):     001e8c0ad090204031200c405500a05a
[     7.548] (II) intel(0):     000000188c0ad08a20e02d10103e9600
[     7.548] (II) intel(0):     a05a0000001800000000000000000046
[     7.548] (II) intel(0): Printing probed modes for output HDMI1
[     7.548] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[     7.548] (II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[     7.548] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[     7.548] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[     7.548] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[     7.548] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[     7.548] (II) intel(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[     7.548] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     7.548] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[     7.548] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[     7.548] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[     7.548] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[     7.596] (II) intel(0): EDID for output DP1
[     7.596] (II) intel(0): Output eDP1 connected
[     7.596] (II) intel(0): Output VGA1 disconnected
[     7.596] (II) intel(0): Output HDMI1 connected
[     7.596] (II) intel(0): Output DP1 disconnected
[     7.596] (II) intel(0): Using sloppy heuristic for initial modes
[     7.596] (II) intel(0): Output eDP1 using initial mode 1600x900
[     7.596] (II) intel(0): Output HDMI1 using initial mode 1440x900
[     7.596] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     7.596] (II) intel(0): Kernel page flipping support detected, enabling
[     7.596] (**) intel(0): Display dimensions: (290, 160) mm
[     7.596] (**) intel(0): DPI set to (140, 142)
[     7.596] (II) Loading sub module "fb"
[     7.596] (II) LoadModule: "fb"
[     7.596] (II) Loading /usr/lib/xorg/modules/libfb.so
[     7.596] (II) Module fb: vendor="X.Org Foundation"
[     7.596]     compiled for 1.11.3, module version = 1.0.0
[     7.596]     ABI class: X.Org ANSI C Emulation, version 0.4
[     7.596] (II) Loading sub module "dri2"
[     7.596] (II) LoadModule: "dri2"
[     7.596] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     7.596] (II) Module dri2: vendor="X.Org Foundation"
[     7.596]     compiled for 1.11.3, module version = 1.2.0
[     7.596]     ABI class: X.Org Server Extension, version 6.0
[     7.596] (II) UnloadModule: "vesa"
[     7.596] (II) Unloading vesa
[     7.596] (II) UnloadModule: "fbdev"
[     7.596] (II) Unloading fbdev
[     7.596] (II) UnloadModule: "fbdevhw"
[     7.596] (II) Unloading fbdevhw
[     7.596] (==) Depth 24 pixmap format is 32 bpp
[     7.596] (II) intel(0): [DRI2] Setup complete
[     7.596] (II) intel(0): [DRI2]   DRI driver: i965
[     7.596] (II) intel(0): Allocated new frame buffer 1600x900 stride 6656, tiled
[     7.601] (II) UXA(0): Driver registered support for the following operations:
[     7.601] (II)         solid
[     7.601] (II)         copy
[     7.601] (II)         composite (RENDER acceleration)
[     7.601] (II)         put_image
[     7.601] (II)         get_image
[     7.601] (==) intel(0): Backing store disabled
[     7.601] (==) intel(0): Silken mouse enabled
[     7.601] (II) intel(0): Initializing HW Cursor
[     8.079] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     8.079] (==) intel(0): DPMS enabled
[     8.079] (==) intel(0): Intel XvMC decoder enabled
[     8.079] (II) intel(0): Set up textured video
[     8.079] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     8.079] (II) intel(0): direct rendering: DRI2 Enabled
[     8.079] (==) intel(0): hotplug detection: "enabled"
[     8.080] (--) RandR disabled
[     8.080] (II) Initializing built-in extension Generic Event Extension
[     8.080] (II) Initializing built-in extension SHAPE
[     8.080] (II) Initializing built-in extension MIT-SHM
[     8.080] (II) Initializing built-in extension XInputExtension
[     8.080] (II) Initializing built-in extension XTEST
[     8.080] (II) Initializing built-in extension BIG-REQUESTS
[     8.080] (II) Initializing built-in extension SYNC
[     8.080] (II) Initializing built-in extension XKEYBOARD
[     8.080] (II) Initializing built-in extension XC-MISC
[     8.080] (II) Initializing built-in extension SECURITY
[     8.080] (II) Initializing built-in extension XINERAMA
[     8.080] (II) Initializing built-in extension XFIXES
[     8.080] (II) Initializing built-in extension RENDER
[     8.080] (II) Initializing built-in extension RANDR
[     8.080] (II) Initializing built-in extension COMPOSITE
[     8.080] (II) Initializing built-in extension DAMAGE
[     8.086] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     8.086] (II) AIGLX: enabled GLX_INTEL_swap_event
[     8.086] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     8.086] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     8.086] (II) AIGLX: Loaded and initialized i965
[     8.086] (II) GLX: Initialized DRI2 GL provider for screen 0
[     8.086] (II) intel(0): Setting screen physical size to 423 x 238
[     8.094] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.096] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[     8.096] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     8.096] (II) LoadModule: "evdev"
[     8.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.098] (II) Module evdev: vendor="X.Org Foundation"
[     8.098]     compiled for 1.11.3, module version = 2.7.0
[     8.098]     Module class: X.Org XInput Driver
[     8.098]     ABI class: X.Org XInput driver, version 16.0
[     8.098] (II) Using input driver 'evdev' for 'Video Bus'
[     8.098] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.098] (**) Video Bus: always reports core events
[     8.098] (**) evdev: Video Bus: Device: "/dev/input/event8"
[     8.099] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     8.099] (--) evdev: Video Bus: Found keys
[     8.099] (II) evdev: Video Bus: Configuring as keyboard
[     8.099] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:09/input/input8/event8"
[     8.099] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[     8.099] (**) Option "xkb_rules" "evdev"
[     8.099] (**) Option "xkb_model" "pc105"
[     8.099] (**) Option "xkb_layout" "us"
[     8.099] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event3)
[     8.099] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[     8.099] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[     8.099] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.099] (**) Sony Vaio Keys: always reports core events
[     8.099] (**) evdev: Sony Vaio Keys: Device: "/dev/input/event3"
[     8.099] (--) evdev: Sony Vaio Keys: Vendor 0x104d Product 0
[     8.099] (--) evdev: Sony Vaio Keys: Found keys
[     8.099] (II) evdev: Sony Vaio Keys: Configuring as keyboard
[     8.099] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input3/event3"
[     8.099] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD, id 7)
[     8.099] (**) Option "xkb_rules" "evdev"
[     8.099] (**) Option "xkb_model" "pc105"
[     8.099] (**) Option "xkb_layout" "us"
[     8.099] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.099] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.099] (II) Using input driver 'evdev' for 'Power Button'
[     8.099] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.099] (**) Power Button: always reports core events
[     8.099] (**) evdev: Power Button: Device: "/dev/input/event1"
[     8.099] (--) evdev: Power Button: Vendor 0 Product 0x1
[     8.099] (--) evdev: Power Button: Found keys
[     8.099] (II) evdev: Power Button: Configuring as keyboard
[     8.099] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     8.099] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     8.099] (**) Option "xkb_rules" "evdev"
[     8.099] (**) Option "xkb_model" "pc105"
[     8.099] (**) Option "xkb_layout" "us"
[     8.100] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     8.100] (II) No input driver specified, ignoring this device.
[     8.100] (II) This device may have been added with another device file.
[     8.100] (II) config/udev: Adding input device USB2.0 Camera (/dev/input/event5)
[     8.100] (**) USB2.0 Camera: Applying InputClass "evdev keyboard catchall"
[     8.100] (II) Using input driver 'evdev' for 'USB2.0 Camera'
[     8.100] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.100] (**) USB2.0 Camera: always reports core events
[     8.100] (**) evdev: USB2.0 Camera: Device: "/dev/input/event5"
[     8.100] (--) evdev: USB2.0 Camera: Vendor 0x5c8 Product 0x318
[     8.100] (--) evdev: USB2.0 Camera: Found keys
[     8.100] (II) evdev: USB2.0 Camera: Configuring as keyboard
[     8.100] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input5/event5"
[     8.100] (II) XINPUT: Adding extended input device "USB2.0 Camera" (type: KEYBOARD, id 9)
[     8.100] (**) Option "xkb_rules" "evdev"
[     8.100] (**) Option "xkb_model" "pc105"
[     8.100] (**) Option "xkb_layout" "us"
[     8.100] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[     8.100] (II) No input driver specified, ignoring this device.
[     8.100] (II) This device may have been added with another device file.
[     8.100] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[     8.100] (II) No input driver specified, ignoring this device.
[     8.100] (II) This device may have been added with another device file.
[     8.101] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event7)
[     8.101] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[     8.101] (II) Using input driver 'evdev' for 'Logitech USB Gaming Mouse'
[     8.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.101] (**) Logitech USB Gaming Mouse: always reports core events
[     8.101] (**) evdev: Logitech USB Gaming Mouse: Device: "/dev/input/event7"
[     8.101] (--) evdev: Logitech USB Gaming Mouse: Vendor 0x46d Product 0xc041
[     8.101] (--) evdev: Logitech USB Gaming Mouse: Found 20 mouse buttons
[     8.101] (--) evdev: Logitech USB Gaming Mouse: Found scroll wheel(s)
[     8.101] (--) evdev: Logitech USB Gaming Mouse: Found relative axes
[     8.101] (--) evdev: Logitech USB Gaming Mouse: Found x and y relative axes
[     8.101] (II) evdev: Logitech USB Gaming Mouse: Configuring as mouse
[     8.101] (II) evdev: Logitech USB Gaming Mouse: Adding scrollwheel support
[     8.101] (**) evdev: Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[     8.101] (**) evdev: Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.101] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2.6/2-1.2.6:1.0/input/input7/event7"
[     8.101] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE, id 10)
[     8.101] (II) evdev: Logitech USB Gaming Mouse: initialized for relative axes.
[     8.101] (**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
[     8.101] (**) Logitech USB Gaming Mouse: (accel) acceleration profile 0
[     8.101] (**) Logitech USB Gaming Mouse: (accel) acceleration factor: 2.000
[     8.101] (**) Logitech USB Gaming Mouse: (accel) acceleration threshold: 4
[     8.101] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse2)
[     8.101] (II) No input driver specified, ignoring this device.
[     8.101] (II) This device may have been added with another device file.
[     8.101] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     8.101] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     8.101] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     8.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.101] (**) AT Translated Set 2 keyboard: always reports core events
[     8.101] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[     8.101] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     8.101] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     8.101] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     8.101] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[     8.101] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[     8.101] (**) Option "xkb_rules" "evdev"
[     8.101] (**) Option "xkb_model" "pc105"
[     8.101] (**) Option "xkb_layout" "us"
[     8.102] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[     8.102] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     8.102] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     8.102] (II) LoadModule: "synaptics"
[     8.102] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     8.103] (II) Module synaptics: vendor="X.Org Foundation"
[     8.103]     compiled for 1.11.3, module version = 1.6.2
[     8.103]     Module class: X.Org XInput Driver
[     8.103]     ABI class: X.Org XInput driver, version 16.0
[     8.103] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     8.103] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     8.103] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     8.103] (**) Option "Device" "/dev/input/event6"
[     8.128] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     8.128] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[     8.128] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[     8.128] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     8.128] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     8.128] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     8.128] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     8.128] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     8.128] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     8.132] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[     8.132] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[     8.132] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     8.132] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[     8.132] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[     8.132] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     8.132] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     8.132] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     8.132] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     8.132] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     8.132] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[     8.132] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     8.133] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event4)
[     8.133] (II) No input driver specified, ignoring this device.
[     8.133] (II) This device may have been added with another device file.
[     8.133] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse0)
[     8.133] (II) No input driver specified, ignoring this device.
[     8.133] (II) This device may have been added with another device file.
[    11.038] (II) intel(0): EDID vendor "SNY", prod id 1786
[    11.038] (II) intel(0): Using hsync ranges from config file
[    11.038] (II) intel(0): Using vrefresh ranges from config file
[    11.038] (II) intel(0): Printing DDC gathered Modelines:
[    11.038] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[    11.038] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[    11.038] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    11.273] (II) Quirked EDID physical size to 0x0 cm
[    11.376] (II) intel(0): EDID vendor "SNY", prod id 1786
[    11.376] (II) intel(0): Using hsync ranges from config file
[    11.376] (II) intel(0): Using vrefresh ranges from config file
[    11.376] (II) intel(0): Printing DDC gathered Modelines:
[    11.376] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[    11.376] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[    11.376] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    11.609] (II) Quirked EDID physical size to 0x0 cm
[    11.735] (II) intel(0): EDID vendor "SNY", prod id 1786
[    11.735] (II) intel(0): Using hsync ranges from config file
[    11.735] (II) intel(0): Using vrefresh ranges from config file
[    11.735] (II) intel(0): Printing DDC gathered Modelines:
[    11.735] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[    11.736] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[    11.736] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    11.969] (II) Quirked EDID physical size to 0x0 cm
[    12.213] (II) intel(0): EDID vendor "SNY", prod id 1786
[    12.213] (II) intel(0): Using hsync ranges from config file
[    12.213] (II) intel(0): Using vrefresh ranges from config file
[    12.213] (II) intel(0): Printing DDC gathered Modelines:
[    12.213] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[    12.213] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[    12.213] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    12.452] (II) Quirked EDID physical size to 0x0 cm
[    12.579] (II) intel(0): EDID vendor "SNY", prod id 1786
[    12.579] (II) intel(0): Using hsync ranges from config file
[    12.579] (II) intel(0): Using vrefresh ranges from config file
[    12.579] (II) intel(0): Printing DDC gathered Modelines:
[    12.579] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[    12.579] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[    12.579] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    12.818] (II) Quirked EDID physical size to 0x0 cm
[   583.062] (II) intel(0): EDID vendor "SNY", prod id 1786
[   583.062] (II) intel(0): Using hsync ranges from config file
[   583.062] (II) intel(0): Using vrefresh ranges from config file
[   583.062] (II) intel(0): Printing DDC gathered Modelines:
[   583.062] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[   583.062] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[   583.062] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[   583.312] (II) Quirked EDID physical size to 0x0 cm
[   585.089] (II) intel(0): EDID vendor "SNY", prod id 1786
[   585.089] (II) intel(0): Using hsync ranges from config file
[   585.089] (II) intel(0): Using vrefresh ranges from config file
[   585.089] (II) intel(0): Printing DDC gathered Modelines:
[   585.089] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[   585.089] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[   585.089] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[   585.337] (II) Quirked EDID physical size to 0x0 cm
[   586.809] (II) intel(0): EDID vendor "SNY", prod id 1786
[   586.809] (II) intel(0): Using hsync ranges from config file
[   586.809] (II) intel(0): Using vrefresh ranges from config file
[   586.809] (II) intel(0): Printing DDC gathered Modelines:
[   586.809] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[   586.809] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[   586.809] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[   587.059] (II) Quirked EDID physical size to 0x0 cm
[   587.172] (II) intel(0): EDID vendor "SNY", prod id 1786
[   587.172] (II) intel(0): Using hsync ranges from config file
[   587.172] (II) intel(0): Using vrefresh ranges from config file
[   587.172] (II) intel(0): Printing DDC gathered Modelines:
[   587.172] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[   587.172] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[   587.172] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[   587.421] (II) Quirked EDID physical size to 0x0 cm
[   587.504] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[   588.337] (II) intel(0): EDID vendor "SNY", prod id 1786
[   588.337] (II) intel(0): Using hsync ranges from config file
[   588.337] (II) intel(0): Using vrefresh ranges from config file
[   588.337] (II) intel(0): Printing DDC gathered Modelines:
[   588.337] (II) intel(0): Modeline "1600x900"x0.0  107.99  1600 1664 1728 1969  900 903 906 915 -hsync -vsync (54.8 kHz)
[   588.337] (II) intel(0): Modeline "1600x900"x0.0   76.09  1600 1664 1728 2079  900 903 906 915 -hsync -vsync (36.6 kHz)
[   588.337] (II) intel(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[   588.587] (II) Quirked EDID physical size to 0x0 cm
[   589.121] (II) Quirked EDID physical size to 0x0 cm
[   589.121] (II) intel(0): EDID vendor "SAM", prod id 1485
[   589.121] (II) intel(0): Using hsync ranges from config file
[   589.121] (II) intel(0): Using vrefresh ranges from config file
[   589.121] (II) intel(0): Printing DDC gathered Modelines:
[   589.121] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   589.121] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   589.121] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   589.121] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   589.121] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   589.121] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   589.121] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   589.121] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   589.121] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   589.121] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   589.121] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   589.121] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   589.121] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   589.121] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   589.121] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   589.121] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   589.121] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   589.121] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   589.121] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   589.121] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   589.613] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[   590.758] (II) Quirked EDID physical size to 0x0 cm
[   590.758] (II) intel(0): EDID vendor "SAM", prod id 1485
[   590.758] (II) intel(0): Using hsync ranges from config file
[   590.758] (II) intel(0): Using vrefresh ranges from config file
[   590.758] (II) intel(0): Printing DDC gathered Modelines:
[   590.758] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   590.758] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   590.758] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   590.758] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   590.758] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   590.758] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   590.759] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   590.759] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   590.759] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   590.759] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   590.759] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   590.759] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   590.759] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   590.759] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   590.759] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   590.759] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   590.759] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   590.759] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   590.759] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   590.759] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   591.132] (II) Quirked EDID physical size to 0x0 cm
[   591.132] (II) intel(0): EDID vendor "SAM", prod id 1485
[   591.132] (II) intel(0): Using hsync ranges from config file
[   591.132] (II) intel(0): Using vrefresh ranges from config file
[   591.132] (II) intel(0): Printing DDC gathered Modelines:
[   591.132] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   591.132] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   591.132] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   591.132] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   591.132] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   591.132] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   591.132] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   591.132] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   591.132] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   591.132] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   591.132] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   591.132] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   591.132] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   591.132] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   591.132] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   591.132] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   591.132] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   591.132] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   591.132] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   591.132] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[ 10080.444] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 10086.347] (II) Open ACPI successful (/var/run/acpid.socket)
[ 10086.347] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 10089.386] (II) Quirked EDID physical size to 0x0 cm
[ 10089.386] (II) intel(0): EDID vendor "SAM", prod id 1485
[ 10089.386] (II) intel(0): Using hsync ranges from config file
[ 10089.386] (II) intel(0): Using vrefresh ranges from config file
[ 10089.386] (II) intel(0): Printing DDC gathered Modelines:
[ 10089.386] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[ 10089.386] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[ 10089.386] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[ 10089.386] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[ 10089.386] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[ 10089.386] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[ 10089.386] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[ 10089.386] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 10089.386] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 10089.387] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 10089.387] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 10089.387] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[ 10089.387] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 10089.387] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[ 10089.387] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[ 10089.387] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[ 10089.387] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[ 10089.387] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[ 10089.387] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[ 10089.387] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[ 10089.439] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found





```

---

### Post by mreq on 2013-04-13
Seems like the issue is connected with suspending. I do use suspend quite a lot and it'd explain the increasing usage over time.

---

### Post by rollingthunderb on 2013-04-23
I found this thread as I'm experiencing the same thing of sorts. headless torrent box/file server, Xubuntu 64bit 12.04 (old AMD Op 64 2Core w/2GRam, lspci reports ATI X800 VGA) was working fine and smooth for the last 6 months with regular updates, and then I updated to the 3.2.0-40 kernel two weeks ago, and all things went bad. My Samba shares broke. My serviced VNC server failed, and grub seemed to not load the OS without a monitor attached and powered on. This bugged me so much I decided to re-install since I'm not 1337 enough to figure out what happened and revert back. I've since done a re-install this evening. Did all updates, kernel is up to 3.2.0-40, real vnc in serviced mode back up, and now my cpu is idling much higher overall than it used to with xorg being the lead hog. I know this because I had task manger up on my old install all the time and I liked to see how much (or little in this case) memory and cpu it would use with just a vnc session, torrents, file manager, maybe browsing just a bit as well. Now with just TOP running in the terminal I idle at around 11% and when I move my mouse around on a clear desktop cpu will increase to 27%. If I launch the gui task manager that comes with Xubuntu cpu then idles at 47-50%.  I don't use suspend like the person above. 

[IMG]https://www.dropbox.com/s/kdwg3t7c77iyhvk/tskmgr_top1.jpeg[/IMG]

I have another Xbox (much less powerfull file server that's running Xubuntu 12.04 i386 single core 1.5GRam (S3UniCode) VIA compatible VGA)) using the 3.2.0-39 kernel that I won't upgrade because it is even less powerful, and I'm scared the same bad things will happen. 

Back to the AMD dual core box, the cursor in my VNC sessions even feels slugish where it didn't before. The characters that I type while in session aren't as quick either. This is all on local LAN. both boxes on same switch. 

I don't notice any upgrade changes on my other boxes as they are much more powerful and I use them in a local session (not VNC'd).

I can really tell something has drastically changed, but I'm not savvy enough to get you better information without help.
 
Please let me know what I need to do to show what is happening so we can get this fixed.
 
Thank you,

Brian

---

### Post by mreq on 2013-04-24
Try upgrading to final 13.04 tomorrow. I have the beta installed on second partition and it works **much** better. I know I'll dump 12.04 for 13.04 tomorrow ;)

---

### Post by rollingthunderb on 2013-04-24
Thanks for the reply. I may test later, but I went with 12.04 because it is LTS. I'd prefer to get this build back to its old stable self. I'll definitely play with 13.04 in a VM just for fun, but it won't be the same. 

Thank you again for commenting. 

I'm willing to provide logs and do some other testing since this is now a blank box again. At least for a little while. 

Have a great day and thanks for reading.

---

### Post by rollingthunderb on 2013-04-25
Hello, I&#8217;m back.
 
Last night I worked on this some more. On my less powerful i386 box where it was all still working fine and I was waiting to do the recent updates I decided to do all the upgrades except for the 3 updates labeled for XOrg thinking that might have something to do with it. So here I go throwing the 3.2.0-40 kernel on for testing. All went well. CPU runs low and well. So I&#8217;m mistaken thinking it was kernel related. Most of you knew that already I guess.
 
I then went to my dual core box (the one with the problems) and re-installed Xubuntu 12.04 64bit again. Instead of doing the updates during the install, I opted out. Once done I had 401 updates to complete. Out of these 401 I deselected the 3 XOrg updates identified on the other box. This proved nothing other than those updates aren't the problem. CPU utilization was still super high.
 
I updated the remaining 3 updates (all XOrg related) on the i386 box and that didn't change anything for the worse. Box still fine, CPU low and stable.
 
I then went back to the AMD64 box and installed Ubuntu Server 12.04 64bit &#8211; Simple Samba Server and VM host. Then added the XFCE desktop, task manager, bare essentials, etc&#8230;. It was pretty fun I will say. After all the updates I had the 3.5.0-23 generic kernel. All good. Time to add VNC.
 
Added RealVNC 5.0.5, all is good. Able to now see machine remotely. Nothing good has happened though. CPU runs very high. I've noticed that when run local, the CPU idle is very low. When viewing remotely it runs very high.
 
Differences in i386 box and the AMD dual core after recent updates:
 
Behavior
I386 - CPU runs low (7-12%) when viewed remotely.
AMD64 - CPU runs high (50% or more) when viewed remotely
 
VNC
I386 running RealVNC server 5.0.4
AMD64 running RealVNC server 5.0.5
 
[FONT=arial]Video
[/FONT]
[FONT=arial]I386 - 01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
[/FONT][FONT=arial]AMD64 - 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI R420 JK [Radeon X800][/FONT][FONT=arial]
[/FONT]
So tonight I&#8217;ll re-image the AMD64 box again, but this time install RealVNC 5.0.4 to see if there&#8217;s any change in that load.
 
After that I guess I&#8217;ll try 13.4 just for testing. If this isn't VNC related, then there seems to have been a change in how &#8216;buntu is handling my legacy ATI Rage card. As I mentioned previously, this box used to run fine with Xubuntu 12.04. Something has changed in the updates over the last 30-45 days and I wish I knew how to locate it and fix it.
 
I&#8217;ll report back again soon. If you have anything you&#8217;d like me to do to help investigate further while I still have the server on this image, please let me know. I&#8217;d be happy to do it.
 
Thank you for reading.

---

### Post by mreq on 2013-04-29
For me and my sony vaio, the problem is (hopefully) gone after upgrading to 13.04.

---

### Post by rollingthunderb on 2013-04-30
I&#8217;ve gone through both RealVNC 5.0.4 and 5.0.5, and neither version performed better, so that wasn&#8217;t it.
 
I even loaded Xubuntu 12.04 base install with no updates. Still No difference. I then went to Xubuntu 13.04. Much better.
 
All of this work reminded me of the trouble I had getting 12.04 on the box way back when I initially set the box up last year. Just to get the box to install again, I had to invoke NOMODESET.
 
Clearly I did something more than nomodeset if not several things to get the install to be happy with the video card last year. Unfortunately I can&#8217;t remember everything I did to get my desktop happy. Sure wish I would have written it down. Lesson learned there. The positive side effect from whatever I did made the CPU utilization low. It ran for close to a year with updates and nothing ever went wrong until one of the recent packs of updates broke whatever I had in place. Oh well.
 
This weekend will bring us Debian 7.0 &#8211; that should be fun to try. Maybe I&#8217;ll use that with an XFCE DE as my server from now on. That&#8217;ll depend on how good it is.
 
Thanks for reading. Wish someone had some pointers on what to do with 12.04. I guess I&#8217;ll dig around the internet some more for solutions.
 
Since 13.04 handles it much better, I guess I&#8217;ll consider this closed so to speak.
 
Xubuntu 13.04 is a lot snappier. I really like the newer XFCE desktop. Unfortunately it is only supported for 9 months now. Does anyone know if the changes made in 13.04 will be back-ported into 12.04 LTS at some point? If so, when?
 
Have a great day.

---

### Post by mreq on 2013-04-30
If it's XFCE we're talking about, you can install the latest stable (4.10) via a ppa - [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10).

I found out that Xorg usage was high because of stuck exo-helpers, more in [this topic]("http://ubuntuforums.org/showthread.php?t=2139592&p=12624754#post12624754").

---

