---
title: "nouveau drivers not loding, vesa ones are"
date: 2012-09-23
forum: Desktop Environments
---

### Post by jakebriggs on 2012-09-23
Hi All

So I upgraded to latest ubuntu (12.04) about 2 months ago, and after the upgrade I was only able to get 1024x768 resolution on the desktop. I have a geforce4 mx440 (nv17)

I played around with it for ages, trying the nvidia drivers and the nouveau drivers and the only thing I could get to work was the vesa drivers - stuck at 1024x768.

Now, I gather that the binary nvidia drivers I need to use on my card are too old to work with unity (nvidia-175 I think) and I couldn't make them work anyway. I'd liek to use the nouveau drivers but I can't get them working either - I have them installed but I get his in the Xorg.0.log:

```

[ 76576.539] drmOpenDevice: node name is /dev/dri/card0
[ 76576.612] [drm] failed to load kernel module "nouveau"
[ 76576.612] (EE) [drm] failed to open device
[ 76576.612] drmOpenDevice: node name is /dev/dri/card0
[ 76576.625] [drm] failed to load kernel module "nouveau"
[ 76576.625] (EE) [drm] failed to open device
[ 76576.625] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

```

and it falls back to vesa. I have no /etc/X11/xorg.conf

If I could make vesa do 1360x768 then maybe I would be cool with that - as long as I could watch youtube vids or whatever - light desktop usage. But nouveau would be nice.

Here is the full Xorg.0.log:

