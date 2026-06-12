---
title: "Boot splash - No GDM startup on vty7"
date: 2010-12-14
forum: Desktop Environments
---

### Post by entr0py on 2010-12-14
Hi,

I've seen similar posts but nothing that's been able to solve my issue.

System
Linux qbit 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Desktop
Gnome

Issue
Upon boot I can see the Ubuntu splash with the 6 white progress dots. No GDM or X11 session is started automatically with the progress screen simply remaining on display.

Temporary Solution
Stop GDM on vty7 and start it on vty1 or anywhere else for that matter - just not vty7 as this won't work.

ctrl+alt+1
sudo /etc/init.d/gdm stop && startx

Possible solutions
/boot/grub/grub.cfg (added "i915.modeset=1")
linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=0ce8b2ed-ffcd-4dcc-8bbe-57e8b9a1726a ro   quiet splash i915.modeset=1

X11
[attached]

Anyone have any ideas what's doing? ;) xorg seems to recognize the chipset Intel 915 and loads the intel as well as vesa drivers...

---

### Post by entr0py on 2010-12-14
root@qbit:/var/log# cat Xorg.0.log
[    19.555] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    19.555] X Protocol Version 11, Revision 0
[    19.555] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    19.555] Current Operating System: Linux qbit 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64
[    19.555] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=0ce8b2ed-ffcd-4dcc-8bbe-57e8b9a1726a ro quiet splash i915.modeset=1
[    19.555] Build Date: 16 September 2010  06:18:41PM
[    19.555] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.555] Current version of pixman: 0.18.4
[    19.555] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    19.555] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.556] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 15 11:58:47 2010
[    19.556] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.556] (==) No Layout section.  Using the first Screen section.
[    19.556] (==) No screen section available. Using defaults.
[    19.556] (**) |-->Screen "Default Screen Section" (0)
[    19.556] (**) |   |-->Monitor "<default monitor>"
[    19.556] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    19.556] (==) Automatically adding devices
[    19.556] (==) Automatically enabling devices
[    19.556] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.556] 	Entry deleted from font path.
[    19.556] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.556] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.556] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.556] (II) Loader magic: 0x7d0200
[    19.556] (II) Module ABI versions:
[    19.556] 	X.Org ANSI C Emulation: 0.4
[    19.556] 	X.Org Video Driver: 8.0
[    19.556] 	X.Org XInput driver : 11.0
[    19.556] 	X.Org Server Extension : 4.0
[    19.557] (--) PCI:*(0:0:2:0) 8086:2a42:17aa:20e4 rev 7, Mem @ 0xf2000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[    19.557] (--) PCI: (0:0:2:1) 8086:2a43:17aa:20e4 rev 7, Mem @ 0xf2400000/1048576
[    19.557] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.557] (II) LoadModule: "extmod"
[    19.558] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.558] (II) Module extmod: vendor="X.Org Foundation"
[    19.558] 	compiled for 1.9.0, module version = 1.0.0
[    19.558] 	Module class: X.Org Server Extension
[    19.558] 	ABI class: X.Org Server Extension, version 4.0
[    19.558] (II) Loading extension MIT-SCREEN-SAVER
[    19.558] (II) Loading extension XFree86-VidModeExtension
[    19.558] (II) Loading extension XFree86-DGA
[    19.558] (II) Loading extension DPMS
[    19.558] (II) Loading extension XVideo
[    19.558] (II) Loading extension XVideo-MotionCompensation
[    19.558] (II) Loading extension X-Resource
[    19.558] (II) LoadModule: "dbe"
[    19.558] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.558] (II) Module dbe: vendor="X.Org Foundation"
[    19.558] 	compiled for 1.9.0, module version = 1.0.0
[    19.558] 	Module class: X.Org Server Extension
[    19.558] 	ABI class: X.Org Server Extension, version 4.0
[    19.558] (II) Loading extension DOUBLE-BUFFER
[    19.558] (II) LoadModule: "glx"
[    19.559] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.559] (II) Module glx: vendor="X.Org Foundation"
[    19.559] 	compiled for 1.9.0, module version = 1.0.0
[    19.559] 	ABI class: X.Org Server Extension, version 4.0
[    19.559] (==) AIGLX enabled
[    19.559] (II) Loading extension GLX
[    19.559] (II) LoadModule: "record"
[    19.559] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.559] (II) Module record: vendor="X.Org Foundation"
[    19.559] 	compiled for 1.9.0, module version = 1.13.0
[    19.559] 	Module class: X.Org Server Extension
[    19.559] 	ABI class: X.Org Server Extension, version 4.0
[    19.559] (II) Loading extension RECORD
[    19.559] (II) LoadModule: "dri"
[    19.560] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.560] (II) Module dri: vendor="X.Org Foundation"
[    19.560] 	compiled for 1.9.0, module version = 1.0.0
[    19.560] 	ABI class: X.Org Server Extension, version 4.0
[    19.560] (II) Loading extension XFree86-DRI
[    19.560] (II) LoadModule: "dri2"
[    19.560] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.560] (II) Module dri2: vendor="X.Org Foundation"
[    19.560] 	compiled for 1.9.0, module version = 1.2.0
[    19.560] 	ABI class: X.Org Server Extension, version 4.0
[    19.560] (II) Loading extension DRI2
[    19.560] (==) Matched intel as autoconfigured driver 0
[    19.560] (==) Matched vesa as autoconfigured driver 1
[    19.560] (==) Matched fbdev as autoconfigured driver 2
[    19.560] (==) Assigned the driver to the xf86ConfigLayout
[    19.560] (II) LoadModule: "intel"
[    19.560] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.560] (II) Module intel: vendor="X.Org Foundation"
[    19.560] 	compiled for 1.9.0, module version = 2.12.0
[    19.560] 	Module class: X.Org Video Driver
[    19.560] 	ABI class: X.Org Video Driver, version 8.0
[    19.560] (II) LoadModule: "vesa"
[    19.561] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.561] (II) Module vesa: vendor="X.Org Foundation"
[    19.561] 	compiled for 1.8.99.905, module version = 2.3.0
[    19.561] 	Module class: X.Org Video Driver
[    19.561] 	ABI class: X.Org Video Driver, version 8.0
[    19.561] (II) LoadModule: "fbdev"
[    19.561] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.561] (II) Module fbdev: vendor="X.Org Foundation"
[    19.561] 	compiled for 1.8.99.905, module version = 0.4.2
[    19.561] 	ABI class: X.Org Video Driver, version 8.0
[    19.561] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    19.561] (II) VESA: driver for VESA chipsets: vesa
[    19.561] (II) FBDEV: driver for framebuffer: fbdev
[    19.561] (--) using VT number 8