```

[ 76576.187] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[ 76576.187] X Protocol Version 11, Revision 0
[ 76576.187] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[ 76576.187] Current Operating System: Linux beastie 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:54:40 UTC 2012 i686
[ 76576.187] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-30-generic root=UUID=2679dccb-7465-45df-b862-9ca3ff989c40 ro plymouth:debug drm.debug=0xe noacpi=1 acpi=off
[ 76576.187] Build Date: 04 August 2012  01:51:24AM
[ 76576.187] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[ 76576.187] Current version of pixman: 0.24.4
[ 76576.187]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[ 76576.187] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 76576.188] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 24 14:47:27 2012
[ 76576.188] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 76576.235] (==) No Layout section.  Using the first Screen section.
[ 76576.235] (==) No screen section available. Using defaults.
[ 76576.235] (**) |-->Screen "Default Screen Section" (0)
[ 76576.235] (**) |   |-->Monitor "<default monitor>"
[ 76576.236] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[ 76576.236] (==) Automatically adding devices
[ 76576.236] (==) Automatically enabling devices
[ 76576.251] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 76576.251]     Entry deleted from font path.
[ 76576.269] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[ 76576.269] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 76576.269] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 76576.269] (II) Loader magic: 0x6ed5a0
[ 76576.269] (II) Module ABI versions:
[ 76576.269]     X.Org ANSI C Emulation: 0.4
[ 76576.269]     X.Org Video Driver: 11.0
[ 76576.269]     X.Org XInput driver : 16.0
[ 76576.269]     X.Org Server Extension : 6.0
[ 76576.270] (--) PCI:*(0:1:0:0) 10de:0171:1043:808b rev 163, Mem @ 0xfc000000/16777216, 0xe0000000/134217728, 0xe8000000/524288, BIOS @ 0x????????/131072
[ 76576.271] (II) Open ACPI successful (/var/run/acpid.socket)
[ 76576.271] (II) LoadModule: "extmod"
[ 76576.272] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 76576.272] (II) Module extmod: vendor="X.Org Foundation"
[ 76576.272]     compiled for 1.11.3, module version = 1.0.0
[ 76576.272]     Module class: X.Org Server Extension
[ 76576.272]     ABI class: X.Org Server Extension, version 6.0
[ 76576.272] (II) Loading extension MIT-SCREEN-SAVER
[ 76576.272] (II) Loading extension XFree86-VidModeExtension
[ 76576.272] (II) Loading extension XFree86-DGA
[ 76576.272] (II) Loading extension DPMS
[ 76576.272] (II) Loading extension XVideo
[ 76576.272] (II) Loading extension XVideo-MotionCompensation
[ 76576.272] (II) Loading extension X-Resource
[ 76576.272] (II) LoadModule: "dbe"
[ 76576.273] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 76576.283] (II) Module dbe: vendor="X.Org Foundation"
[ 76576.283]     compiled for 1.11.3, module version = 1.0.0
[ 76576.284]     Module class: X.Org Server Extension
[ 76576.284]     ABI class: X.Org Server Extension, version 6.0
[ 76576.284] (II) Loading extension DOUBLE-BUFFER
[ 76576.284] (II) LoadModule: "glx"
[ 76576.284] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 76576.304] (II) Module glx: vendor="X.Org Foundation"
[ 76576.304]     compiled for 1.11.3, module version = 1.0.0
[ 76576.304]     ABI class: X.Org Server Extension, version 6.0
[ 76576.304] (==) AIGLX enabled
[ 76576.304] (II) Loading extension GLX
[ 76576.304] (II) LoadModule: "record"
[ 76576.305] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 76576.305] (II) Module record: vendor="X.Org Foundation"
[ 76576.305]     compiled for 1.11.3, module version = 1.13.0
[ 76576.305]     Module class: X.Org Server Extension
[ 76576.305]     ABI class: X.Org Server Extension, version 6.0
[ 76576.305] (II) Loading extension RECORD
[ 76576.305] (II) LoadModule: "dri"
[ 76576.305] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 76576.387] (II) Module dri: vendor="X.Org Foundation"
[ 76576.387]     compiled for 1.11.3, module version = 1.0.0
[ 76576.387]     ABI class: X.Org Server Extension, version 6.0
[ 76576.387] (II) Loading extension XFree86-DRI
[ 76576.387] (II) LoadModule: "dri2"
[ 76576.387] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 76576.389] (II) Module dri2: vendor="X.Org Foundation"
[ 76576.389]     compiled for 1.11.3, module version = 1.2.0
[ 76576.389]     ABI class: X.Org Server Extension, version 6.0
[ 76576.389] (II) Loading extension DRI2
[ 76576.389] (==) Matched nvidia as autoconfigured driver 0
[ 76576.389] (==) Matched nouveau as autoconfigured driver 1
[ 76576.389] (==) Matched nv as autoconfigured driver 2
[ 76576.389] (==) Matched vesa as autoconfigured driver 3
[ 76576.389] (==) Matched fbdev as autoconfigured driver 4
[ 76576.389] (==) Assigned the driver to the xf86ConfigLayout
[ 76576.389] (II) LoadModule: "nvidia"
[ 76576.390] (WW) Warning, couldn't open module nvidia
[ 76576.390] (II) UnloadModule: "nvidia"
[ 76576.390] (II) Unloading nvidia
[ 76576.390] (EE) Failed to load module "nvidia" (module does not exist, 0)
[ 76576.390] (II) LoadModule: "nouveau"
[ 76576.390] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 76576.482] (II) Module nouveau: vendor="X.Org Foundation"
[ 76576.482]     compiled for 1.11.3, module version = 0.0.16
[ 76576.482]     Module class: X.Org Video Driver
[ 76576.482]     ABI class: X.Org Video Driver, version 11.0
[ 76576.482] (II) LoadModule: "nv"
[ 76576.482] (WW) Warning, couldn't open module nv
[ 76576.483] (II) UnloadModule: "nv"
[ 76576.483] (II) Unloading nv
[ 76576.483] (EE) Failed to load module "nv" (module does not exist, 0)
[ 76576.483] (II) LoadModule: "vesa"
[ 76576.483] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 76576.518] (II) Module vesa: vendor="X.Org Foundation"
[ 76576.518]     compiled for 1.11.3, module version = 2.3.0
[ 76576.518]     Module class: X.Org Video Driver
[ 76576.518]     ABI class: X.Org Video Driver, version 11.0
[ 76576.518] (II) LoadModule: "fbdev"
[ 76576.519] (WW) Warning, couldn't open module fbdev
[ 76576.519] (II) UnloadModule: "fbdev"
[ 76576.519] (II) Unloading fbdev
[ 76576.519] (EE) Failed to load module "fbdev" (module does not exist, 0)
[ 76576.519] (==) Matched nvidia as autoconfigured driver 0
[ 76576.519] (==) Matched nouveau as autoconfigured driver 1
[ 76576.519] (==) Matched nv as autoconfigured driver 2
[ 76576.519] (==) Matched vesa as autoconfigured driver 3
[ 76576.519] (==) Matched fbdev as autoconfigured driver 4
[ 76576.519] (==) Assigned the driver to the xf86ConfigLayout
[ 76576.519] (II) LoadModule: "nvidia"
[ 76576.520] (WW) Warning, couldn't open module nvidia
[ 76576.520] (II) UnloadModule: "nvidia"
[ 76576.520] (II) Unloading nvidia
[ 76576.520] (EE) Failed to load module "nvidia" (module does not exist, 0)
[ 76576.520] (II) LoadModule: "nouveau"
[ 76576.520] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 76576.520] (II) Module nouveau: vendor="X.Org Foundation"
[ 76576.520]     compiled for 1.11.3, module version = 0.0.16
[ 76576.520]     Module class: X.Org Video Driver
[ 76576.520]     ABI class: X.Org Video Driver, version 11.0
[ 76576.520] (II) UnloadModule: "nouveau"
[ 76576.520] (II) Unloading nouveau
[ 76576.520] (II) Failed to load module "nouveau" (already loaded, 0)
[ 76576.520] (II) LoadModule: "nv"
[ 76576.521] (WW) Warning, couldn't open module nv
[ 76576.521] (II) UnloadModule: "nv"
[ 76576.521] (II) Unloading nv
[ 76576.521] (EE) Failed to load module "nv" (module does not exist, 0)
[ 76576.521] (II) LoadModule: "vesa"
[ 76576.521] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 76576.521] (II) Module vesa: vendor="X.Org Foundation"
[ 76576.521]     compiled for 1.11.3, module version = 2.3.0
[ 76576.521]     Module class: X.Org Video Driver
[ 76576.521]     ABI class: X.Org Video Driver, version 11.0
[ 76576.521] (II) UnloadModule: "vesa"
[ 76576.521] (II) Unloading vesa
[ 76576.521] (II) Failed to load module "vesa" (already loaded, 0)
[ 76576.521] (II) LoadModule: "fbdev"
[ 76576.522] (WW) Warning, couldn't open module fbdev
[ 76576.522] (II) UnloadModule: "fbdev"
[ 76576.522] (II) Unloading fbdev
[ 76576.522] (EE) Failed to load module "fbdev" (module does not exist, 0)
[ 76576.522] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[ 76576.522] (II) NOUVEAU driver for NVIDIA chipset families :
[ 76576.522]     RIVA TNT        (NV04)
[ 76576.522]     RIVA TNT2       (NV05)
[ 76576.522]     GeForce 256     (NV10)
[ 76576.522]     GeForce 2       (NV11, NV15)
[ 76576.522]     GeForce 4MX     (NV17, NV18)
[ 76576.523]     GeForce 3       (NV20)
[ 76576.523]     GeForce 4Ti     (NV25, NV28)
[ 76576.523]     GeForce FX      (NV3x)
[ 76576.523]     GeForce 6       (NV4x)
[ 76576.523]     GeForce 7       (G7x)
[ 76576.523]     GeForce 8       (G8x)
[ 76576.523]     GeForce GTX 200 (NVA0)
[ 76576.523]     GeForce GTX 400 (NVC0)
[ 76576.523] (II) VESA: driver for VESA chipsets: vesa
[ 76576.523] (--) using VT number 8

[ 76576.539] drmOpenDevice: node name is /dev/dri/card0
[ 76576.612] [drm] failed to load kernel module "nouveau"
[ 76576.612] (EE) [drm] failed to open device
[ 76576.612] drmOpenDevice: node name is /dev/dri/card0
[ 76576.625] [drm] failed to load kernel module "nouveau"
[ 76576.625] (EE) [drm] failed to open device
[ 76576.625] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 76576.626] (II) Loading sub module "vbe"
[ 76576.626] (II) LoadModule: "vbe"
[ 76576.626] (II) Loading /usr/lib/xorg/modules/libvbe.so
[ 76576.656] (II) Module vbe: vendor="X.Org Foundation"
[ 76576.656]     compiled for 1.11.3, module version = 1.1.0
[ 76576.656]     ABI class: X.Org Video Driver, version 11.0
[ 76576.656] (II) Loading sub module "int10"
[ 76576.656] (II) LoadModule: "int10"
[ 76576.656] (II) Loading /usr/lib/xorg/modules/libint10.so
[ 76576.690] (II) Module int10: vendor="X.Org Foundation"
[ 76576.690]     compiled for 1.11.3, module version = 1.0.0
[ 76576.690]     ABI class: X.Org Video Driver, version 11.0
[ 76576.690] (II) VESA(0): initializing int10
[ 76576.707] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[ 76576.771] (II) VESA(0): VESA BIOS detected
[ 76576.771] (II) VESA(0): VESA VBE Version 3.0
[ 76576.771] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[ 76576.771] (II) VESA(0): VESA VBE OEM: NVIDIA
[ 76576.771] (II) VESA(0): VESA VBE OEM Software Rev: 4.23
[ 76576.771] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[ 76576.771] (II) VESA(0): VESA VBE OEM Product: NV17 Board
[ 76576.771] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A5
[ 76577.005] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[ 76577.005] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[ 76577.005] (==) VESA(0): RGB weight 888
[ 76577.005] (==) VESA(0): Default visual is TrueColor
[ 76577.005] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 76577.005] (II) Loading sub module "ddc"
[ 76577.005] (II) LoadModule: "ddc"
[ 76577.005] (II) Module "ddc" already built-in
[ 76577.194] (II) VESA(0): VESA VBE DDC supported
[ 76577.194] (II) VESA(0): VESA VBE DDC Level 2
[ 76577.194] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[ 76577.696] (II) VESA(0): VESA VBE DDC read successfully
[ 76577.696] (II) VESA(0): Manufacturer: AOC  Model: 1936  Serial#: 2538
[ 76577.696] (II) VESA(0): Year: 2011  Week: 14
[ 76577.696] (II) VESA(0): EDID Version: 1.3
[ 76577.696] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[ 76577.697] (II) VESA(0): Sync:  Separate
[ 76577.697] (II) VESA(0): Max Image Size [cm]: horiz.: 41  vert.: 23
[ 76577.697] (II) VESA(0): Gamma: 2.20
[ 76577.697] (II) VESA(0): DPMS capabilities: Off; RGB/Color Display
[ 76577.697] (II) VESA(0): First detailed timing is preferred mode
[ 76577.697] (II) VESA(0): redX: 0.647 redY: 0.334   greenX: 0.284 greenY: 0.607
[ 76577.697] (II) VESA(0): blueX: 0.151 blueY: 0.071   whiteX: 0.312 whiteY: 0.329
[ 76577.697] (II) VESA(0): Supported established timings:
[ 76577.697] (II) VESA(0): 720x400@70Hz
[ 76577.697] (II) VESA(0): 640x480@60Hz
[ 76577.697] (II) VESA(0): 640x480@67Hz
[ 76577.697] (II) VESA(0): 640x480@72Hz
[ 76577.697] (II) VESA(0): 640x480@75Hz
[ 76577.697] (II) VESA(0): 800x600@56Hz
[ 76577.697] (II) VESA(0): 800x600@60Hz
[ 76577.697] (II) VESA(0): 800x600@72Hz
[ 76577.697] (II) VESA(0): 800x600@75Hz
[ 76577.697] (II) VESA(0): 832x624@75Hz
[ 76577.697] (II) VESA(0): 1024x768@60Hz
[ 76577.697] (II) VESA(0): 1024x768@70Hz
[ 76577.697] (II) VESA(0): 1024x768@75Hz
[ 76577.697] (II) VESA(0): Manufacturer's mask: 0
[ 76577.697] (II) VESA(0): Supported standard timings:
[ 76577.697] (II) VESA(0): #0: hsize: 640  vsize 400  refresh: 70  vid: 2609
[ 76577.697] (II) VESA(0): #1: hsize: 1024  vsize 768  refresh: 72  vid: 19553
[ 76577.697] (II) VESA(0): Supported detailed timing:
[ 76577.697] (II) VESA(0): clock: 85.5 MHz   Image Size:  410 x 230 mm
[ 76577.697] (II) VESA(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[ 76577.697] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[ 76577.697] (II) VESA(0): Supported detailed timing:
[ 76577.697] (II) VESA(0): clock: 85.5 MHz   Image Size:  410 x 230 mm
[ 76577.697] (II) VESA(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[ 76577.697] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[ 76577.697] (II) VESA(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 95 MHz
[ 76577.697] (II) VESA(0): Monitor name: 936W
[ 76577.697] (II) VESA(0): EDID (in hex):
[ 76577.698] (II) VESA(0):     00ffffffffffff0005e33619ea090000
[ 76577.698] (II) VESA(0):     0e150103682917782aeed1a555489b26
[ 76577.698] (II) VESA(0):     125054bfee00310a614c010101010101
[ 76577.698] (II) VESA(0):     010101010101662156aa51001e30468f
[ 76577.698] (II) VESA(0):     33009ae61000001e662150b051001b30
[ 76577.698] (II) VESA(0):     407036009ae61000001e000000fd0037
[ 76577.698] (II) VESA(0):     4b1e5109000a202020202020000000fc
[ 76577.698] (II) VESA(0):     00393336570a202020202020202000ff
[ 76577.698] (II) VESA(0): EDID vendor "AOC", prod id 6454
[ 76577.698] (II) VESA(0): Using EDID range info for horizontal sync
[ 76577.698] (II) VESA(0): Using EDID range info for vertical refresh
[ 76577.698] (II) VESA(0): Printing DDC gathered Modelines:
[ 76577.698] (II) VESA(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz)
[ 76577.698] (II) VESA(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[ 76577.698] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 76577.698] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 76577.698] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 76577.698] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[ 76577.698] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[ 76577.698] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 76577.698] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[ 76577.698] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[ 76577.698] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[ 76577.698] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 76577.698] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[ 76577.698] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[ 76577.698] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[ 76577.698] (II) VESA(0): Modeline "640x400"x70.0   23.35  640 656 720 800  400 401 404 417 -hsync +vsync (29.2 kHz)
[ 76577.698] (II) VESA(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[ 76577.698] (II) VESA(0): Searching for matching VESA mode(s):
[ 76577.708] Mode: 100 (640x400)
[ 76577.708]     ModeAttributes: 0x39f
[ 76577.708]     WinAAttributes: 0x7
[ 76577.708]     WinBAttributes: 0x0
[ 76577.708]     WinGranularity: 64
[ 76577.708]     WinSize: 64
[ 76577.709]     WinASegment: 0xa000
[ 76577.709]     WinBSegment: 0x0
[ 76577.709]     WinFuncPtr: 0xc000ada2
[ 76577.709]     BytesPerScanline: 640
[ 76577.709]     XResolution: 640
[ 76577.709]     YResolution: 400
[ 76577.709]     XCharSize: 8
[ 76577.709]     YCharSize: 16
[ 76577.709]     NumberOfPlanes: 1
[ 76577.709]     BitsPerPixel: 8
[ 76577.709]     NumberOfBanks: 1
[ 76577.709]     MemoryModel: 4
[ 76577.709]     BankSize: 0
[ 76577.709]     NumberOfImages: 14
[ 76577.709]     RedMaskSize: 0
[ 76577.709]     RedFieldPosition: 0
[ 76577.709]     GreenMaskSize: 0
[ 76577.709]     GreenFieldPosition: 0
[ 76577.709]     BlueMaskSize: 0
[ 76577.709]     BlueFieldPosition: 0
[ 76577.709]     RsvdMaskSize: 0
[ 76577.709]     RsvdFieldPosition: 0
[ 76577.709]     DirectColorModeInfo: 0
[ 76577.709]     PhysBasePtr: 0xe0000000
[ 76577.709]     LinBytesPerScanLine: 640
[ 76577.709]     BnkNumberOfImagePages: 14
[ 76577.709]     LinNumberOfImagePages: 14
[ 76577.709]     LinRedMaskSize: 0
[ 76577.709]     LinRedFieldPosition: 0
[ 76577.709]     LinGreenMaskSize: 0
[ 76577.709]     LinGreenFieldPosition: 0
[ 76577.709]     LinBlueMaskSize: 0
[ 76577.709]     LinBlueFieldPosition: 0
[ 76577.709]     LinRsvdMaskSize: 0
[ 76577.709]     LinRsvdFieldPosition: 0
[ 76577.709]     MaxPixelClock: 229500000
[ 76577.711] Mode: 101 (640x480)
[ 76577.711]     ModeAttributes: 0x39f
[ 76577.711]     WinAAttributes: 0x7
[ 76577.716]     WinBAttributes: 0x0
[ 76577.716]     WinGranularity: 64
[ 76577.716]     WinSize: 64
[ 76577.716]     WinASegment: 0xa000
[ 76577.716]     WinBSegment: 0x0
[ 76577.716]     WinFuncPtr: 0xc000ada2
[ 76577.716]     BytesPerScanline: 640
[ 76577.716]     XResolution: 640
[ 76577.716]     YResolution: 480
[ 76577.716]     XCharSize: 8
[ 76577.716]     YCharSize: 16
[ 76577.716]     NumberOfPlanes: 1
[ 76577.716]     BitsPerPixel: 8
[ 76577.716]     NumberOfBanks: 1
[ 76577.716]     MemoryModel: 4
[ 76577.716]     BankSize: 0
[ 76577.716]     NumberOfImages: 10
[ 76577.716]     RedMaskSize: 0
[ 76577.716]     RedFieldPosition: 0
[ 76577.716]     GreenMaskSize: 0
[ 76577.716]     GreenFieldPosition: 0
[ 76577.716]     BlueMaskSize: 0
[ 76577.716]     BlueFieldPosition: 0
[ 76577.716]     RsvdMaskSize: 0
[ 76577.716]     RsvdFieldPosition: 0
[ 76577.716]     DirectColorModeInfo: 0
[ 76577.716]     PhysBasePtr: 0xe0000000
[ 76577.716]     LinBytesPerScanLine: 640
[ 76577.716]     BnkNumberOfImagePages: 10
[ 76577.716]     LinNumberOfImagePages: 10
[ 76577.716]     LinRedMaskSize: 0
[ 76577.716]     LinRedFieldPosition: 0
[ 76577.716]     LinGreenMaskSize: 0
[ 76577.716]     LinGreenFieldPosition: 0
[ 76577.716]     LinBlueMaskSize: 0
[ 76577.716]     LinBlueFieldPosition: 0
[ 76577.716]     LinRsvdMaskSize: 0
[ 76577.716]     LinRsvdFieldPosition: 0
[ 76577.716]     MaxPixelClock: 229500000
[ 76577.718] Mode: 102 (800x600)
[ 76577.718]     ModeAttributes: 0x31f
[ 76577.718]     WinAAttributes: 0x7
[ 76577.718]     WinBAttributes: 0x0
[ 76577.718]     WinGranularity: 64
[ 76577.718]     WinSize: 64
[ 76577.718]     WinASegment: 0xa000
[ 76577.718]     WinBSegment: 0x0
[ 76577.718]     WinFuncPtr: 0xc000ada2
[ 76577.718]     BytesPerScanline: 100
[ 76577.718]     XResolution: 800
[ 76577.718]     YResolution: 600
[ 76577.718]     XCharSize: 8
[ 76577.718]     YCharSize: 16
[ 76577.718]     NumberOfPlanes: 4
[ 76577.718]     BitsPerPixel: 4
[ 76577.718]     NumberOfBanks: 1
[ 76577.718]     MemoryModel: 3
[ 76577.718]     BankSize: 0
[ 76577.718]     NumberOfImages: 14
[ 76577.718]     RedMaskSize: 0
[ 76577.718]     RedFieldPosition: 0
[ 76577.718]     GreenMaskSize: 0
[ 76577.718]     GreenFieldPosition: 0
[ 76577.718]     BlueMaskSize: 0
[ 76577.718]     BlueFieldPosition: 0
[ 76577.718]     RsvdMaskSize: 0
[ 76577.718]     RsvdFieldPosition: 0
[ 76577.718]     DirectColorModeInfo: 0
[ 76577.718]     PhysBasePtr: 0x0
[ 76577.718]     LinBytesPerScanLine: 100
[ 76577.718]     BnkNumberOfImagePages: 14
[ 76577.718]     LinNumberOfImagePages: 14
[ 76577.718]     LinRedMaskSize: 0
[ 76577.719]     LinRedFieldPosition: 0
[ 76577.719]     LinGreenMaskSize: 0
[ 76577.719]     LinGreenFieldPosition: 0
[ 76577.719]     LinBlueMaskSize: 0
[ 76577.719]     LinBlueFieldPosition: 0
[ 76577.719]     LinRsvdMaskSize: 0
[ 76577.719]     LinRsvdFieldPosition: 0
[ 76577.719]     MaxPixelClock: 108500000
[ 76577.727] Mode: 103 (800x600)
[ 76577.727]     ModeAttributes: 0x39f
[ 76577.727]     WinAAttributes: 0x7
[ 76577.727]     WinBAttributes: 0x0
[ 76577.727]     WinGranularity: 64
[ 76577.727]     WinSize: 64
[ 76577.727]     WinASegment: 0xa000
[ 76577.727]     WinBSegment: 0x0
[ 76577.727]     WinFuncPtr: 0xc000ada2
[ 76577.728]     BytesPerScanline: 800
[ 76577.728]     XResolution: 800
[ 76577.728]     YResolution: 600
[ 76577.728]     XCharSize: 8
[ 76577.728]     YCharSize: 16
[ 76577.728]     NumberOfPlanes: 1
[ 76577.728]     BitsPerPixel: 8
[ 76577.728]     NumberOfBanks: 1
[ 76577.728]     MemoryModel: 4
[ 76577.728]     BankSize: 0
[ 76577.728]     NumberOfImages: 6
[ 76577.728]     RedMaskSize: 0
[ 76577.728]     RedFieldPosition: 0
[ 76577.728]     GreenMaskSize: 0
[ 76577.728]     GreenFieldPosition: 0
[ 76577.728]     BlueMaskSize: 0
[ 76577.728]     BlueFieldPosition: 0
[ 76577.728]     RsvdMaskSize: 0
[ 76577.728]     RsvdFieldPosition: 0
[ 76577.728]     DirectColorModeInfo: 0
[ 76577.728]     PhysBasePtr: 0xe0000000
[ 76577.728]     LinBytesPerScanLine: 800
[ 76577.728]     BnkNumberOfImagePages: 6
[ 76577.728]     LinNumberOfImagePages: 6
[ 76577.728]     LinRedMaskSize: 0
[ 76577.728]     LinRedFieldPosition: 0
[ 76577.728]     LinGreenMaskSize: 0
[ 76577.728]     LinGreenFieldPosition: 0
[ 76577.728]     LinBlueMaskSize: 0
[ 76577.728]     LinBlueFieldPosition: 0
[ 76577.728]     LinRsvdMaskSize: 0
[ 76577.728]     LinRsvdFieldPosition: 0
[ 76577.728]     MaxPixelClock: 229500000
[ 76577.730] Mode: 104 (1024x768)
[ 76577.730]     ModeAttributes: 0x31f
[ 76577.730]     WinAAttributes: 0x7
[ 76577.730]     WinBAttributes: 0x0
[ 76577.730]     WinGranularity: 64
[ 76577.730]     WinSize: 64
[ 76577.730]     WinASegment: 0xa000
[ 76577.730]     WinBSegment: 0x0
[ 76577.730]     WinFuncPtr: 0xc000ada2
[ 76577.730]     BytesPerScanline: 128
[ 76577.730]     XResolution: 1024
[ 76577.730]     YResolution: 768
[ 76577.730]     XCharSize: 8
[ 76577.730]     YCharSize: 16
[ 76577.730]     NumberOfPlanes: 4
[ 76577.730]     BitsPerPixel: 4
[ 76577.730]     NumberOfBanks: 1
[ 76577.730]     MemoryModel: 3
[ 76577.730]     BankSize: 0
[ 76577.730]     NumberOfImages: 6
[ 76577.730]     RedMaskSize: 0
[ 76577.730]     RedFieldPosition: 0
[ 76577.730]     GreenMaskSize: 0
[ 76577.730]     GreenFieldPosition: 0
[ 76577.730]     BlueMaskSize: 0
[ 76577.730]     BlueFieldPosition: 0
[ 76577.730]     RsvdMaskSize: 0
[ 76577.730]     RsvdFieldPosition: 0
[ 76577.730]     DirectColorModeInfo: 0
[ 76577.730]     PhysBasePtr: 0x0
[ 76577.730]     LinBytesPerScanLine: 128
[ 76577.730]     BnkNumberOfImagePages: 6
[ 76577.730]     LinNumberOfImagePages: 6
[ 76577.730]     LinRedMaskSize: 0
[ 76577.730]     LinRedFieldPosition: 0
[ 76577.730]     LinGreenMaskSize: 0
[ 76577.730]     LinGreenFieldPosition: 0
[ 76577.730]     LinBlueMaskSize: 0
[ 76577.730]     LinBlueFieldPosition: 0
[ 76577.730]     LinRsvdMaskSize: 0
[ 76577.730]     LinRsvdFieldPosition: 0
[ 76577.730]     MaxPixelClock: 108500000
[ 76577.740] Mode: 105 (1024x768)
[ 76577.740]     ModeAttributes: 0x39f
[ 76577.740]     WinAAttributes: 0x7
[ 76577.741]     WinBAttributes: 0x0
[ 76577.741]     WinGranularity: 64
[ 76577.741]     WinSize: 64
[ 76577.741]     WinASegment: 0xa000
[ 76577.741]     WinBSegment: 0x0
[ 76577.741]     WinFuncPtr: 0xc000ada2
[ 76577.741]     BytesPerScanline: 1024
[ 76577.741]     XResolution: 1024
[ 76577.741]     YResolution: 768
[ 76577.741]     XCharSize: 8
[ 76577.741]     YCharSize: 16
[ 76577.741]     NumberOfPlanes: 1
[ 76577.741]     BitsPerPixel: 8
[ 76577.741]     NumberOfBanks: 1
[ 76577.741]     MemoryModel: 4
[ 76577.741]     BankSize: 0
[ 76577.741]     NumberOfImages: 3
[ 76577.741]     RedMaskSize: 0
[ 76577.741]     RedFieldPosition: 0
[ 76577.741]     GreenMaskSize: 0
[ 76577.741]     GreenFieldPosition: 0
[ 76577.741]     BlueMaskSize: 0
[ 76577.741]     BlueFieldPosition: 0
[ 76577.741]     RsvdMaskSize: 0
[ 76577.741]     RsvdFieldPosition: 0
[ 76577.741]     DirectColorModeInfo: 0
[ 76577.741]     PhysBasePtr: 0xe0000000
[ 76577.741]     LinBytesPerScanLine: 1024
[ 76577.741]     BnkNumberOfImagePages: 3
[ 76577.741]     LinNumberOfImagePages: 3
[ 76577.741]     LinRedMaskSize: 0
[ 76577.741]     LinRedFieldPosition: 0
[ 76577.741]     LinGreenMaskSize: 0
[ 76577.741]     LinGreenFieldPosition: 0
[ 76577.741]     LinBlueMaskSize: 0
[ 76577.741]     LinBlueFieldPosition: 0
[ 76577.741]     LinRsvdMaskSize: 0
[ 76577.741]     LinRsvdFieldPosition: 0
[ 76577.741]     MaxPixelClock: 229500000
[ 76577.743] Mode: 106 (1280x1024)
[ 76577.743]     ModeAttributes: 0x31f
[ 76577.744]     WinAAttributes: 0x7
[ 76577.745]     WinBAttributes: 0x0
[ 76577.745]     WinGranularity: 64
[ 76577.745]     WinSize: 64
[ 76577.745]     WinASegment: 0xa000
[ 76577.745]     WinBSegment: 0x0
[ 76577.745]     WinFuncPtr: 0xc000ada2
[ 76577.745]     BytesPerScanline: 160
[ 76577.745]     XResolution: 1280
[ 76577.745]     YResolution: 1024
[ 76577.745]     XCharSize: 8
[ 76577.745]     YCharSize: 16
[ 76577.745]     NumberOfPlanes: 4
[ 76577.745]     BitsPerPixel: 4
[ 76577.745]     NumberOfBanks: 1
[ 76577.745]     MemoryModel: 3
[ 76577.745]     BankSize: 0
[ 76577.745]     NumberOfImages: 3
[ 76577.745]     RedMaskSize: 0
[ 76577.745]     RedFieldPosition: 0
[ 76577.745]     GreenMaskSize: 0
[ 76577.745]     GreenFieldPosition: 0
[ 76577.745]     BlueMaskSize: 0
[ 76577.745]     BlueFieldPosition: 0
[ 76577.745]     RsvdMaskSize: 0
[ 76577.745]     RsvdFieldPosition: 0
[ 76577.745]     DirectColorModeInfo: 0
[ 76577.745]     PhysBasePtr: 0x0
[ 76577.745]     LinBytesPerScanLine: 160
[ 76577.745]     BnkNumberOfImagePages: 3
[ 76577.745]     LinNumberOfImagePages: 3
[ 76577.745]     LinRedMaskSize: 0
[ 76577.745]     LinRedFieldPosition: 0
[ 76577.745]     LinGreenMaskSize: 0
[ 76577.745]     LinGreenFieldPosition: 0
[ 76577.745]     LinBlueMaskSize: 0
[ 76577.745]     LinBlueFieldPosition: 0
[ 76577.745]     LinRsvdMaskSize: 0
[ 76577.745]     LinRsvdFieldPosition: 0
[ 76577.745]     MaxPixelClock: 108500000
[ 76577.747] Mode: 107 (1280x1024)
[ 76577.747]     ModeAttributes: 0x39f
[ 76577.747]     WinAAttributes: 0x7
[ 76577.747]     WinBAttributes: 0x0
[ 76577.747]     WinGranularity: 64
[ 76577.747]     WinSize: 64
[ 76577.747]     WinASegment: 0xa000
[ 76577.747]     WinBSegment: 0x0
[ 76577.747]     WinFuncPtr: 0xc000ada2
[ 76577.747]     BytesPerScanline: 1280
[ 76577.747]     XResolution: 1280
[ 76577.747]     YResolution: 1024
[ 76577.747]     XCharSize: 8
[ 76577.747]     YCharSize: 16
[ 76577.747]     NumberOfPlanes: 1
[ 76577.747]     BitsPerPixel: 8
[ 76577.747]     NumberOfBanks: 1
[ 76577.747]     MemoryModel: 4
[ 76577.747]     BankSize: 0
[ 76577.747]     NumberOfImages: 1
[ 76577.747]     RedMaskSize: 0
[ 76577.747]     RedFieldPosition: 0
[ 76577.747]     GreenMaskSize: 0
[ 76577.747]     GreenFieldPosition: 0
[ 76577.747]     BlueMaskSize: 0
[ 76577.747]     BlueFieldPosition: 0
[ 76577.753]     RsvdMaskSize: 0
[ 76577.753]     RsvdFieldPosition: 0
[ 76577.753]     DirectColorModeInfo: 0
[ 76577.753]     PhysBasePtr: 0xe0000000
[ 76577.753]     LinBytesPerScanLine: 1280
[ 76577.753]     BnkNumberOfImagePages: 1
[ 76577.753]     LinNumberOfImagePages: 1
[ 76577.753]     LinRedMaskSize: 0
[ 76577.753]     LinRedFieldPosition: 0
[ 76577.753]     LinGreenMaskSize: 0
[ 76577.753]     LinGreenFieldPosition: 0
[ 76577.753]     LinBlueMaskSize: 0
[ 76577.753]     LinBlueFieldPosition: 0
[ 76577.753]     LinRsvdMaskSize: 0
[ 76577.753]     LinRsvdFieldPosition: 0
[ 76577.753]     MaxPixelClock: 229500000
[ 76577.760] Mode: 108 (80x60)
[ 76577.760]     ModeAttributes: 0x38f
[ 76577.760]     WinAAttributes: 0x7
[ 76577.760]     WinBAttributes: 0x0
[ 76577.760]     WinGranularity: 32
[ 76577.760]     WinSize: 32
[ 76577.760]     WinASegment: 0xb800
[ 76577.760]     WinBSegment: 0x0
[ 76577.760]     WinFuncPtr: 0xc000ada2
[ 76577.760]     BytesPerScanline: 160
[ 76577.760]     XResolution: 80
[ 76577.760]     YResolution: 60
[ 76577.760]     XCharSize: 8
[ 76577.760]     YCharSize: 8
[ 76577.760]     NumberOfPlanes: 1
[ 76577.760]     BitsPerPixel: 4
[ 76577.760]     NumberOfBanks: 1
[ 76577.760]     MemoryModel: 0
[ 76577.760]     BankSize: 0
[ 76577.760]     NumberOfImages: 0
[ 76577.760]     RedMaskSize: 0
[ 76577.760]     RedFieldPosition: 0
[ 76577.760]     GreenMaskSize: 0
[ 76577.760]     GreenFieldPosition: 0
[ 76577.760]     BlueMaskSize: 0
[ 76577.760]     BlueFieldPosition: 0
[ 76577.760]     RsvdMaskSize: 0
[ 76577.760]     RsvdFieldPosition: 0
[ 76577.760]     DirectColorModeInfo: 0
[ 76577.760]     PhysBasePtr: 0xe0000000
[ 76577.760]     LinBytesPerScanLine: 160
[ 76577.760]     BnkNumberOfImagePages: 0
[ 76577.760]     LinNumberOfImagePages: 0
[ 76577.760]     LinRedMaskSize: 0
[ 76577.761]     LinRedFieldPosition: 0
[ 76577.761]     LinGreenMaskSize: 0
[ 76577.761]     LinGreenFieldPosition: 0
[ 76577.761]     LinBlueMaskSize: 0
[ 76577.761]     LinBlueFieldPosition: 0
[ 76577.761]     LinRsvdMaskSize: 0
[ 76577.761]     LinRsvdFieldPosition: 0
[ 76577.761]     MaxPixelClock: 108500000
[ 76577.762] Mode: 109 (132x25)
[ 76577.762]     ModeAttributes: 0x38f
[ 76577.762]     WinAAttributes: 0x7
[ 76577.762]     WinBAttributes: 0x0
[ 76577.762]     WinGranularity: 32
[ 76577.762]     WinSize: 32
[ 76577.762]     WinASegment: 0xb800
[ 76577.762]     WinBSegment: 0x0
[ 76577.762]     WinFuncPtr: 0xc000ada2
[ 76577.762]     BytesPerScanline: 264
[ 76577.762]     XResolution: 132
[ 76577.763]     YResolution: 25
[ 76577.763]     XCharSize: 8
[ 76577.763]     YCharSize: 16
[ 76577.763]     NumberOfPlanes: 1
[ 76577.763]     BitsPerPixel: 4
[ 76577.763]     NumberOfBanks: 1
[ 76577.763]     MemoryModel: 0
[ 76577.763]     BankSize: 0
[ 76577.763]     NumberOfImages: 0
[ 76577.763]     RedMaskSize: 0
[ 76577.763]     RedFieldPosition: 0
[ 76577.763]     GreenMaskSize: 0
[ 76577.763]     GreenFieldPosition: 0
[ 76577.763]     BlueMaskSize: 0
[ 76577.763]     BlueFieldPosition: 0
[ 76577.763]     RsvdMaskSize: 0
[ 76577.763]     RsvdFieldPosition: 0
[ 76577.763]     DirectColorModeInfo: 0
[ 76577.763]     PhysBasePtr: 0xe0000000
[ 76577.763]     LinBytesPerScanLine: 264
[ 76577.763]     BnkNumberOfImagePages: 0
[ 76577.763]     LinNumberOfImagePages: 0
[ 76577.763]     LinRedMaskSize: 0
[ 76577.763]     LinRedFieldPosition: 0
[ 76577.763]     LinGreenMaskSize: 0
[ 76577.763]     LinGreenFieldPosition: 0
[ 76577.763]     LinBlueMaskSize: 0
[ 76577.763]     LinBlueFieldPosition: 0
[ 76577.763]     LinRsvdMaskSize: 0
[ 76577.763]     LinRsvdFieldPosition: 0
[ 76577.763]     MaxPixelClock: 108500000
[ 76577.769] Mode: 10a (132x43)
[ 76577.769]     ModeAttributes: 0x38f
[ 76577.769]     WinAAttributes: 0x7
[ 76577.769]     WinBAttributes: 0x0
[ 76577.769]     WinGranularity: 32
[ 76577.769]     WinSize: 32
[ 76577.769]     WinASegment: 0xb800
[ 76577.769]     WinBSegment: 0x0
[ 76577.769]     WinFuncPtr: 0xc000ada2
[ 76577.769]     BytesPerScanline: 264
[ 76577.769]     XResolution: 132
[ 76577.769]     YResolution: 43
[ 76577.769]     XCharSize: 8
[ 76577.769]     YCharSize: 9
[ 76577.769]     NumberOfPlanes: 1
[ 76577.769]     BitsPerPixel: 4
[ 76577.769]     NumberOfBanks: 1
[ 76577.769]     MemoryModel: 0
[ 76577.769]     BankSize: 0
[ 76577.769]     NumberOfImages: 0
[ 76577.769]     RedMaskSize: 0
[ 76577.769]     RedFieldPosition: 0
[ 76577.769]     GreenMaskSize: 0
[ 76577.769]     GreenFieldPosition: 0
[ 76577.769]     BlueMaskSize: 0
[ 76577.769]     BlueFieldPosition: 0
[ 76577.769]     RsvdMaskSize: 0
[ 76577.769]     RsvdFieldPosition: 0
[ 76577.769]     DirectColorModeInfo: 0
[ 76577.769]     PhysBasePtr: 0xe0000000
[ 76577.769]     LinBytesPerScanLine: 264
[ 76577.769]     BnkNumberOfImagePages: 0
[ 76577.769]     LinNumberOfImagePages: 0
[ 76577.769]     LinRedMaskSize: 0
[ 76577.769]     LinRedFieldPosition: 0
[ 76577.769]     LinGreenMaskSize: 0
[ 76577.770]     LinGreenFieldPosition: 0
[ 76577.770]     LinBlueMaskSize: 0
[ 76577.770]     LinBlueFieldPosition: 0
[ 76577.770]     LinRsvdMaskSize: 0
[ 76577.770]     LinRsvdFieldPosition: 0
[ 76577.770]     MaxPixelClock: 108500000
[ 76577.771] Mode: 10b (132x50)
[ 76577.771]     ModeAttributes: 0x38f
[ 76577.771]     WinAAttributes: 0x7
[ 76577.771]     WinBAttributes: 0x0
[ 76577.778]     WinGranularity: 32
[ 76577.778]     WinSize: 32
[ 76577.778]     WinASegment: 0xb800
[ 76577.778]     WinBSegment: 0x0
[ 76577.778]     WinFuncPtr: 0xc000ada2
[ 76577.778]     BytesPerScanline: 264
[ 76577.778]     XResolution: 132
[ 76577.778]     YResolution: 50
[ 76577.778]     XCharSize: 8
[ 76577.778]     YCharSize: 8
[ 76577.778]     NumberOfPlanes: 1
[ 76577.778]     BitsPerPixel: 4
[ 76577.778]     NumberOfBanks: 1
[ 76577.778]     MemoryModel: 0
[ 76577.778]     BankSize: 0
[ 76577.778]     NumberOfImages: 0
[ 76577.778]     RedMaskSize: 0
[ 76577.778]     RedFieldPosition: 0
[ 76577.778]     GreenMaskSize: 0
[ 76577.778]     GreenFieldPosition: 0
[ 76577.778]     BlueMaskSize: 0
[ 76577.778]     BlueFieldPosition: 0
[ 76577.778]     RsvdMaskSize: 0
[ 76577.778]     RsvdFieldPosition: 0
[ 76577.778]     DirectColorModeInfo: 0
[ 76577.778]     PhysBasePtr: 0xe0000000
[ 76577.778]     LinBytesPerScanLine: 264
[ 76577.778]     BnkNumberOfImagePages: 0
[ 76577.778]     LinNumberOfImagePages: 0
[ 76577.778]     LinRedMaskSize: 0
[ 76577.778]     LinRedFieldPosition: 0
[ 76577.778]     LinGreenMaskSize: 0
[ 76577.778]     LinGreenFieldPosition: 0
[ 76577.778]     LinBlueMaskSize: 0
[ 76577.778]     LinBlueFieldPosition: 0
[ 76577.778]     LinRsvdMaskSize: 0
[ 76577.778]     LinRsvdFieldPosition: 0
[ 76577.778]     MaxPixelClock: 108500000
[ 76577.780] Mode: 10c (132x60)
[ 76577.780]     ModeAttributes: 0x38f
[ 76577.780]     WinAAttributes: 0x7
[ 76577.781]     WinBAttributes: 0x0
[ 76577.781]     WinGranularity: 32
[ 76577.781]     WinSize: 32
[ 76577.781]     WinASegment: 0xb800
[ 76577.781]     WinBSegment: 0x0
[ 76577.781]     WinFuncPtr: 0xc000ada2
[ 76577.781]     BytesPerScanline: 264
[ 76577.781]     XResolution: 132
[ 76577.781]     YResolution: 60
[ 76577.781]     XCharSize: 8
[ 76577.781]     YCharSize: 8
[ 76577.781]     NumberOfPlanes: 1
[ 76577.781]     BitsPerPixel: 4
[ 76577.781]     NumberOfBanks: 1
[ 76577.781]     MemoryModel: 0
[ 76577.781]     BankSize: 0
[ 76577.781]     NumberOfImages: 0
[ 76577.781]     RedMaskSize: 0
[ 76577.781]     RedFieldPosition: 0
[ 76577.781]     GreenMaskSize: 0
[ 76577.781]     GreenFieldPosition: 0
[ 76577.781]     BlueMaskSize: 0
[ 76577.781]     BlueFieldPosition: 0
[ 76577.781]     RsvdMaskSize: 0
[ 76577.781]     RsvdFieldPosition: 0
[ 76577.781]     DirectColorModeInfo: 0
[ 76577.781]     PhysBasePtr: 0xe0000000
[ 76577.781]     LinBytesPerScanLine: 264
[ 76577.781]     BnkNumberOfImagePages: 0
[ 76577.781]     LinNumberOfImagePages: 0
[ 76577.781]     LinRedMaskSize: 0
[ 76577.781]     LinRedFieldPosition: 0
[ 76577.781]     LinGreenMaskSize: 0
[ 76577.781]     LinGreenFieldPosition: 0
[ 76577.781]     LinBlueMaskSize: 0
[ 76577.781]     LinBlueFieldPosition: 0
[ 76577.781]     LinRsvdMaskSize: 0
[ 76577.781]     LinRsvdFieldPosition: 0
[ 76577.781]     MaxPixelClock: 108500000
[ 76577.783] Mode: 10e (320x200)
[ 76577.783]     ModeAttributes: 0x39f
[ 76577.783]     WinAAttributes: 0x7
[ 76577.783]     WinBAttributes: 0x0
[ 76577.783]     WinGranularity: 64
[ 76577.783]     WinSize: 64
[ 76577.783]     WinASegment: 0xa000
[ 76577.783]     WinBSegment: 0x0
[ 76577.783]     WinFuncPtr: 0xc000ada2
[ 76577.783]     BytesPerScanline: 640
[ 76577.783]     XResolution: 320
[ 76577.783]     YResolution: 200
[ 76577.783]     XCharSize: 8
[ 76577.783]     YCharSize: 8
[ 76577.783]     NumberOfPlanes: 1
[ 76577.783]     BitsPerPixel: 16
[ 76577.783]     NumberOfBanks: 1
[ 76577.783]     MemoryModel: 6
[ 76577.783]     BankSize: 0
[ 76577.783]     NumberOfImages: 30
[ 76577.783]     RedMaskSize: 5
[ 76577.783]     RedFieldPosition: 11
[ 76577.783]     GreenMaskSize: 6
[ 76577.783]     GreenFieldPosition: 5
[ 76577.783]     BlueMaskSize: 5
[ 76577.783]     BlueFieldPosition: 0
[ 76577.783]     RsvdMaskSize: 0
[ 76577.790]     RsvdFieldPosition: 0
[ 76577.790]     DirectColorModeInfo: 0
[ 76577.790]     PhysBasePtr: 0xe0000000
[ 76577.790]     LinBytesPerScanLine: 640
[ 76577.790]     BnkNumberOfImagePages: 30
[ 76577.790]     LinNumberOfImagePages: 30
[ 76577.790]     LinRedMaskSize: 5
[ 76577.790]     LinRedFieldPosition: 11
[ 76577.790]     LinGreenMaskSize: 6
[ 76577.790]     LinGreenFieldPosition: 5
[ 76577.790]     LinBlueMaskSize: 5
[ 76577.790]     LinBlueFieldPosition: 0
[ 76577.790]     LinRsvdMaskSize: 0
[ 76577.790]     LinRsvdFieldPosition: 0
[ 76577.790]     MaxPixelClock: 229500000
[ 76577.791] *Mode: 10f (320x200)
[ 76577.791]     ModeAttributes: 0x39f
[ 76577.791]     WinAAttributes: 0x7
[ 76577.791]     WinBAttributes: 0x0
[ 76577.791]     WinGranularity: 64
[ 76577.791]     WinSize: 64
[ 76577.791]     WinASegment: 0xa000
[ 76577.791]     WinBSegment: 0x0
[ 76577.791]     WinFuncPtr: 0xc000ada2
[ 76577.792]     BytesPerScanline: 1280
[ 76577.792]     XResolution: 320
[ 76577.792]     YResolution: 200
[ 76577.792]     XCharSize: 8
[ 76577.792]     YCharSize: 8
[ 76577.792]     NumberOfPlanes: 1
[ 76577.792]     BitsPerPixel: 32
[ 76577.792]     NumberOfBanks: 1
[ 76577.792]     MemoryModel: 6
[ 76577.792]     BankSize: 0
[ 76577.792]     NumberOfImages: 14
[ 76577.792]     RedMaskSize: 8
[ 76577.792]     RedFieldPosition: 16
[ 76577.792]     GreenMaskSize: 8
[ 76577.792]     GreenFieldPosition: 8
[ 76577.792]     BlueMaskSize: 8
[ 76577.792]     BlueFieldPosition: 0
[ 76577.792]     RsvdMaskSize: 8
[ 76577.792]     RsvdFieldPosition: 24
[ 76577.792]     DirectColorModeInfo: 0
[ 76577.792]     PhysBasePtr: 0xe0000000
[ 76577.792]     LinBytesPerScanLine: 1280
[ 76577.792]     BnkNumberOfImagePages: 14
[ 76577.792]     LinNumberOfImagePages: 14
[ 76577.792]     LinRedMaskSize: 8
[ 76577.792]     LinRedFieldPosition: 16
[ 76577.792]     LinGreenMaskSize: 8
[ 76577.792]     LinGreenFieldPosition: 8
[ 76577.792]     LinBlueMaskSize: 8
[ 76577.792]     LinBlueFieldPosition: 0
[ 76577.792]     LinRsvdMaskSize: 8
[ 76577.792]     LinRsvdFieldPosition: 24
[ 76577.792]     MaxPixelClock: 229500000
[ 76577.800] Mode: 111 (640x480)
[ 76577.800]     ModeAttributes: 0x39f
[ 76577.800]     WinAAttributes: 0x7
[ 76577.800]     WinBAttributes: 0x0
[ 76577.800]     WinGranularity: 64
[ 76577.800]     WinSize: 64
[ 76577.800]     WinASegment: 0xa000
[ 76577.800]     WinBSegment: 0x0
[ 76577.800]     WinFuncPtr: 0xc000ada2
[ 76577.800]     BytesPerScanline: 1280
[ 76577.800]     XResolution: 640
[ 76577.800]     YResolution: 480
[ 76577.800]     XCharSize: 8
[ 76577.800]     YCharSize: 16
[ 76577.800]     NumberOfPlanes: 1
[ 76577.800]     BitsPerPixel: 16
[ 76577.800]     NumberOfBanks: 1
[ 76577.800]     MemoryModel: 6
[ 76577.800]     BankSize: 0
[ 76577.800]     NumberOfImages: 4
[ 76577.800]     RedMaskSize: 5
[ 76577.800]     RedFieldPosition: 11
[ 76577.801]     GreenMaskSize: 6
[ 76577.801]     GreenFieldPosition: 5
[ 76577.801]     BlueMaskSize: 5
[ 76577.801]     BlueFieldPosition: 0
[ 76577.801]     RsvdMaskSize: 0
[ 76577.801]     RsvdFieldPosition: 0
[ 76577.801]     DirectColorModeInfo: 0
[ 76577.801]     PhysBasePtr: 0xe0000000
[ 76577.801]     LinBytesPerScanLine: 1280
[ 76577.801]     BnkNumberOfImagePages: 4
[ 76577.801]     LinNumberOfImagePages: 4
[ 76577.801]     LinRedMaskSize: 5
[ 76577.801]     LinRedFieldPosition: 11
[ 76577.801]     LinGreenMaskSize: 6
[ 76577.801]     LinGreenFieldPosition: 5
[ 76577.801]     LinBlueMaskSize: 5
[ 76577.801]     LinBlueFieldPosition: 0
[ 76577.801]     LinRsvdMaskSize: 0
[ 76577.801]     LinRsvdFieldPosition: 0
[ 76577.801]     MaxPixelClock: 229500000
[ 76577.802] *Mode: 112 (640x480)
[ 76577.802]     ModeAttributes: 0x39f
[ 76577.802]     WinAAttributes: 0x7
[ 76577.802]     WinBAttributes: 0x0
[ 76577.802]     WinGranularity: 64
[ 76577.802]     WinSize: 64
[ 76577.802]     WinASegment: 0xa000
[ 76577.802]     WinBSegment: 0x0
[ 76577.802]     WinFuncPtr: 0xc000ada2
[ 76577.802]     BytesPerScanline: 2560
[ 76577.802]     XResolution: 640
[ 76577.802]     YResolution: 480
[ 76577.802]     XCharSize: 8
[ 76577.802]     YCharSize: 16
[ 76577.802]     NumberOfPlanes: 1
[ 76577.802]     BitsPerPixel: 32
[ 76577.802]     NumberOfBanks: 1
[ 76577.802]     MemoryModel: 6
[ 76577.802]     BankSize: 0
[ 76577.803]     NumberOfImages: 1
[ 76577.803]     RedMaskSize: 8
[ 76577.803]     RedFieldPosition: 16
[ 76577.803]     GreenMaskSize: 8
[ 76577.803]     GreenFieldPosition: 8
[ 76577.803]     BlueMaskSize: 8
[ 76577.803]     BlueFieldPosition: 0
[ 76577.803]     RsvdMaskSize: 8
[ 76577.803]     RsvdFieldPosition: 24
[ 76577.803]     DirectColorModeInfo: 0
[ 76577.803]     PhysBasePtr: 0xe0000000
[ 76577.803]     LinBytesPerScanLine: 2560
[ 76577.803]     BnkNumberOfImagePages: 1
[ 76577.803]     LinNumberOfImagePages: 1
[ 76577.803]     LinRedMaskSize: 8
[ 76577.803]     LinRedFieldPosition: 16
[ 76577.803]     LinGreenMaskSize: 8
[ 76577.803]     LinGreenFieldPosition: 8
[ 76577.803]     LinBlueMaskSize: 8
[ 76577.803]     LinBlueFieldPosition: 0
[ 76577.803]     LinRsvdMaskSize: 8
[ 76577.803]     LinRsvdFieldPosition: 24
[ 76577.803]     MaxPixelClock: 229500000
[ 76577.813] Mode: 114 (800x600)
[ 76577.813]     ModeAttributes: 0x39f
[ 76577.813]     WinAAttributes: 0x7
[ 76577.813]     WinBAttributes: 0x0
[ 76577.813]     WinGranularity: 64
[ 76577.813]     WinSize: 64
[ 76577.813]     WinASegment: 0xa000
[ 76577.813]     WinBSegment: 0x0
[ 76577.813]     WinFuncPtr: 0xc000ada2
[ 76577.813]     BytesPerScanline: 1600
[ 76577.813]     XResolution: 800
[ 76577.813]     YResolution: 600
[ 76577.813]     XCharSize: 8
[ 76577.813]     YCharSize: 16
[ 76577.813]     NumberOfPlanes: 1
[ 76577.813]     BitsPerPixel: 16
[ 76577.813]     NumberOfBanks: 1
[ 76577.813]     MemoryModel: 6
[ 76577.813]     BankSize: 0
[ 76577.813]     NumberOfImages: 2
[ 76577.813]     RedMaskSize: 5
[ 76577.813]     RedFieldPosition: 11
[ 76577.813]     GreenMaskSize: 6
[ 76577.813]     GreenFieldPosition: 5
[ 76577.813]     BlueMaskSize: 5
[ 76577.813]     BlueFieldPosition: 0
[ 76577.813]     RsvdMaskSize: 0
[ 76577.813]     RsvdFieldPosition: 0
[ 76577.813]     DirectColorModeInfo: 0
[ 76577.813]     PhysBasePtr: 0xe0000000
[ 76577.813]     LinBytesPerScanLine: 1600
[ 76577.813]     BnkNumberOfImagePages: 2
[ 76577.813]     LinNumberOfImagePages: 2
[ 76577.813]     LinRedMaskSize: 5
[ 76577.813]     LinRedFieldPosition: 11
[ 76577.813]     LinGreenMaskSize: 6
[ 76577.813]     LinGreenFieldPosition: 5
[ 76577.813]     LinBlueMaskSize: 5
[ 76577.813]     LinBlueFieldPosition: 0
[ 76577.813]     LinRsvdMaskSize: 0
[ 76577.813]     LinRsvdFieldPosition: 0
[ 76577.813]     MaxPixelClock: 229500000
[ 76577.815] *Mode: 115 (800x600)
[ 76577.815]     ModeAttributes: 0x39f
[ 76577.815]     WinAAttributes: 0x7
[ 76577.815]     WinBAttributes: 0x0
[ 76577.815]     WinGranularity: 64
[ 76577.815]     WinSize: 64
[ 76577.815]     WinASegment: 0xa000
[ 76577.815]     WinBSegment: 0x0
[ 76577.815]     WinFuncPtr: 0xc000ada2
[ 76577.815]     BytesPerScanline: 3200
[ 76577.815]     XResolution: 800
[ 76577.815]     YResolution: 600
[ 76577.815]     XCharSize: 8
[ 76577.815]     YCharSize: 16
[ 76577.815]     NumberOfPlanes: 1
[ 76577.815]     BitsPerPixel: 32
[ 76577.815]     NumberOfBanks: 1
[ 76577.815]     MemoryModel: 6
[ 76577.815]     BankSize: 0
[ 76577.815]     NumberOfImages: 1
[ 76577.815]     RedMaskSize: 8
[ 76577.815]     RedFieldPosition: 16
[ 76577.815]     GreenMaskSize: 8
[ 76577.815]     GreenFieldPosition: 8
[ 76577.815]     BlueMaskSize: 8
[ 76577.815]     BlueFieldPosition: 0
[ 76577.815]     RsvdMaskSize: 8
[ 76577.815]     RsvdFieldPosition: 24
[ 76577.815]     DirectColorModeInfo: 0
[ 76577.815]     PhysBasePtr: 0xe0000000
[ 76577.815]     LinBytesPerScanLine: 3200
[ 76577.815]     BnkNumberOfImagePages: 1
[ 76577.815]     LinNumberOfImagePages: 1
[ 76577.815]     LinRedMaskSize: 8
[ 76577.815]     LinRedFieldPosition: 16
[ 76577.815]     LinGreenMaskSize: 8
[ 76577.815]     LinGreenFieldPosition: 8
[ 76577.815]     LinBlueMaskSize: 8
[ 76577.815]     LinBlueFieldPosition: 0
[ 76577.815]     LinRsvdMaskSize: 8
[ 76577.815]     LinRsvdFieldPosition: 24
[ 76577.815]     MaxPixelClock: 229500000
[ 76577.823] Mode: 117 (1024x768)
[ 76577.823]     ModeAttributes: 0x39f
[ 76577.823]     WinAAttributes: 0x7
[ 76577.823]     WinBAttributes: 0x0
[ 76577.823]     WinGranularity: 64
[ 76577.823]     WinSize: 64
[ 76577.823]     WinASegment: 0xa000
[ 76577.823]     WinBSegment: 0x0
[ 76577.823]     WinFuncPtr: 0xc000ada2
[ 76577.823]     BytesPerScanline: 2048
[ 76577.823]     XResolution: 1024
[ 76577.823]     YResolution: 768
[ 76577.823]     XCharSize: 8
[ 76577.823]     YCharSize: 16
[ 76577.823]     NumberOfPlanes: 1
[ 76577.823]     BitsPerPixel: 16
[ 76577.823]     NumberOfBanks: 1
[ 76577.823]     MemoryModel: 6
[ 76577.823]     BankSize: 0
[ 76577.824]     NumberOfImages: 1
[ 76577.824]     RedMaskSize: 5
[ 76577.824]     RedFieldPosition: 11
[ 76577.824]     GreenMaskSize: 6
[ 76577.824]     GreenFieldPosition: 5
[ 76577.824]     BlueMaskSize: 5
[ 76577.824]     BlueFieldPosition: 0
[ 76577.824]     RsvdMaskSize: 0
[ 76577.824]     RsvdFieldPosition: 0
[ 76577.824]     DirectColorModeInfo: 0
[ 76577.824]     PhysBasePtr: 0xe0000000
[ 76577.824]     LinBytesPerScanLine: 2048
[ 76577.824]     BnkNumberOfImagePages: 1
[ 76577.824]     LinNumberOfImagePages: 1
[ 76577.824]     LinRedMaskSize: 5
[ 76577.824]     LinRedFieldPosition: 11
[ 76577.824]     LinGreenMaskSize: 6
[ 76577.824]     LinGreenFieldPosition: 5
[ 76577.824]     LinBlueMaskSize: 5
[ 76577.824]     LinBlueFieldPosition: 0
[ 76577.824]     LinRsvdMaskSize: 0
[ 76577.824]     LinRsvdFieldPosition: 0
[ 76577.824]     MaxPixelClock: 229500000
[ 76577.829] *Mode: 118 (1024x768)
[ 76577.829]     ModeAttributes: 0x39f
[ 76577.829]     WinAAttributes: 0x7
[ 76577.829]     WinBAttributes: 0x0
[ 76577.829]     WinGranularity: 64
[ 76577.829]     WinSize: 64
[ 76577.829]     WinASegment: 0xa000
[ 76577.829]     WinBSegment: 0x0
[ 76577.829]     WinFuncPtr: 0xc000ada2
[ 76577.829]     BytesPerScanline: 4096
[ 76577.829]     XResolution: 1024
[ 76577.829]     YResolution: 768
[ 76577.829]     XCharSize: 8
[ 76577.829]     YCharSize: 16
[ 76577.829]     NumberOfPlanes: 1
[ 76577.829]     BitsPerPixel: 32
[ 76577.829]     NumberOfBanks: 1
[ 76577.829]     MemoryModel: 6
[ 76577.829]     BankSize: 0
[ 76577.829]     NumberOfImages: 1
[ 76577.829]     RedMaskSize: 8
[ 76577.829]     RedFieldPosition: 16
[ 76577.829]     GreenMaskSize: 8
[ 76577.829]     GreenFieldPosition: 8
[ 76577.829]     BlueMaskSize: 8
[ 76577.829]     BlueFieldPosition: 0
[ 76577.829]     RsvdMaskSize: 8
[ 76577.829]     RsvdFieldPosition: 24
[ 76577.829]     DirectColorModeInfo: 0
[ 76577.829]     PhysBasePtr: 0xe0000000
[ 76577.829]     LinBytesPerScanLine: 4096
[ 76577.829]     BnkNumberOfImagePages: 1
[ 76577.829]     LinNumberOfImagePages: 1
[ 76577.829]     LinRedMaskSize: 8
[ 76577.829]     LinRedFieldPosition: 16
[ 76577.830]     LinGreenMaskSize: 8
[ 76577.830]     LinGreenFieldPosition: 8
[ 76577.830]     LinBlueMaskSize: 8
[ 76577.830]     LinBlueFieldPosition: 0
[ 76577.830]     LinRsvdMaskSize: 8
[ 76577.830]     LinRsvdFieldPosition: 24
[ 76577.830]     MaxPixelClock: 229500000
[ 76577.831] Mode: 11a (1280x1024)
[ 76577.831]     ModeAttributes: 0x39f
[ 76577.831]     WinAAttributes: 0x7
[ 76577.831]     WinBAttributes: 0x0
[ 76577.831]     WinGranularity: 64
[ 76577.831]     WinSize: 64
[ 76577.831]     WinASegment: 0xa000
[ 76577.831]     WinBSegment: 0x0
[ 76577.831]     WinFuncPtr: 0xc000ada2
[ 76577.831]     BytesPerScanline: 2560
[ 76577.831]     XResolution: 1280
[ 76577.837]     YResolution: 1024
[ 76577.837]     XCharSize: 8
[ 76577.837]     YCharSize: 16
[ 76577.837]     NumberOfPlanes: 1
[ 76577.837]     BitsPerPixel: 16
[ 76577.837]     NumberOfBanks: 1
[ 76577.837]     MemoryModel: 6
[ 76577.837]     BankSize: 0
[ 76577.837]     NumberOfImages: 1
[ 76577.837]     RedMaskSize: 5
[ 76577.837]     RedFieldPosition: 11
[ 76577.837]     GreenMaskSize: 6
[ 76577.837]     GreenFieldPosition: 5
[ 76577.837]     BlueMaskSize: 5
[ 76577.837]     BlueFieldPosition: 0
[ 76577.837]     RsvdMaskSize: 0
[ 76577.837]     RsvdFieldPosition: 0
[ 76577.837]     DirectColorModeInfo: 0
[ 76577.837]     PhysBasePtr: 0xe0000000
[ 76577.837]     LinBytesPerScanLine: 2560
[ 76577.837]     BnkNumberOfImagePages: 1
[ 76577.837]     LinNumberOfImagePages: 1
[ 76577.837]     LinRedMaskSize: 5
[ 76577.837]     LinRedFieldPosition: 11
[ 76577.837]     LinGreenMaskSize: 6
[ 76577.837]     LinGreenFieldPosition: 5
[ 76577.837]     LinBlueMaskSize: 5
[ 76577.837]     LinBlueFieldPosition: 0
[ 76577.837]     LinRsvdMaskSize: 0
[ 76577.837]     LinRsvdFieldPosition: 0
[ 76577.838]     MaxPixelClock: 229500000
[ 76577.840] *Mode: 11b (1280x1024)
[ 76577.840]     ModeAttributes: 0x39f
[ 76577.840]     WinAAttributes: 0x7
[ 76577.840]     WinBAttributes: 0x0
[ 76577.840]     WinGranularity: 64
[ 76577.840]     WinSize: 64
[ 76577.840]     WinASegment: 0xa000
[ 76577.840]     WinBSegment: 0x0
[ 76577.840]     WinFuncPtr: 0xc000ada2
[ 76577.840]     BytesPerScanline: 5120
[ 76577.840]     XResolution: 1280
[ 76577.840]     YResolution: 1024
[ 76577.840]     XCharSize: 8
[ 76577.840]     YCharSize: 16
[ 76577.840]     NumberOfPlanes: 1
[ 76577.840]     BitsPerPixel: 32
[ 76577.840]     NumberOfBanks: 1
[ 76577.840]     MemoryModel: 6
[ 76577.840]     BankSize: 0
[ 76577.840]     NumberOfImages: 0
[ 76577.840]     RedMaskSize: 8
[ 76577.840]     RedFieldPosition: 16
[ 76577.840]     GreenMaskSize: 8
[ 76577.840]     GreenFieldPosition: 8
[ 76577.840]     BlueMaskSize: 8
[ 76577.840]     BlueFieldPosition: 0
[ 76577.840]     RsvdMaskSize: 8
[ 76577.840]     RsvdFieldPosition: 24
[ 76577.840]     DirectColorModeInfo: 0
[ 76577.840]     PhysBasePtr: 0xe0000000
[ 76577.840]     LinBytesPerScanLine: 5120
[ 76577.840]     BnkNumberOfImagePages: 0
[ 76577.840]     LinNumberOfImagePages: 0
[ 76577.840]     LinRedMaskSize: 8
[ 76577.840]     LinRedFieldPosition: 16
[ 76577.840]     LinGreenMaskSize: 8
[ 76577.840]     LinGreenFieldPosition: 8
[ 76577.840]     LinBlueMaskSize: 8
[ 76577.840]     LinBlueFieldPosition: 0
[ 76577.840]     LinRsvdMaskSize: 8
[ 76577.840]     LinRsvdFieldPosition: 24
[ 76577.848]     MaxPixelClock: 229500000
[ 76577.849] Mode: 130 (320x200)
[ 76577.849]     ModeAttributes: 0x39f
[ 76577.849]     WinAAttributes: 0x7
[ 76577.849]     WinBAttributes: 0x0
[ 76577.849]     WinGranularity: 64
[ 76577.849]     WinSize: 64
[ 76577.849]     WinASegment: 0xa000
[ 76577.849]     WinBSegment: 0x0
[ 76577.849]     WinFuncPtr: 0xc000ada2
[ 76577.849]     BytesPerScanline: 320
[ 76577.849]     XResolution: 320
[ 76577.849]     YResolution: 200
[ 76577.849]     XCharSize: 8
[ 76577.849]     YCharSize: 8
[ 76577.849]     NumberOfPlanes: 1
[ 76577.849]     BitsPerPixel: 8
[ 76577.849]     NumberOfBanks: 1
[ 76577.849]     MemoryModel: 4
[ 76577.849]     BankSize: 0
[ 76577.849]     NumberOfImages: 62
[ 76577.850]     RedMaskSize: 0
[ 76577.850]     RedFieldPosition: 0
[ 76577.850]     GreenMaskSize: 0
[ 76577.850]     GreenFieldPosition: 0
[ 76577.850]     BlueMaskSize: 0
[ 76577.850]     BlueFieldPosition: 0
[ 76577.855]     RsvdMaskSize: 0
[ 76577.855]     RsvdFieldPosition: 0
[ 76577.855]     DirectColorModeInfo: 0
[ 76577.855]     PhysBasePtr: 0xe0000000
[ 76577.855]     LinBytesPerScanLine: 320
[ 76577.855]     BnkNumberOfImagePages: 62
[ 76577.855]     LinNumberOfImagePages: 62
[ 76577.855]     LinRedMaskSize: 0
[ 76577.855]     LinRedFieldPosition: 0
[ 76577.855]     LinGreenMaskSize: 0
[ 76577.855]     LinGreenFieldPosition: 0
[ 76577.855]     LinBlueMaskSize: 0
[ 76577.855]     LinBlueFieldPosition: 0
[ 76577.855]     LinRsvdMaskSize: 0
[ 76577.855]     LinRsvdFieldPosition: 0
[ 76577.855]     MaxPixelClock: 229500000
[ 76577.857] Mode: 131 (320x400)
[ 76577.857]     ModeAttributes: 0x39f
[ 76577.857]     WinAAttributes: 0x7
[ 76577.857]     WinBAttributes: 0x0
[ 76577.857]     WinGranularity: 64
[ 76577.857]     WinSize: 64
[ 76577.857]     WinASegment: 0xa000
[ 76577.857]     WinBSegment: 0x0
[ 76577.857]     WinFuncPtr: 0xc000ada2
[ 76577.857]     BytesPerScanline: 320
[ 76577.857]     XResolution: 320
[ 76577.857]     YResolution: 400
[ 76577.857]     XCharSize: 8
[ 76577.857]     YCharSize: 16
[ 76577.857]     NumberOfPlanes: 1
[ 76577.857]     BitsPerPixel: 8
[ 76577.857]     NumberOfBanks: 1
[ 76577.857]     MemoryModel: 4
[ 76577.857]     BankSize: 0
[ 76577.857]     NumberOfImages: 30
[ 76577.857]     RedMaskSize: 0
[ 76577.857]     RedFieldPosition: 0
[ 76577.857]     GreenMaskSize: 0
[ 76577.857]     GreenFieldPosition: 0
[ 76577.857]     BlueMaskSize: 0
[ 76577.857]     BlueFieldPosition: 0
[ 76577.857]     RsvdMaskSize: 0
[ 76577.857]     RsvdFieldPosition: 0
[ 76577.857]     DirectColorModeInfo: 0
[ 76577.857]     PhysBasePtr: 0xe0000000
[ 76577.857]     LinBytesPerScanLine: 320
[ 76577.857]     BnkNumberOfImagePages: 30
[ 76577.857]     LinNumberOfImagePages: 30
[ 76577.857]     LinRedMaskSize: 0
[ 76577.857]     LinRedFieldPosition: 0
[ 76577.857]     LinGreenMaskSize: 0
[ 76577.857]     LinGreenFieldPosition: 0
[ 76577.857]     LinBlueMaskSize: 0
[ 76577.857]     LinBlueFieldPosition: 0
[ 76577.857]     LinRsvdMaskSize: 0
[ 76577.857]     LinRsvdFieldPosition: 0
[ 76577.857]     MaxPixelClock: 229500000
[ 76577.859] Mode: 132 (320x400)
[ 76577.859]     ModeAttributes: 0x39f
[ 76577.859]     WinAAttributes: 0x7
[ 76577.859]     WinBAttributes: 0x0
[ 76577.859]     WinGranularity: 64
[ 76577.859]     WinSize: 64
[ 76577.859]     WinASegment: 0xa000
[ 76577.859]     WinBSegment: 0x0
[ 76577.859]     WinFuncPtr: 0xc000ada2
[ 76577.859]     BytesPerScanline: 640
[ 76577.859]     XResolution: 320
[ 76577.859]     YResolution: 400
[ 76577.859]     XCharSize: 8
[ 76577.859]     YCharSize: 16
[ 76577.859]     NumberOfPlanes: 1
[ 76577.859]     BitsPerPixel: 16
[ 76577.859]     NumberOfBanks: 1
[ 76577.859]     MemoryModel: 6
[ 76577.859]     BankSize: 0
[ 76577.859]     NumberOfImages: 14
[ 76577.859]     RedMaskSize: 5
[ 76577.859]     RedFieldPosition: 11
[ 76577.859]     GreenMaskSize: 6
[ 76577.859]     GreenFieldPosition: 5
[ 76577.859]     BlueMaskSize: 5
[ 76577.859]     BlueFieldPosition: 0
[ 76577.859]     RsvdMaskSize: 0
[ 76577.859]     RsvdFieldPosition: 0
[ 76577.859]     DirectColorModeInfo: 0
[ 76577.859]     PhysBasePtr: 0xe0000000
[ 76577.859]     LinBytesPerScanLine: 640
[ 76577.859]     BnkNumberOfImagePages: 14
[ 76577.863]     LinNumberOfImagePages: 14
[ 76577.863]     LinRedMaskSize: 5
[ 76577.863]     LinRedFieldPosition: 11
[ 76577.863]     LinGreenMaskSize: 6
[ 76577.863]     LinGreenFieldPosition: 5
[ 76577.863]     LinBlueMaskSize: 5
[ 76577.863]     LinBlueFieldPosition: 0
[ 76577.863]     LinRsvdMaskSize: 0
[ 76577.863]     LinRsvdFieldPosition: 0
[ 76577.863]     MaxPixelClock: 229500000
[ 76577.867] *Mode: 133 (320x400)
[ 76577.867]     ModeAttributes: 0x39f
[ 76577.867]     WinAAttributes: 0x7
[ 76577.867]     WinBAttributes: 0x0
[ 76577.867]     WinGranularity: 64
[ 76577.867]     WinSize: 64
[ 76577.867]     WinASegment: 0xa000
[ 76577.867]     WinBSegment: 0x0
[ 76577.867]     WinFuncPtr: 0xc000ada2
[ 76577.867]     BytesPerScanline: 1280
[ 76577.867]     XResolution: 320
[ 76577.867]     YResolution: 400
[ 76577.867]     XCharSize: 8
[ 76577.867]     YCharSize: 16
[ 76577.867]     NumberOfPlanes: 1
[ 76577.867]     BitsPerPixel: 32
[ 76577.867]     NumberOfBanks: 1
[ 76577.867]     MemoryModel: 6
[ 76577.867]     BankSize: 0
[ 76577.867]     NumberOfImages: 6
[ 76577.867]     RedMaskSize: 8
[ 76577.867]     RedFieldPosition: 16
[ 76577.867]     GreenMaskSize: 8
[ 76577.867]     GreenFieldPosition: 8
[ 76577.867]     BlueMaskSize: 8
[ 76577.867]     BlueFieldPosition: 0
[ 76577.867]     RsvdMaskSize: 8
[ 76577.867]     RsvdFieldPosition: 24
[ 76577.867]     DirectColorModeInfo: 0
[ 76577.867]     PhysBasePtr: 0xe0000000
[ 76577.867]     LinBytesPerScanLine: 1280
[ 76577.867]     BnkNumberOfImagePages: 6
[ 76577.867]     LinNumberOfImagePages: 6
[ 76577.867]     LinRedMaskSize: 8
[ 76577.867]     LinRedFieldPosition: 16
[ 76577.867]     LinGreenMaskSize: 8
[ 76577.867]     LinGreenFieldPosition: 8
[ 76577.867]     LinBlueMaskSize: 8
[ 76577.867]     LinBlueFieldPosition: 0
[ 76577.867]     LinRsvdMaskSize: 8
[ 76577.867]     LinRsvdFieldPosition: 24
[ 76577.867]     MaxPixelClock: 229500000
[ 76577.871] Mode: 134 (320x240)
[ 76577.872]     ModeAttributes: 0x39f
[ 76577.872]     WinAAttributes: 0x7
[ 76577.872]     WinBAttributes: 0x0
[ 76577.872]     WinGranularity: 64
[ 76577.872]     WinSize: 64
[ 76577.872]     WinASegment: 0xa000
[ 76577.872]     WinBSegment: 0x0
[ 76577.872]     WinFuncPtr: 0xc000ada2
[ 76577.872]     BytesPerScanline: 320
[ 76577.872]     XResolution: 320
[ 76577.872]     YResolution: 240
[ 76577.872]     XCharSize: 8
[ 76577.872]     YCharSize: 8
[ 76577.872]     NumberOfPlanes: 1
[ 76577.872]     BitsPerPixel: 8
[ 76577.872]     NumberOfBanks: 1
[ 76577.872]     MemoryModel: 4
[ 76577.872]     BankSize: 0
[ 76577.872]     NumberOfImages: 30
[ 76577.872]     RedMaskSize: 0
[ 76577.872]     RedFieldPosition: 0
[ 76577.872]     GreenMaskSize: 0
[ 76577.872]     GreenFieldPosition: 0
[ 76577.872]     BlueMaskSize: 0
[ 76577.872]     BlueFieldPosition: 0
[ 76577.872]     RsvdMaskSize: 0
[ 76577.872]     RsvdFieldPosition: 0
[ 76577.872]     DirectColorModeInfo: 0
[ 76577.872]     PhysBasePtr: 0xe0000000
[ 76577.872]     LinBytesPerScanLine: 320
[ 76577.872]     BnkNumberOfImagePages: 30
[ 76577.872]     LinNumberOfImagePages: 30
[ 76577.872]     LinRedMaskSize: 0
[ 76577.872]     LinRedFieldPosition: 0
[ 76577.872]     LinGreenMaskSize: 0
[ 76577.872]     LinGreenFieldPosition: 0
[ 76577.872]     LinBlueMaskSize: 0
[ 76577.872]     LinBlueFieldPosition: 0
[ 76577.872]     LinRsvdMaskSize: 0
[ 76577.872]     LinRsvdFieldPosition: 0
[ 76577.872]     MaxPixelClock: 229500000
[ 76577.874] Mode: 135 (320x240)
[ 76577.874]     ModeAttributes: 0x39f
[ 76577.874]     WinAAttributes: 0x7
[ 76577.874]     WinBAttributes: 0x0
[ 76577.874]     WinGranularity: 64
[ 76577.874]     WinSize: 64
[ 76577.874]     WinASegment: 0xa000
[ 76577.874]     WinBSegment: 0x0
[ 76577.874]     WinFuncPtr: 0xc000ada2
[ 76577.874]     BytesPerScanline: 640
[ 76577.874]     XResolution: 320
[ 76577.874]     YResolution: 240
[ 76577.874]     XCharSize: 8
[ 76577.874]     YCharSize: 8
[ 76577.874]     NumberOfPlanes: 1
[ 76577.874]     BitsPerPixel: 16
[ 76577.874]     NumberOfBanks: 1
[ 76577.874]     MemoryModel: 6
[ 76577.874]     BankSize: 0
[ 76577.874]     NumberOfImages: 19
[ 76577.874]     RedMaskSize: 5
[ 76577.874]     RedFieldPosition: 11
[ 76577.874]     GreenMaskSize: 6
[ 76577.874]     GreenFieldPosition: 5
[ 76577.874]     BlueMaskSize: 5
[ 76577.874]     BlueFieldPosition: 0
[ 76577.874]     RsvdMaskSize: 0
[ 76577.874]     RsvdFieldPosition: 0
[ 76577.874]     DirectColorModeInfo: 0
[ 76577.874]     PhysBasePtr: 0xe0000000
[ 76577.874]     LinBytesPerScanLine: 640
[ 76577.874]     BnkNumberOfImagePages: 19
[ 76577.874]     LinNumberOfImagePages: 19
[ 76577.874]     LinRedMaskSize: 5
[ 76577.874]     LinRedFieldPosition: 11
[ 76577.874]     LinGreenMaskSize: 6
[ 76577.874]     LinGreenFieldPosition: 5
[ 76577.874]     LinBlueMaskSize: 5
[ 76577.874]     LinBlueFieldPosition: 0
[ 76577.874]     LinRsvdMaskSize: 0
[ 76577.874]     LinRsvdFieldPosition: 0
[ 76577.874]     MaxPixelClock: 229500000
[ 76577.885] *Mode: 136 (320x240)
[ 76577.885]     ModeAttributes: 0x39f
[ 76577.885]     WinAAttributes: 0x7
[ 76577.885]     WinBAttributes: 0x0
[ 76577.885]     WinGranularity: 64
[ 76577.885]     WinSize: 64
[ 76577.885]     WinASegment: 0xa000
[ 76577.885]     WinBSegment: 0x0
[ 76577.885]     WinFuncPtr: 0xc000ada2
[ 76577.885]     BytesPerScanline: 1280
[ 76577.885]     XResolution: 320
[ 76577.885]     YResolution: 240
[ 76577.885]     XCharSize: 8
[ 76577.885]     YCharSize: 8
[ 76577.885]     NumberOfPlanes: 1
[ 76577.885]     BitsPerPixel: 32
[ 76577.885]     NumberOfBanks: 1
[ 76577.885]     MemoryModel: 6
[ 76577.885]     BankSize: 0
[ 76577.885]     NumberOfImages: 10
[ 76577.885]     RedMaskSize: 8
[ 76577.885]     RedFieldPosition: 16
[ 76577.885]     GreenMaskSize: 8
[ 76577.885]     GreenFieldPosition: 8
[ 76577.885]     BlueMaskSize: 8
[ 76577.885]     BlueFieldPosition: 0
[ 76577.885]     RsvdMaskSize: 8
[ 76577.885]     RsvdFieldPosition: 24
[ 76577.885]     DirectColorModeInfo: 0
[ 76577.885]     PhysBasePtr: 0xe0000000
[ 76577.885]     LinBytesPerScanLine: 1280
[ 76577.885]     BnkNumberOfImagePages: 10
[ 76577.885]     LinNumberOfImagePages: 10
[ 76577.885]     LinRedMaskSize: 8
[ 76577.885]     LinRedFieldPosition: 16
[ 76577.885]     LinGreenMaskSize: 8
[ 76577.885]     LinGreenFieldPosition: 8
[ 76577.885]     LinBlueMaskSize: 8
[ 76577.885]     LinBlueFieldPosition: 0
[ 76577.885]     LinRsvdMaskSize: 8
[ 76577.885]     LinRsvdFieldPosition: 24
[ 76577.885]     MaxPixelClock: 229500000
[ 76577.887] Mode: 13d (640x400)
[ 76577.887]     ModeAttributes: 0x39f
[ 76577.887]     WinAAttributes: 0x7
[ 76577.887]     WinBAttributes: 0x0
[ 76577.887]     WinGranularity: 64
[ 76577.887]     WinSize: 64
[ 76577.887]     WinASegment: 0xa000
[ 76577.887]     WinBSegment: 0x0
[ 76577.887]     WinFuncPtr: 0xc000ada2
[ 76577.887]     BytesPerScanline: 1280
[ 76577.887]     XResolution: 640
[ 76577.887]     YResolution: 400
[ 76577.887]     XCharSize: 8
[ 76577.887]     YCharSize: 16
[ 76577.887]     NumberOfPlanes: 1
[ 76577.887]     BitsPerPixel: 16
[ 76577.887]     NumberOfBanks: 1
[ 76577.887]     MemoryModel: 6
[ 76577.887]     BankSize: 0
[ 76577.887]     NumberOfImages: 6
[ 76577.887]     RedMaskSize: 5
[ 76577.887]     RedFieldPosition: 11
[ 76577.887]     GreenMaskSize: 6
[ 76577.887]     GreenFieldPosition: 5
[ 76577.887]     BlueMaskSize: 5
[ 76577.887]     BlueFieldPosition: 0
[ 76577.887]     RsvdMaskSize: 0
[ 76577.887]     RsvdFieldPosition: 0
[ 76577.887]     DirectColorModeInfo: 0
[ 76577.887]     PhysBasePtr: 0xe0000000
[ 76577.887]     LinBytesPerScanLine: 1280
[ 76577.887]     BnkNumberOfImagePages: 6
[ 76577.887]     LinNumberOfImagePages: 6
[ 76577.887]     LinRedMaskSize: 5
[ 76577.887]     LinRedFieldPosition: 11
[ 76577.887]     LinGreenMaskSize: 6
[ 76577.887]     LinGreenFieldPosition: 5
[ 76577.887]     LinBlueMaskSize: 5
[ 76577.887]     LinBlueFieldPosition: 0
[ 76577.887]     LinRsvdMaskSize: 0
[ 76577.888]     LinRsvdFieldPosition: 0
[ 76577.888]     MaxPixelClock: 229500000
[ 76577.889] *Mode: 13e (640x400)
[ 76577.889]     ModeAttributes: 0x39f
[ 76577.889]     WinAAttributes: 0x7
[ 76577.889]     WinBAttributes: 0x0
[ 76577.889]     WinGranularity: 64
[ 76577.889]     WinSize: 64
[ 76577.889]     WinASegment: 0xa000
[ 76577.889]     WinBSegment: 0x0
[ 76577.889]     WinFuncPtr: 0xc000ada2
[ 76577.889]     BytesPerScanline: 2560
[ 76577.889]     XResolution: 640
[ 76577.889]     YResolution: 400
[ 76577.889]     XCharSize: 8
[ 76577.889]     YCharSize: 16
[ 76577.889]     NumberOfPlanes: 1
[ 76577.889]     BitsPerPixel: 32
[ 76577.890]     NumberOfBanks: 1
[ 76577.890]     MemoryModel: 6
[ 76577.890]     BankSize: 0
[ 76577.890]     NumberOfImages: 2
[ 76577.890]     RedMaskSize: 8
[ 76577.890]     RedFieldPosition: 16
[ 76577.890]     GreenMaskSize: 8
[ 76577.890]     GreenFieldPosition: 8
[ 76577.890]     BlueMaskSize: 8
[ 76577.890]     BlueFieldPosition: 0
[ 76577.890]     RsvdMaskSize: 8
[ 76577.890]     RsvdFieldPosition: 24
[ 76577.890]     DirectColorModeInfo: 0
[ 76577.890]     PhysBasePtr: 0xe0000000
[ 76577.890]     LinBytesPerScanLine: 2560
[ 76577.890]     BnkNumberOfImagePages: 2
[ 76577.890]     LinNumberOfImagePages: 2
[ 76577.890]     LinRedMaskSize: 8
[ 76577.890]     LinRedFieldPosition: 16
[ 76577.890]     LinGreenMaskSize: 8
[ 76577.890]     LinGreenFieldPosition: 8
[ 76577.890]     LinBlueMaskSize: 8
[ 76577.890]     LinBlueFieldPosition: 0
[ 76577.890]     LinRsvdMaskSize: 8
[ 76577.890]     LinRsvdFieldPosition: 24
[ 76577.890]     MaxPixelClock: 229500000
[ 76577.901] Mode: 145 (1600x1200)
[ 76577.901]     ModeAttributes: 0x39f
[ 76577.901]     WinAAttributes: 0x7
[ 76577.901]     WinBAttributes: 0x0
[ 76577.901]     WinGranularity: 64
[ 76577.901]     WinSize: 64
[ 76577.901]     WinASegment: 0xa000
[ 76577.901]     WinBSegment: 0x0
[ 76577.901]     WinFuncPtr: 0xc000ada2
[ 76577.901]     BytesPerScanline: 1600
[ 76577.901]     XResolution: 1600
[ 76577.901]     YResolution: 1200
[ 76577.901]     XCharSize: 8
[ 76577.901]     YCharSize: 16
[ 76577.901]     NumberOfPlanes: 1
[ 76577.901]     BitsPerPixel: 8
[ 76577.901]     NumberOfBanks: 1
[ 76577.901]     MemoryModel: 4
[ 76577.901]     BankSize: 0
[ 76577.901]     NumberOfImages: 1
[ 76577.901]     RedMaskSize: 0
[ 76577.901]     RedFieldPosition: 0
[ 76577.901]     GreenMaskSize: 0
[ 76577.901]     GreenFieldPosition: 0
[ 76577.901]     BlueMaskSize: 0
[ 76577.901]     BlueFieldPosition: 0
[ 76577.901]     RsvdMaskSize: 0
[ 76577.901]     RsvdFieldPosition: 0
[ 76577.901]     DirectColorModeInfo: 0
[ 76577.901]     PhysBasePtr: 0xe0000000
[ 76577.901]     LinBytesPerScanLine: 1600
[ 76577.901]     BnkNumberOfImagePages: 1
[ 76577.901]     LinNumberOfImagePages: 1
[ 76577.901]     LinRedMaskSize: 0
[ 76577.901]     LinRedFieldPosition: 0
[ 76577.901]     LinGreenMaskSize: 0
[ 76577.901]     LinGreenFieldPosition: 0
[ 76577.901]     LinBlueMaskSize: 0
[ 76577.902]     LinBlueFieldPosition: 0
[ 76577.902]     LinRsvdMaskSize: 0
[ 76577.902]     LinRsvdFieldPosition: 0
[ 76577.902]     MaxPixelClock: 229500000
[ 76577.903] Mode: 146 (1600x1200)
[ 76577.903]     ModeAttributes: 0x39f
[ 76577.903]     WinAAttributes: 0x7
[ 76577.903]     WinBAttributes: 0x0
[ 76577.903]     WinGranularity: 64
[ 76577.903]     WinSize: 64
[ 76577.903]     WinASegment: 0xa000
[ 76577.903]     WinBSegment: 0x0
[ 76577.903]     WinFuncPtr: 0xc000ada2
[ 76577.903]     BytesPerScanline: 3200
[ 76577.903]     XResolution: 1600
[ 76577.909]     YResolution: 1200
[ 76577.910]     XCharSize: 8
[ 76577.910]     YCharSize: 16
[ 76577.910]     NumberOfPlanes: 1
[ 76577.910]     BitsPerPixel: 16
[ 76577.910]     NumberOfBanks: 1
[ 76577.910]     MemoryModel: 6
[ 76577.910]     BankSize: 0
[ 76577.910]     NumberOfImages: 1
[ 76577.910]     RedMaskSize: 5
[ 76577.910]     RedFieldPosition: 11
[ 76577.910]     GreenMaskSize: 6
[ 76577.910]     GreenFieldPosition: 5
[ 76577.910]     BlueMaskSize: 5
[ 76577.910]     BlueFieldPosition: 0
[ 76577.910]     RsvdMaskSize: 0
[ 76577.910]     RsvdFieldPosition: 0
[ 76577.910]     DirectColorModeInfo: 0
[ 76577.910]     PhysBasePtr: 0xe0000000
[ 76577.910]     LinBytesPerScanLine: 3200
[ 76577.910]     BnkNumberOfImagePages: 1
[ 76577.910]     LinNumberOfImagePages: 1
[ 76577.910]     LinRedMaskSize: 5
[ 76577.910]     LinRedFieldPosition: 11
[ 76577.910]     LinGreenMaskSize: 6
[ 76577.910]     LinGreenFieldPosition: 5
[ 76577.910]     LinBlueMaskSize: 5
[ 76577.910]     LinBlueFieldPosition: 0
[ 76577.910]     LinRsvdMaskSize: 0
[ 76577.910]     LinRsvdFieldPosition: 0
[ 76577.910]     MaxPixelClock: 229500000
[ 76577.912] Mode: 147 (1400x1050)
[ 76577.912]     ModeAttributes: 0x39f
[ 76577.912]     WinAAttributes: 0x7
[ 76577.912]     WinBAttributes: 0x0
[ 76577.912]     WinGranularity: 64
[ 76577.912]     WinSize: 64
[ 76577.912]     WinASegment: 0xa000
[ 76577.912]     WinBSegment: 0x0
[ 76577.912]     WinFuncPtr: 0xc000ada2
[ 76577.912]     BytesPerScanline: 1400
[ 76577.912]     XResolution: 1400
[ 76577.912]     YResolution: 1050
[ 76577.915]     XCharSize: 8
[ 76577.915]     YCharSize: 14
[ 76577.915]     NumberOfPlanes: 1
[ 76577.915]     BitsPerPixel: 8
[ 76577.915]     NumberOfBanks: 1
[ 76577.915]     MemoryModel: 4
[ 76577.915]     BankSize: 0
[ 76577.915]     NumberOfImages: 1
[ 76577.915]     RedMaskSize: 0
[ 76577.915]     RedFieldPosition: 0
[ 76577.915]     GreenMaskSize: 0
[ 76577.915]     GreenFieldPosition: 0
[ 76577.915]     BlueMaskSize: 0
[ 76577.915]     BlueFieldPosition: 0
[ 76577.915]     RsvdMaskSize: 0
[ 76577.915]     RsvdFieldPosition: 0
[ 76577.915]     DirectColorModeInfo: 0
[ 76577.915]     PhysBasePtr: 0xe0000000
[ 76577.915]     LinBytesPerScanLine: 1400
[ 76577.915]     BnkNumberOfImagePages: 1
[ 76577.915]     LinNumberOfImagePages: 1
[ 76577.915]     LinRedMaskSize: 0
[ 76577.915]     LinRedFieldPosition: 0
[ 76577.915]     LinGreenMaskSize: 0
[ 76577.915]     LinGreenFieldPosition: 0
[ 76577.915]     LinBlueMaskSize: 0
[ 76577.915]     LinBlueFieldPosition: 0
[ 76577.915]     LinRsvdMaskSize: 0
[ 76577.915]     LinRsvdFieldPosition: 0
[ 76577.915]     MaxPixelClock: 229500000
[ 76577.917] Mode: 148 (1400x1050)
[ 76577.917]     ModeAttributes: 0x39f
[ 76577.917]     WinAAttributes: 0x7
[ 76577.917]     WinBAttributes: 0x0
[ 76577.917]     WinGranularity: 64
[ 76577.917]     WinSize: 64
[ 76577.917]     WinASegment: 0xa000
[ 76577.917]     WinBSegment: 0x0
[ 76577.917]     WinFuncPtr: 0xc000ada2
[ 76577.917]     BytesPerScanline: 2800
[ 76577.917]     XResolution: 1400
[ 76577.917]     YResolution: 1050
[ 76577.917]     XCharSize: 8
[ 76577.917]     YCharSize: 14
[ 76577.917]     NumberOfPlanes: 1
[ 76577.917]     BitsPerPixel: 16
[ 76577.917]     NumberOfBanks: 1
[ 76577.918]     MemoryModel: 6
[ 76577.918]     BankSize: 0
[ 76577.918]     NumberOfImages: 1
[ 76577.918]     RedMaskSize: 5
[ 76577.918]     RedFieldPosition: 11
[ 76577.918]     GreenMaskSize: 6
[ 76577.918]     GreenFieldPosition: 5
[ 76577.918]     BlueMaskSize: 5
[ 76577.918]     BlueFieldPosition: 0
[ 76577.918]     RsvdMaskSize: 0
[ 76577.918]     RsvdFieldPosition: 0
[ 76577.918]     DirectColorModeInfo: 0
[ 76577.918]     PhysBasePtr: 0xe0000000
[ 76577.918]     LinBytesPerScanLine: 2800
[ 76577.918]     BnkNumberOfImagePages: 1
[ 76577.918]     LinNumberOfImagePages: 1
[ 76577.918]     LinRedMaskSize: 5
[ 76577.918]     LinRedFieldPosition: 11
[ 76577.918]     LinGreenMaskSize: 6
[ 76577.918]     LinGreenFieldPosition: 5
[ 76577.918]     LinBlueMaskSize: 5
[ 76577.918]     LinBlueFieldPosition: 0
[ 76577.918]     LinRsvdMaskSize: 0
[ 76577.918]     LinRsvdFieldPosition: 0
[ 76577.918]     MaxPixelClock: 229500000
[ 76577.928] *Mode: 152 (2048x1536)
[ 76577.928]     ModeAttributes: 0x39f
[ 76577.928]     WinAAttributes: 0x7
[ 76577.928]     WinBAttributes: 0x0
[ 76577.928]     WinGranularity: 64
[ 76577.928]     WinSize: 64
[ 76577.928]     WinASegment: 0xa000
[ 76577.928]     WinBSegment: 0x0
[ 76577.928]     WinFuncPtr: 0xc000ada2
[ 76577.928]     BytesPerScanline: 8192
[ 76577.928]     XResolution: 2048
[ 76577.928]     YResolution: 1536
[ 76577.928]     XCharSize: 8
[ 76577.928]     YCharSize: 16
[ 76577.928]     NumberOfPlanes: 1
[ 76577.928]     BitsPerPixel: 32
[ 76577.928]     NumberOfBanks: 1
[ 76577.928]     MemoryModel: 6
[ 76577.929]     BankSize: 0
[ 76577.929]     NumberOfImages: 0
[ 76577.929]     RedMaskSize: 8
[ 76577.929]     RedFieldPosition: 16
[ 76577.929]     GreenMaskSize: 8
[ 76577.929]     GreenFieldPosition: 8
[ 76577.929]     BlueMaskSize: 8
[ 76577.929]     BlueFieldPosition: 0
[ 76577.929]     RsvdMaskSize: 8
[ 76577.929]     RsvdFieldPosition: 24
[ 76577.929]     DirectColorModeInfo: 0
[ 76577.929]     PhysBasePtr: 0xe0000000
[ 76577.929]     LinBytesPerScanLine: 8192
[ 76577.929]     BnkNumberOfImagePages: 0
[ 76577.929]     LinNumberOfImagePages: 0
[ 76577.929]     LinRedMaskSize: 8
[ 76577.929]     LinRedFieldPosition: 16
[ 76577.929]     LinGreenMaskSize: 8
[ 76577.929]     LinGreenFieldPosition: 8
[ 76577.929]     LinBlueMaskSize: 8
[ 76577.929]     LinBlueFieldPosition: 0
[ 76577.929]     LinRsvdMaskSize: 8
[ 76577.929]     LinRsvdFieldPosition: 24
[ 76577.929]     MaxPixelClock: 229500000
[ 76577.929] 
[ 76577.929] (II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
[ 76577.929] (II) VESA(0): <default monitor>: Using hsync range of 30.00-81.00 kHz
[ 76577.929] (II) VESA(0): <default monitor>: Using vrefresh range of 55.00-75.00 Hz
[ 76577.929] (II) VESA(0): <default monitor>: Using maximum pixel clock of 95.00 MHz
[ 76577.929] (WW) VESA(0): Unable to estimate virtual size
[ 76577.929] (II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
[ 76577.929] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[ 76577.932] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[ 76577.932] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[ 76577.932] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[ 76577.932] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[ 76577.932] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[ 76577.932] (**) VESA(0): *Built-in mode "1024x768"
[ 76577.932] (**) VESA(0): *Built-in mode "800x600"
[ 76577.932] (**) VESA(0): *Built-in mode "640x480"
[ 76577.932] (**) VESA(0): Display dimensions: (410, 230) mm
[ 76577.932] (**) VESA(0): DPI set to (63, 84)
[ 76577.932] (**) VESA(0): Using "Shadow Framebuffer"
[ 76577.932] (II) Loading sub module "shadow"
[ 76577.932] (II) LoadModule: "shadow"
[ 76577.933] (II) Loading /usr/lib/xorg/modules/libshadow.so
[ 76577.961] (II) Module shadow: vendor="X.Org Foundation"
[ 76577.961]     compiled for 1.11.3, module version = 1.1.0
[ 76577.961]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 76577.961] (II) Loading sub module "fb"
[ 76577.961] (II) LoadModule: "fb"
[ 76577.962] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 76577.979] (II) Module fb: vendor="X.Org Foundation"
[ 76577.979]     compiled for 1.11.3, module version = 1.0.0
[ 76577.979]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 76577.980] (==) Depth 24 pixmap format is 32 bpp
[ 76577.980] (II) Loading sub module "int10"
[ 76577.980] (II) LoadModule: "int10"
[ 76577.980] (II) Loading /usr/lib/xorg/modules/libint10.so
[ 76577.980] (II) Module int10: vendor="X.Org Foundation"
[ 76577.980]     compiled for 1.11.3, module version = 1.0.0
[ 76577.980]     ABI class: X.Org Video Driver, version 11.0
[ 76577.980] (II) VESA(0): initializing int10
[ 76578.000] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[ 76578.061] (II) VESA(0): VESA BIOS detected
[ 76578.061] (II) VESA(0): VESA VBE Version 3.0
[ 76578.061] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[ 76578.061] (II) VESA(0): VESA VBE OEM: NVIDIA
[ 76578.061] (II) VESA(0): VESA VBE OEM Software Rev: 4.23
[ 76578.061] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[ 76578.061] (II) VESA(0): VESA VBE OEM Product: NV17 Board
[ 76578.061] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A5
[ 76578.084] (II) VESA(0): virtual address = 0xb35dd000,
    physical address = 0xe0000000, size = 67108864
[ 76578.103] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[ 76578.345] (==) VESA(0): Default visual is TrueColor
[ 76578.345] (==) VESA(0): Backing store disabled
[ 76578.345] (==) VESA(0): DPMS enabled
[ 76578.345] (==) RandR enabled
[ 76578.345] (II) Initializing built-in extension Generic Event Extension
[ 76578.346] (II) Initializing built-in extension SHAPE
[ 76578.347] (II) Initializing built-in extension MIT-SHM
[ 76578.347] (II) Initializing built-in extension XInputExtension
[ 76578.347] (II) Initializing built-in extension XTEST
[ 76578.347] (II) Initializing built-in extension BIG-REQUESTS
[ 76578.347] (II) Initializing built-in extension SYNC
[ 76578.347] (II) Initializing built-in extension XKEYBOARD
[ 76578.347] (II) Initializing built-in extension XC-MISC
[ 76578.347] (II) Initializing built-in extension SECURITY
[ 76578.347] (II) Initializing built-in extension XINERAMA
[ 76578.347] (II) Initializing built-in extension XFIXES
[ 76578.347] (II) Initializing built-in extension RENDER
[ 76578.347] (II) Initializing built-in extension RANDR
[ 76578.347] (II) Initializing built-in extension COMPOSITE
[ 76578.347] (II) Initializing built-in extension DAMAGE
[ 76578.385] (II) AIGLX: Screen 0 is not DRI2 capable
[ 76578.385] (II) AIGLX: Screen 0 is not DRI capable
[ 76578.746] (II) AIGLX: Loaded and initialized swrast
[ 76578.746] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[ 76579.217] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 76579.261] (II) config/udev: Adding input device HID 0566:3002 (/dev/input/event0)
[ 76579.261] (**) HID 0566:3002: Applying InputClass "evdev keyboard catchall"
[ 76579.261] (II) LoadModule: "evdev"
[ 76579.262] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 76579.290] (II) Module evdev: vendor="X.Org Foundation"
[ 76579.290]     compiled for 1.11.3, module version = 2.7.0
[ 76579.290]     Module class: X.Org XInput Driver
[ 76579.290]     ABI class: X.Org XInput driver, version 16.0
[ 76579.290] (II) Using input driver 'evdev' for 'HID 0566:3002'
[ 76579.290] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 76579.290] (**) HID 0566:3002: always reports core events
[ 76579.290] (**) evdev: HID 0566:3002: Device: "/dev/input/event0"
[ 76579.290] (--) evdev: HID 0566:3002: Vendor 0x566 Product 0x3002
[ 76579.291] (--) evdev: HID 0566:3002: Found keys
[ 76579.291] (II) evdev: HID 0566:3002: Configuring as keyboard
[ 76579.291] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1:1.0/input/input0/event0"
[ 76579.291] (II) XINPUT: Adding extended input device "HID 0566:3002" (type: KEYBOARD, id 6)
[ 76579.291] (**) Option "xkb_rules" "evdev"
[ 76579.291] (**) Option "xkb_model" "pc105"
[ 76579.291] (**) Option "xkb_layout" "us"
[ 76579.292] (II) config/udev: Adding input device HID 0566:3002 (/dev/input/event1)
[ 76579.292] (**) HID 0566:3002: Applying InputClass "evdev keyboard catchall"
[ 76579.292] (II) Using input driver 'evdev' for 'HID 0566:3002'
[ 76579.292] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 76579.292] (**) HID 0566:3002: always reports core events
[ 76579.292] (**) evdev: HID 0566:3002: Device: "/dev/input/event1"
[ 76579.292] (--) evdev: HID 0566:3002: Vendor 0x566 Product 0x3002
[ 76579.292] (--) evdev: HID 0566:3002: Found keys
[ 76579.292] (II) evdev: HID 0566:3002: Configuring as keyboard
[ 76579.292] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1:1.1/input/input1/event1"
[ 76579.292] (II) XINPUT: Adding extended input device "HID 0566:3002" (type: KEYBOARD, id 7)
[ 76579.292] (**) Option "xkb_rules" "evdev"
[ 76579.292] (**) Option "xkb_model" "pc105"
[ 76579.292] (**) Option "xkb_layout" "us"
[ 76579.293] (II) config/udev: Adding input device Microsoft Microsoft Wheel Mouse Optical® (/dev/input/event2)
[ 76579.293] (**) Microsoft Microsoft Wheel Mouse Optical®: Applying InputClass "evdev pointer catchall"
[ 76579.293] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wheel Mouse Optical®'
[ 76579.294] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 76579.294] (**) Microsoft Microsoft Wheel Mouse Optical®: always reports core events
[ 76579.294] (**) evdev: Microsoft Microsoft Wheel Mouse Optical®: Device: "/dev/input/event2"
[ 76579.294] (--) evdev: Microsoft Microsoft Wheel Mouse Optical®: Vendor 0x45e Product 0x40
[ 76579.294] (--) evdev: Microsoft Microsoft Wheel Mouse Optical®: Found 3 mouse buttons
[ 76579.294] (--) evdev: Microsoft Microsoft Wheel Mouse Optical®: Found scroll wheel(s)
[ 76579.297] (--) evdev: Microsoft Microsoft Wheel Mouse Optical®: Found relative axes
[ 76579.297] (--) evdev: Microsoft Microsoft Wheel Mouse Optical®: Found x and y relative axes
[ 76579.297] (II) evdev: Microsoft Microsoft Wheel Mouse Optical®: Configuring as mouse
[ 76579.297] (II) evdev: Microsoft Microsoft Wheel Mouse Optical®: Adding scrollwheel support
[ 76579.297] (**) evdev: Microsoft Microsoft Wheel Mouse Optical®: YAxisMapping: buttons 4 and 5
[ 76579.297] (**) evdev: Microsoft Microsoft Wheel Mouse Optical®: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 76579.297] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.3/1-1.3:1.0/input/input2/event2"
[ 76579.297] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wheel Mouse Optical®" (type: MOUSE, id 8)
[ 76579.298] (II) evdev: Microsoft Microsoft Wheel Mouse Optical®: initialized for relative axes.
[ 76579.298] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) keeping acceleration scheme 1
[ 76579.298] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration profile 0
[ 76579.298] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration factor: 2.000
[ 76579.298] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration threshold: 4
[ 76579.299] (II) config/udev: Adding input device Microsoft Microsoft Wheel Mouse Optical® (/dev/input/mouse0)
[ 76579.299] (II) No input driver specified, ignoring this device.
[ 76579.299] (II) This device may have been added with another device file.

```

---