[    19.564] (WW) Falling back to old probe method for vesa
[    19.564] (WW) Falling back to old probe method for fbdev
[    19.564] (II) Loading sub module "fbdevhw"
[    19.564] (II) LoadModule: "fbdevhw"
[    19.565] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.565] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.565] 	compiled for 1.9.0, module version = 0.0.2
[    19.565] 	ABI class: X.Org Video Driver, version 8.0
[    19.566] drmOpenDevice: node name is /dev/dri/card0
[    19.566] drmOpenDevice: open result is 9, (OK)
[    19.566] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    19.566] drmOpenDevice: node name is /dev/dri/card0
[    19.566] drmOpenDevice: open result is 9, (OK)
[    19.566] drmOpenByBusid: drmOpenMinor returns 9
[    19.566] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    19.566] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    19.566] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    19.566] (==) intel(0): RGB weight 888
[    19.566] (==) intel(0): Default visual is TrueColor
[    19.566] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    19.566] (--) intel(0): Chipset: "GM45"
[    19.566] (==) intel(0): video overlay key set to 0x101fe
[    19.600] (II) intel(0): Output VGA1 has no monitor section
[    19.600] (II) intel(0): Output LVDS1 has no monitor section
[    19.600] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    19.609] (II) intel(0): Output HDMI1 has no monitor section
[    19.609] (II) intel(0): Output DP1 has no monitor section
[    19.618] (II) intel(0): Output HDMI2 has no monitor section
[    19.618] (II) intel(0): Output DP2 has no monitor section
[    19.619] (II) intel(0): Output DP3 has no monitor section
[    19.650] (II) intel(0): EDID for output VGA1
[    19.650] (II) intel(0): EDID for output LVDS1
[    19.650] (II) intel(0): Manufacturer: LEN  Model: 4036  Serial#: 0
[    19.650] (II) intel(0): Year: 2009  Week: 51
[    19.650] (II) intel(0): EDID Version: 1.3
[    19.650] (II) intel(0): Digital Display Input
[    19.650] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    19.650] (II) intel(0): Gamma: 2.20
[    19.650] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[    19.650] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    19.650] (II) intel(0): First detailed timing is preferred mode
[    19.650] (II) intel(0): redX: 0.577 redY: 0.338   greenX: 0.310 greenY: 0.563
[    19.650] (II) intel(0): blueX: 0.158 blueY: 0.157   whiteX: 0.313 whiteY: 0.329
[    19.650] (II) intel(0): Manufacturer's mask: 0
[    19.650] (II) intel(0): Supported detailed timing:
[    19.650] (II) intel(0): clock: 101.2 MHz   Image Size:  304 x 190 mm
[    19.650] (II) intel(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1820 h_border: 0
[    19.650] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    19.650] (II) intel(0): Supported detailed timing:
[    19.650] (II) intel(0): clock: 82.0 MHz   Image Size:  304 x 190 mm
[    19.650] (II) intel(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1770 h_border: 0
[    19.650] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    19.650] (II) intel(0): Unknown vendor-specific block f
[    19.650] (II) intel(0):  LT141DEQ8B00
[    19.650] (II) intel(0): EDID (in hex):
[    19.650] (II) intel(0): 	00ffffffffffff0030ae364000000000
[    19.650] (II) intel(0): 	33130103801e1378eae59593564f9028
[    19.650] (II) intel(0): 	28505400000001010101010101010101
[    19.650] (II) intel(0): 	0101010101018827a07c51841a303020
[    19.650] (II) intel(0): 	360030be100000180820a04a51841a30
[    19.650] (II) intel(0): 	3020360030be100000180000000f0095
[    19.650] (II) intel(0): 	0a32950a281e090030640811000000fe
[    19.650] (II) intel(0): 	004c54313431444551384230300a004f
[    19.650] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    19.650] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    19.650] (II) intel(0): Printing probed modes for output LVDS1
[    19.650] (II) intel(0): Modeline "1440x900"x60.0  101.20  1440 1488 1520 1820  900 903 909 926 -hsync -vsync (55.6 kHz)
[    19.650] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    19.650] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    19.650] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    19.650] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    19.650] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.650] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.650] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.650] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.659] (II) intel(0): EDID for output HDMI1
[    19.659] (II) intel(0): EDID for output DP1
[    19.668] (II) intel(0): EDID for output HDMI2
[    19.668] (II) intel(0): EDID for output DP2
[    19.669] (II) intel(0): EDID for output DP3
[    19.669] (II) intel(0): Output VGA1 disconnected
[    19.669] (II) intel(0): Output LVDS1 connected
[    19.669] (II) intel(0): Output HDMI1 disconnected
[    19.669] (II) intel(0): Output DP1 disconnected
[    19.669] (II) intel(0): Output HDMI2 disconnected
[    19.669] (II) intel(0): Output DP2 disconnected
[    19.669] (II) intel(0): Output DP3 disconnected
[    19.669] (II) intel(0): Using exact sizes for initial modes
[    19.669] (II) intel(0): Output LVDS1 using initial mode 1440x900
[    19.669] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    19.669] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    19.669] (==) intel(0): DPI set to (96, 96)
[    19.669] (II) Loading sub module "fb"
[    19.669] (II) LoadModule: "fb"
[    19.670] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.670] (II) Module fb: vendor="X.Org Foundation"
[    19.670] 	compiled for 1.9.0, module version = 1.0.0
[    19.670] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.670] (II) UnloadModule: "vesa"
[    19.670] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.670] (II) UnloadModule: "fbdev"
[    19.670] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.670] (II) UnloadModule: "fbdevhw"
[    19.670] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    19.670] (==) Depth 24 pixmap format is 32 bpp
[    19.670] (II) intel(0): [DRI2] Setup complete
[    19.670] (II) intel(0): [DRI2]   DRI driver: i965
[    19.670] (**) intel(0): Tiling enabled
[    19.670] (**) intel(0): SwapBuffers wait enabled
[    19.670] (==) intel(0): VideoRam: 262144 KB
[    19.670] (II) intel(0): Allocated new frame buffer 1472x900 stride 6144, tiled
[    19.678] (II) UXA(0): Driver registered support for the following operations:
[    19.678] (II)         solid
[    19.678] (II)         copy
[    19.678] (II)         composite (RENDER acceleration)
[    19.678] (II)         put_image
[    19.678] (II)         get_image
[    19.678] (==) intel(0): Backing store disabled
[    19.678] (==) intel(0): Silken mouse enabled
[    19.678] (II) intel(0): Initializing HW Cursor
[    19.721] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.723] (==) intel(0): DPMS enabled
[    19.723] (==) intel(0): Intel XvMC decoder enabled
[    19.723] (II) intel(0): Set up textured video
[    19.723] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    19.723] (II) intel(0): direct rendering: DRI2 Enabled
[    19.723] (--) RandR disabled
[    19.723] (II) Initializing built-in extension Generic Event Extension
[    19.723] (II) Initializing built-in extension SHAPE
[    19.724] (II) Initializing built-in extension MIT-SHM
[    19.724] (II) Initializing built-in extension XInputExtension
[    19.724] (II) Initializing built-in extension XTEST
[    19.724] (II) Initializing built-in extension BIG-REQUESTS
[    19.724] (II) Initializing built-in extension SYNC
[    19.724] (II) Initializing built-in extension XKEYBOARD
[    19.724] (II) Initializing built-in extension XC-MISC
[    19.724] (II) Initializing built-in extension SECURITY
[    19.724] (II) Initializing built-in extension XINERAMA
[    19.724] (II) Initializing built-in extension XFIXES
[    19.724] (II) Initializing built-in extension RENDER
[    19.724] (II) Initializing built-in extension RANDR
[    19.724] (II) Initializing built-in extension COMPOSITE
[    19.724] (II) Initializing built-in extension DAMAGE
[    19.724] (II) Initializing built-in extension GESTURE
[    19.730] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.730] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.730] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.730] (II) AIGLX: enabled GLX_SGI_make_current_read
[    19.730] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.730] (II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
[    19.730] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.730] (II) intel(0): Setting screen physical size to 381 x 238
[    19.743] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.776] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.776] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.776] (II) LoadModule: "evdev"
[    19.776] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.776] (II) Module evdev: vendor="X.Org Foundation"
[    19.776] 	compiled for 1.9.0, module version = 2.3.2
[    19.776] 	Module class: X.Org XInput Driver
[    19.776] 	ABI class: X.Org XInput driver, version 11.0
[    19.776] (**) Power Button: always reports core events
[    19.776] (**) Power Button: Device: "/dev/input/event2"
[    19.800] (II) Power Button: Found keys
[    19.800] (II) Power Button: Configuring as keyboard
[    19.800] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.800] (**) Option "xkb_rules" "evdev"
[    19.800] (**) Option "xkb_model" "pc105"
[    19.800] (**) Option "xkb_layout" "us"
[    19.800] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    19.800] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.800] (**) Video Bus: always reports core events
[    19.800] (**) Video Bus: Device: "/dev/input/event4"
[    19.830] (II) Video Bus: Found keys
[    19.830] (II) Video Bus: Configuring as keyboard
[    19.830] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    19.830] (**) Option "xkb_rules" "evdev"
[    19.830] (**) Option "xkb_model" "pc105"
[    19.830] (**) Option "xkb_layout" "us"
[    19.831] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    19.831] (II) No input driver/identifier specified (ignoring)
[    19.831] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    19.831] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.831] (**) Sleep Button: always reports core events
[    19.832] (**) Sleep Button: Device: "/dev/input/event1"
[    19.860] (II) Sleep Button: Found keys
[    19.860] (II) Sleep Button: Configuring as keyboard
[    19.860] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    19.860] (**) Option "xkb_rules" "evdev"
[    19.860] (**) Option "xkb_model" "pc105"
[    19.860] (**) Option "xkb_layout" "us"
[    19.862] (II) config/udev: Adding input device Integrated Camera (/dev/input/event5)
[    19.862] (**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
[    19.862] (**) Integrated Camera: always reports core events
[    19.862] (**) Integrated Camera: Device: "/dev/input/event5"
[    19.900] (II) Integrated Camera: Found keys
[    19.900] (II) Integrated Camera: Configuring as keyboard
[    19.900] (II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
[    19.900] (**) Option "xkb_rules" "evdev"
[    19.900] (**) Option "xkb_model" "pc105"
[    19.900] (**) Option "xkb_layout" "us"
[    19.903] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    19.903] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.903] (**) AT Translated Set 2 keyboard: always reports core events
[    19.903] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    19.940] (II) AT Translated Set 2 keyboard: Found keys
[    19.940] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.940] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.940] (**) Option "xkb_rules" "evdev"
[    19.940] (**) Option "xkb_model" "pc105"
[    19.940] (**) Option "xkb_layout" "us"
[    19.940] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    19.940] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    19.940] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    19.940] (II) LoadModule: "synaptics"
[    19.940] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.940] (II) Module synaptics: vendor="X.Org Foundation"
[    19.940] 	compiled for 1.9.0, module version = 1.2.2
[    19.940] 	Module class: X.Org XInput Driver
[    19.940] 	ABI class: X.Org XInput driver, version 11.0
[    19.940] (II) Synaptics touchpad driver version 1.2.2
[    19.940] (**) Option "Device" "/dev/input/event7"
[    19.961] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[    19.961] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4820
[    19.961] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    19.961] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    19.961] (II) SynPS/2 Synaptics TouchPad: buttons: left right middle
[    19.970] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.970] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.981] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    19.981] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    19.981] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    19.981] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    19.981] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    19.990] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.990] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    19.990] (II) No input driver/identifier specified (ignoring)
[    19.990] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event8)
[    19.990] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    19.990] (**) TPPS/2 IBM TrackPoint: always reports core events
[    19.990] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event8"
[    19.990] (II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    19.990] (II) TPPS/2 IBM TrackPoint: Found relative axes
[    19.990] (II) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    19.990] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    19.990] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    19.990] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.990] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    19.990] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    19.991] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    19.991] (II) No input driver/identifier specified (ignoring)
[    19.991] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
[    19.991] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    19.991] (**) ThinkPad Extra Buttons: always reports core events
[    19.991] (**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
[    19.991] (II) ThinkPad Extra Buttons: Found keys
[    19.991] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    19.991] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    19.991] (**) Option "xkb_rules" "evdev"
[    19.991] (**) Option "xkb_model" "pc105"
[    19.991] (**) Option "xkb_layout" "us"
[    20.461] (II) intel(0): EDID vendor "LEN", prod id 16438
[    20.461] (II) intel(0): Printing DDC gathered Modelines:
[    20.461] (II) intel(0): Modeline "1440x900"x0.0  101.20  1440 1488 1520 1820  900 903 909 926 -hsync -vsync (55.6 kHz)
[    20.461] (II) intel(0): Modeline "1440x900"x0.0   82.00  1440 1488 1520 1770  900 903 909 926 -hsync -vsync (46.3 kHz)
[    20.520] (II) intel(0): EDID vendor "LEN", prod id 16438
[    20.520] (II) intel(0): Printing DDC gathered Modelines:
[    20.520] (II) intel(0): Modeline "1440x900"x0.0  101.20  1440 1488 1520 1820  900 903 909 926 -hsync -vsync (55.6 kHz)
[    20.520] (II) intel(0): Modeline "1440x900"x0.0   82.00  1440 1488 1520 1770  900 903 909 926 -hsync -vsync (46.3 kHz)
[    20.580] (II) intel(0): EDID vendor "LEN", prod id 16438
[    20.580] (II) intel(0): Printing DDC gathered Modelines:
[    20.580] (II) intel(0): Modeline "1440x900"x0.0  101.20  1440 1488 1520 1820  900 903 909 926 -hsync -vsync (55.6 kHz)
[    20.580] (II) intel(0): Modeline "1440x900"x0.0   82.00  1440 1488 1520 1770  900 903 909 926 -hsync -vsync (46.3 kHz)
[    21.821] (II) intel(0): EDID vendor "LEN", prod id 16438
[    21.821] (II) intel(0): Printing DDC gathered Modelines:
[    21.821] (II) intel(0): Modeline "1440x900"x0.0  101.20  1440 1488 1520 1820  900 903 909 926 -hsync -vsync (55.6 kHz)
[    21.821] (II) intel(0): Modeline "1440x900"x0.0   82.00  1440 1488 1520 1770  900 903 909 926 -hsync -vsync (46.3 kHz)
[    23.457] (II) config/udev: Adding input device ThinkPad Bluetooth Laser Mouse (/dev/input/event9)
[    23.457] (**) ThinkPad Bluetooth Laser Mouse: Applying InputClass "evdev pointer catchall"
[    23.457] (**) ThinkPad Bluetooth Laser Mouse: always reports core events
[    23.457] (**) ThinkPad Bluetooth Laser Mouse: Device: "/dev/input/event9"
[    23.471] (II) ThinkPad Bluetooth Laser Mouse: Found 9 mouse buttons
[    23.471] (II) ThinkPad Bluetooth Laser Mouse: Found scroll wheel(s)
[    23.471] (II) ThinkPad Bluetooth Laser Mouse: Found relative axes
[    23.471] (II) ThinkPad Bluetooth Laser Mouse: Found x and y relative axes
[    23.471] (II) ThinkPad Bluetooth Laser Mouse: Found absolute axes
[    23.471] (II) evdev-grail: failed to open grail, no gesture support
[    23.471] (II) ThinkPad Bluetooth Laser Mouse: Configuring as mouse
[    23.471] (**) ThinkPad Bluetooth Laser Mouse: YAxisMapping: buttons 4 and 5
[    23.471] (**) ThinkPad Bluetooth Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.471] (II) XINPUT: Adding extended input device "ThinkPad Bluetooth Laser Mouse" (type: MOUSE)
[    23.471] (II) ThinkPad Bluetooth Laser Mouse: initialized for relative axes.
[    23.471] (WW) ThinkPad Bluetooth Laser Mouse: ignoring absolute axes.
[    23.471] (II) config/udev: Adding input device ThinkPad Bluetooth Laser Mouse (/dev/input/mouse2)
[    23.471] (II) No input driver/identifier specified (ignoring)
[    26.660] (II) intel(0): EDID vendor "LEN", prod id 16438
[    26.660] (II) intel(0): Printing DDC gathered Modelines:
[    26.660] (II) intel(0): Modeline "1440x900"x0.0  101.20  1440 1488 1520 1820  900 903 909 926 -hsync -vsync (55.6 kHz)
[    26.660] (II) intel(0): Modeline "1440x900"x0.0   82.00  1440 1488 1520 1770  900 903 909 926 -hsync -vsync (46.3 kHz)

---

