---
title: "extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2015-09-07
forum: Desktop Environments
---

### Post by Kilarin on 2015-09-07
I'm guessing that some standard update I took last week, possibly something to my nvidia drivers?  killed opengl on my computer.  At least I THINK thats what happened.  Graphics and drivers are NOT my area of expertise.  I could use some help.
My computer:
HP Pavilion a1600n AMD Athlon 64 X2 Dual core Processor 3800+ 2.00 GHz 2965MB of Ram,  NVIDIA GeForce 6150LE graphics card
I'm running Xubuntu 14.04.3 

First time I noticed the problem was probably Friday afternoon or Saturday night when I was trying to play Minetest, which worked just fine before, but now I get:
```
$ minetest
Xlib:  extension "GLX" missing on display ":0.0".
2015-09-06 21:31:19: ACTION[Main]: Irrlicht: No GLX support available. OpenGL driver will not work.
2015-09-06 21:31:19: ERROR[Main]: Irrlicht: Fatal error, could not get visual.
2015-09-06 21:31:19: ERROR[Main]: Could not initialize game engine.
```

I backed up several versions in Minetest and confirmed that it wasn't anything to do with Minetest.  glxinfo shows the following:

```
$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

Which, if I'm understanding correctly, looks like openGL isn't there at all?

my Xorg.0.log:
```
[  1072.118]
X.Org X Server 1.15.1
Release Date: 2014-04-13
[  1072.118] X Protocol Version 11, Revision 0
[  1072.118] Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu
[  1072.118] Current Operating System: Linux Malacandra 3.13.0-63-generic #103-Ubuntu SMP Fri Aug 14 21:43:30 UTC 2015 i686
[  1072.118] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-63-generic root=UUID=8a188181-9beb-497f-ac0e-027f336571e6 ro quiet splash
[  1072.118] Build Date: 12 February 2015  02:49:46PM
[  1072.118] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support)
[  1072.118] Current version of pixman: 0.30.2
[  1072.118] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  1072.118] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1072.118] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep  7 06:55:13 2015
[  1072.213] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1072.230] (==) No Layout section.  Using the first Screen section.
[  1072.230] (==) No screen section available. Using defaults.
[  1072.230] (**) |-->Screen "Default Screen Section" (0)
[  1072.230] (**) |   |-->Monitor "<default monitor>"
[  1072.230] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1072.230] (==) Automatically adding devices
[  1072.231] (==) Automatically enabling devices
[  1072.231] (==) Automatically adding GPU devices
[  1072.231] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1072.231] 	Entry deleted from font path.
[  1072.231] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1072.231] 	Entry deleted from font path.
[  1072.231] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1072.231] 	Entry deleted from font path.
[  1072.231] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1072.231] 	Entry deleted from font path.
[  1072.231] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1072.231] 	Entry deleted from font path.
[  1072.231] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[  1072.231] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1072.231] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1072.231] (II) Loader magic: 0xb76f86c0
[  1072.231] (II) Module ABI versions:
[  1072.231] 	X.Org ANSI C Emulation: 0.4
[  1072.231] 	X.Org Video Driver: 15.0
[  1072.231] 	X.Org XInput driver : 20.0
[  1072.231] 	X.Org Server Extension : 8.0
[  1072.233] (--) PCI:*(0:0:5:0) 10de:0241:103c:2a34 rev 162, Mem @ 0xfc000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
[  1072.233] Initializing built-in extension Generic Event Extension
[  1072.233] Initializing built-in extension SHAPE
[  1072.233] Initializing built-in extension MIT-SHM
[  1072.233] Initializing built-in extension XInputExtension
[  1072.233] Initializing built-in extension XTEST
[  1072.233] Initializing built-in extension BIG-REQUESTS
[  1072.233] Initializing built-in extension SYNC
[  1072.233] Initializing built-in extension XKEYBOARD
[  1072.233] Initializing built-in extension XC-MISC
[  1072.233] Initializing built-in extension SECURITY
[  1072.233] Initializing built-in extension XINERAMA
[  1072.233] Initializing built-in extension XFIXES
[  1072.233] Initializing built-in extension RENDER
[  1072.233] Initializing built-in extension RANDR
[  1072.233] Initializing built-in extension COMPOSITE
[  1072.233] Initializing built-in extension DAMAGE
[  1072.233] Initializing built-in extension MIT-SCREEN-SAVER
[  1072.233] Initializing built-in extension DOUBLE-BUFFER
[  1072.233] Initializing built-in extension RECORD
[  1072.233] Initializing built-in extension DPMS
[  1072.233] Initializing built-in extension Present
[  1072.233] Initializing built-in extension DRI3
[  1072.233] Initializing built-in extension X-Resource
[  1072.233] Initializing built-in extension XVideo
[  1072.233] Initializing built-in extension XVideo-MotionCompensation
[  1072.233] Initializing built-in extension SELinux
[  1072.233] Initializing built-in extension XFree86-VidModeExtension
[  1072.233] Initializing built-in extension XFree86-DGA
[  1072.233] Initializing built-in extension XFree86-DRI
[  1072.233] Initializing built-in extension DRI2
[  1072.233] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[  1072.233] (II) "glx" will be loaded by default.
[  1072.233] (WW) "xmir" is not to be loaded by default. Skipping.
[  1072.233] (II) LoadModule: "glx"
[  1072.234] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[  1072.440] (II) Module glx: vendor="NVIDIA Corporation"
[  1072.441] 	compiled for 4.0.2, module version = 1.0.0
[  1072.441] 	Module class: X.Org Server Extension
[  1072.441] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:21:57 PST 2014
[  1072.441] Loading extension GLX
[  1072.441] (==) Matched nvidia as autoconfigured driver 0
[  1072.441] (==) Matched nouveau as autoconfigured driver 1
[  1072.441] (==) Matched modesetting as autoconfigured driver 2
[  1072.441] (==) Matched fbdev as autoconfigured driver 3
[  1072.441] (==) Matched vesa as autoconfigured driver 4
[  1072.441] (==) Assigned the driver to the xf86ConfigLayout
[  1072.441] (II) LoadModule: "nvidia"
[  1072.441] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1072.442] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1072.442] 	compiled for 4.0.2, module version = 1.0.0
[  1072.442] 	Module class: X.Org Video Driver
[  1072.446] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  1072.446] (EE) NVIDIA:     system's kernel log for additional error messages.
[  1072.446] (II) UnloadModule: "nvidia"
[  1072.446] (II) Unloading nvidia
[  1072.447] (EE) Failed to load module "nvidia" (module-specific error, 0)
[  1072.447] (II) LoadModule: "nouveau"
[  1072.447] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1072.458] (II) Module nouveau: vendor="X.Org Foundation"
[  1072.458] 	compiled for 1.15.0, module version = 1.0.10
[  1072.458] 	Module class: X.Org Video Driver
[  1072.458] 	ABI class: X.Org Video Driver, version 15.0
[  1072.458] (II) LoadModule: "modesetting"
[  1072.459] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1072.459] (II) Module modesetting: vendor="X.Org Foundation"
[  1072.459] 	compiled for 1.15.0, module version = 0.8.1
[  1072.459] 	Module class: X.Org Video Driver
[  1072.459] 	ABI class: X.Org Video Driver, version 15.0
[  1072.459] (II) LoadModule: "fbdev"
[  1072.459] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1072.459] (II) Module fbdev: vendor="X.Org Foundation"
[  1072.459] 	compiled for 1.15.0, module version = 0.4.4
[  1072.459] 	Module class: X.Org Video Driver
[  1072.459] 	ABI class: X.Org Video Driver, version 15.0
[  1072.459] (II) LoadModule: "vesa"
[  1072.459] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1072.459] (II) Module vesa: vendor="X.Org Foundation"
[  1072.459] 	compiled for 1.15.0, module version = 2.3.3
[  1072.460] 	Module class: X.Org Video Driver
[  1072.460] 	ABI class: X.Org Video Driver, version 15.0
[  1072.460] (==) Matched nvidia as autoconfigured driver 0
[  1072.460] (==) Matched nouveau as autoconfigured driver 1
[  1072.460] (==) Matched modesetting as autoconfigured driver 2
[  1072.460] (==) Matched fbdev as autoconfigured driver 3
[  1072.460] (==) Matched vesa as autoconfigured driver 4
[  1072.460] (==) Assigned the driver to the xf86ConfigLayout
[  1072.460] (II) LoadModule: "nvidia"
[  1072.460] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  1072.461] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1072.461] 	compiled for 4.0.2, module version = 1.0.0
[  1072.461] 	Module class: X.Org Video Driver
[  1072.465] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  1072.465] (EE) NVIDIA:     system's kernel log for additional error messages.
[  1072.465] (II) UnloadModule: "nvidia"
[  1072.466] (II) Unloading nvidia
[  1072.466] (EE) Failed to load module "nvidia" (module-specific error, 0)
[  1072.466] (II) LoadModule: "nouveau"
[  1072.466] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1072.466] (II) Module nouveau: vendor="X.Org Foundation"
[  1072.466] 	compiled for 1.15.0, module version = 1.0.10
[  1072.466] 	Module class: X.Org Video Driver
[  1072.466] 	ABI class: X.Org Video Driver, version 15.0
[  1072.466] (II) UnloadModule: "nouveau"
[  1072.466] (II) Unloading nouveau
[  1072.466] (II) Failed to load module "nouveau" (already loaded, 0)
[  1072.466] (II) LoadModule: "modesetting"
[  1072.466] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  1072.466] (II) Module modesetting: vendor="X.Org Foundation"
[  1072.466] 	compiled for 1.15.0, module version = 0.8.1
[  1072.466] 	Module class: X.Org Video Driver
[  1072.466] 	ABI class: X.Org Video Driver, version 15.0
[  1072.466] (II) UnloadModule: "modesetting"
[  1072.466] (II) Unloading modesetting
[  1072.467] (II) Failed to load module "modesetting" (already loaded, 0)
[  1072.467] (II) LoadModule: "fbdev"
[  1072.467] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1072.467] (II) Module fbdev: vendor="X.Org Foundation"
[  1072.467] 	compiled for 1.15.0, module version = 0.4.4
[  1072.467] 	Module class: X.Org Video Driver
[  1072.467] 	ABI class: X.Org Video Driver, version 15.0
[  1072.467] (II) UnloadModule: "fbdev"
[  1072.467] (II) Unloading fbdev
[  1072.467] (II) Failed to load module "fbdev" (already loaded, 0)
[  1072.467] (II) LoadModule: "vesa"
[  1072.467] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1072.467] (II) Module vesa: vendor="X.Org Foundation"
[  1072.467] 	compiled for 1.15.0, module version = 2.3.3
[  1072.467] 	Module class: X.Org Video Driver
[  1072.467] 	ABI class: X.Org Video Driver, version 15.0
[  1072.467] (II) UnloadModule: "vesa"
[  1072.467] (II) Unloading vesa
[  1072.467] (II) Failed to load module "vesa" (already loaded, 0)
[  1072.467] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[  1072.467] (II) NOUVEAU driver for NVIDIA chipset families :
[  1072.467] 	RIVA TNT        (NV04)
[  1072.467] 	RIVA TNT2       (NV05)
[  1072.467] 	GeForce 256     (NV10)
[  1072.467] 	GeForce 2       (NV11, NV15)
[  1072.468] 	GeForce 4MX     (NV17, NV18)
[  1072.468] 	GeForce 3       (NV20)
[  1072.468] 	GeForce 4Ti     (NV25, NV28)
[  1072.468] 	GeForce FX      (NV3x)
[  1072.468] 	GeForce 6       (NV4x)
[  1072.468] 	GeForce 7       (G7x)
[  1072.468] 	GeForce 8       (G8x)
[  1072.468] 	GeForce GTX 200 (NVA0)
[  1072.468] 	GeForce GTX 400 (NVC0)
[  1072.468] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  1072.468] (II) FBDEV: driver for framebuffer: fbdev
[  1072.468] (II) VESA: driver for VESA chipsets: vesa
[  1072.468] (++) using VT number 7

[  1072.471] (EE) [drm] KMS not enabled
[  1072.471] (EE) [drm] KMS not enabled
[  1072.472] (EE) open /dev/dri/card0: No such file or directory
[  1072.472] (EE) open /dev/dri/card0: No such file or directory
[  1072.472] (WW) Falling back to old probe method for modesetting
[  1072.472] (EE) open /dev/dri/card0: No such file or directory
[  1072.472] (EE) open /dev/dri/card0: No such file or directory
[  1072.472] (II) Loading sub module "fbdevhw"
[  1072.472] (II) LoadModule: "fbdevhw"
[  1072.490] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1072.491] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1072.491] 	compiled for 1.15.1, module version = 0.0.2
[  1072.491] 	ABI class: X.Org Video Driver, version 15.0
[  1072.491] (EE) open /dev/fb0: No such file or directory
[  1072.491] (II) Loading sub module "fbdevhw"
[  1072.491] (II) LoadModule: "fbdevhw"
[  1072.491] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1072.491] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1072.491] 	compiled for 1.15.1, module version = 0.0.2
[  1072.491] 	ABI class: X.Org Video Driver, version 15.0
[  1072.491] (EE) open /dev/fb0: No such file or directory
[  1072.491] (WW) Falling back to old probe method for fbdev
[  1072.491] (II) Loading sub module "fbdevhw"
[  1072.491] (II) LoadModule: "fbdevhw"
[  1072.492] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1072.492] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1072.492] 	compiled for 1.15.1, module version = 0.0.2
[  1072.492] 	ABI class: X.Org Video Driver, version 15.0
[  1072.492] (EE) open /dev/fb0: No such file or directory
[  1072.492] (EE) open /dev/fb0: No such file or directory
[  1072.492] (EE) Screen 0 deleted because of no matching config section.
[  1072.492] (II) UnloadModule: "modesetting"
[  1072.492] (EE) Screen 0 deleted because of no matching config section.
[  1072.492] (II) UnloadModule: "modesetting"
[  1072.492] (EE) Screen 0 deleted because of no matching config section.
[  1072.492] (II) UnloadModule: "fbdev"
[  1072.492] (II) UnloadSubModule: "fbdevhw"
[  1072.492] (EE) Screen 0 deleted because of no matching config section.
[  1072.492] (II) UnloadModule: "fbdev"
[  1072.492] (II) UnloadSubModule: "fbdevhw"
[  1072.492] (II) UnloadSubModule: "fbdevhw"
[  1072.492] (II) Loading sub module "vbe"
[  1072.492] (II) LoadModule: "vbe"
[  1072.492] (II) Loading /usr/lib/xorg/modules/libvbe.so
[  1072.514] (II) Module vbe: vendor="X.Org Foundation"
[  1072.514] 	compiled for 1.15.1, module version = 1.1.0
[  1072.514] 	ABI class: X.Org Video Driver, version 15.0
[  1072.514] (II) Loading sub module "int10"
[  1072.514] (II) LoadModule: "int10"
[  1072.515] (II) Loading /usr/lib/xorg/modules/libint10.so
[  1072.538] (II) Module int10: vendor="X.Org Foundation"
[  1072.538] 	compiled for 1.15.1, module version = 1.0.0
[  1072.539] 	ABI class: X.Org Video Driver, version 15.0
[  1072.539] (II) VESA(0): initializing int10
[  1072.545] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[  1072.554] (II) VESA(0): VESA BIOS detected
[  1072.554] (II) VESA(0): VESA VBE Version 3.0
[  1072.554] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[  1072.554] (II) VESA(0): VESA VBE OEM: NVIDIA
[  1072.554] (II) VESA(0): VESA VBE OEM Software Rev: 5.81
[  1072.554] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[  1072.554] (II) VESA(0): VESA VBE OEM Product: Crush50 Board - c51pvg0
[  1072.554] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev
[  1072.584] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  1072.584] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[  1072.584] (==) VESA(0): RGB weight 888
[  1072.584] (==) VESA(0): Default visual is TrueColor
[  1072.584] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1072.584] (II) Loading sub module "ddc"
[  1072.584] (II) LoadModule: "ddc"
[  1072.584] (II) Module "ddc" already built-in
[  1072.588] (II) VESA(0): VESA VBE DDC supported
[  1072.588] (II) VESA(0): VESA VBE DDC Level 2
[  1072.588] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[  1072.670] (II) VESA(0): VESA VBE DDC read successfully
[  1072.670] (II) VESA(0): Manufacturer: VSC  Model: 111e  Serial#: 16843009
[  1072.670] (II) VESA(0): Year: 2006  Week: 51
[  1072.670] (II) VESA(0): EDID Version: 1.3
[  1072.670] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[  1072.671] (II) VESA(0): Signal levels configurable
[  1072.671] (II) VESA(0): Sync:  Separate
[  1072.671] (II) VESA(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[  1072.671] (II) VESA(0): Gamma: 2.20
[  1072.671] (II) VESA(0): DPMS capabilities: Off; RGB/Color Display
[  1072.671] (II) VESA(0): Default color space is primary color space
[  1072.671] (II) VESA(0): First detailed timing is preferred mode
[  1072.671] (II) VESA(0): redX: 0.644 redY: 0.328   greenX: 0.290 greenY: 0.614
[  1072.671] (II) VESA(0): blueX: 0.142 blueY: 0.079   whiteX: 0.310 whiteY: 0.340
[  1072.671] (II) VESA(0): Supported established timings:
[  1072.671] (II) VESA(0): 720x400@70Hz
[  1072.671] (II) VESA(0): 640x480@60Hz
[  1072.671] (II) VESA(0): 640x480@67Hz
[  1072.671] (II) VESA(0): 640x480@72Hz
[  1072.671] (II) VESA(0): 640x480@75Hz
[  1072.671] (II) VESA(0): 800x600@56Hz
[  1072.671] (II) VESA(0): 800x600@60Hz
[  1072.671] (II) VESA(0): 800x600@72Hz
[  1072.671] (II) VESA(0): 800x600@75Hz
[  1072.671] (II) VESA(0): 832x624@75Hz
[  1072.671] (II) VESA(0): 1024x768@60Hz
[  1072.671] (II) VESA(0): 1024x768@70Hz
[  1072.671] (II) VESA(0): 1024x768@75Hz
[  1072.671] (II) VESA(0): 1280x1024@75Hz
[  1072.671] (II) VESA(0): 1152x864@75Hz
[  1072.671] (II) VESA(0): Manufacturer's mask: 0
[  1072.671] (II) VESA(0): Supported standard timings:
[  1072.671] (II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  1072.671] (II) VESA(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[  1072.671] (II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  1072.671] (II) VESA(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[  1072.671] (II) VESA(0): #4: hsize: 800  vsize 600  refresh: 85  vid: 22853
[  1072.671] (II) VESA(0): #5: hsize: 640  vsize 480  refresh: 85  vid: 22833
[  1072.671] (II) VESA(0): Supported detailed timing:
[  1072.671] (II) VESA(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[  1072.671] (II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[  1072.671] (II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[  1072.671] (II) VESA(0): Serial No: Q87065125071
[  1072.671] (II) VESA(0): Ranges: V min: 50 V max: 85 Hz, H min: 30 H max: 82 kHz, PixClock max 145 MHz
[  1072.671] (II) VESA(0): Monitor name: VA903 SERIES
[  1072.671] (II) VESA(0): EDID (in hex):
[  1072.671] (II) VESA(0): 	00ffffffffffff005a631e1101010101
[  1072.671] (II) VESA(0): 	3310010318261e782ec554a4544a9d24
[  1072.671] (II) VESA(0): 	144f57bfef8081808140714f61594559
[  1072.671] (II) VESA(0): 	315901010101302a009851002a403070
[  1072.671] (II) VESA(0): 	1300782d1100001e000000ff00513837
[  1072.671] (II) VESA(0): 	3036353132353037310a000000fd0032
[  1072.671] (II) VESA(0): 	551e520e000a202020202020000000fc
[  1072.671] (II) VESA(0): 	005641393033205345524945530a00a9
[  1072.671] (II) VESA(0): EDID vendor "VSC", prod id 4382
[  1072.671] (II) VESA(0): Using EDID range info for horizontal sync
[  1072.672] (II) VESA(0): Using EDID range info for vertical refresh
[  1072.672] (II) VESA(0): Printing DDC gathered Modelines:
[  1072.672] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[  1072.672] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1072.672] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1072.672] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1072.672] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1072.672] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1072.672] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1072.672] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1072.672] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1072.672] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1072.672] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1072.672] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1072.672] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1072.672] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1072.672] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1072.672] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1072.672] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1072.672] (II) VESA(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[  1072.672] (II) VESA(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[  1072.672] (II) VESA(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[  1072.672] (II) VESA(0): Searching for matching VESA mode(s):
[  1072.673] Mode: 100 (640x400)
[  1072.673] 	ModeAttributes: 0x39f
[  1072.673] 	WinAAttributes: 0x7
[  1072.673] 	WinBAttributes: 0x0
[  1072.673] 	WinGranularity: 64
[  1072.673] 	WinSize: 64
[  1072.673] 	WinASegment: 0xa000
[  1072.673] 	WinBSegment: 0x0
[  1072.673] 	WinFuncPtr: 0xc0009fa9
[  1072.673] 	BytesPerScanline: 640
[  1072.673] 	XResolution: 640
[  1072.673] 	YResolution: 400
[  1072.673] 	XCharSize: 8
[  1072.673] 	YCharSize: 16
[  1072.673] 	NumberOfPlanes: 1
[  1072.673] 	BitsPerPixel: 8
[  1072.673] 	NumberOfBanks: 1
[  1072.673] 	MemoryModel: 4
[  1072.673] 	BankSize: 0
[  1072.673] 	NumberOfImages: 14
[  1072.673] 	RedMaskSize: 0
[  1072.673] 	RedFieldPosition: 0
[  1072.673] 	GreenMaskSize: 0
[  1072.673] 	GreenFieldPosition: 0
[  1072.673] 	BlueMaskSize: 0
[  1072.673] 	BlueFieldPosition: 0
[  1072.673] 	RsvdMaskSize: 0
[  1072.673] 	RsvdFieldPosition: 0
[  1072.673] 	DirectColorModeInfo: 0
[  1072.673] 	PhysBasePtr: 0xe0000000
[  1072.673] 	LinBytesPerScanLine: 640
[  1072.673] 	BnkNumberOfImagePages: 14
[  1072.673] 	LinNumberOfImagePages: 14
[  1072.673] 	LinRedMaskSize: 0
[  1072.673] 	LinRedFieldPosition: 0
[  1072.673] 	LinGreenMaskSize: 0
[  1072.673] 	LinGreenFieldPosition: 0
[  1072.673] 	LinBlueMaskSize: 0
[  1072.673] 	LinBlueFieldPosition: 0
[  1072.673] 	LinRsvdMaskSize: 0
[  1072.673] 	LinRsvdFieldPosition: 0
[  1072.673] 	MaxPixelClock: 229500000
[  1072.674] Mode: 101 (640x480)
[  1072.674] 	ModeAttributes: 0x39f
[  1072.674] 	WinAAttributes: 0x7
[  1072.674] 	WinBAttributes: 0x0
[  1072.674] 	WinGranularity: 64
[  1072.674] 	WinSize: 64
[  1072.674] 	WinASegment: 0xa000
[  1072.674] 	WinBSegment: 0x0
[  1072.674] 	WinFuncPtr: 0xc0009fa9
[  1072.674] 	BytesPerScanline: 640
[  1072.674] 	XResolution: 640
[  1072.674] 	YResolution: 480
[  1072.674] 	XCharSize: 8
[  1072.674] 	YCharSize: 16
[  1072.674] 	NumberOfPlanes: 1
[  1072.674] 	BitsPerPixel: 8
[  1072.674] 	NumberOfBanks: 1
[  1072.674] 	MemoryModel: 4
[  1072.674] 	BankSize: 0
[  1072.674] 	NumberOfImages: 10
[  1072.674] 	RedMaskSize: 0
[  1072.674] 	RedFieldPosition: 0
[  1072.674] 	GreenMaskSize: 0
[  1072.674] 	GreenFieldPosition: 0
[  1072.674] 	BlueMaskSize: 0
[  1072.674] 	BlueFieldPosition: 0
[  1072.674] 	RsvdMaskSize: 0
[  1072.674] 	RsvdFieldPosition: 0
[  1072.674] 	DirectColorModeInfo: 0
[  1072.674] 	PhysBasePtr: 0xe0000000
[  1072.674] 	LinBytesPerScanLine: 640
[  1072.674] 	BnkNumberOfImagePages: 10
[  1072.674] 	LinNumberOfImagePages: 10
[  1072.674] 	LinRedMaskSize: 0
[  1072.674] 	LinRedFieldPosition: 0
[  1072.675] 	LinGreenMaskSize: 0
[  1072.675] 	LinGreenFieldPosition: 0
[  1072.675] 	LinBlueMaskSize: 0
[  1072.675] 	LinBlueFieldPosition: 0
[  1072.675] 	LinRsvdMaskSize: 0
[  1072.675] 	LinRsvdFieldPosition: 0
[  1072.675] 	MaxPixelClock: 229500000
[  1072.675] Mode: 102 (800x600)
[  1072.675] 	ModeAttributes: 0x31f
[  1072.675] 	WinAAttributes: 0x7
[  1072.675] 	WinBAttributes: 0x0
[  1072.675] 	WinGranularity: 64
[  1072.675] 	WinSize: 64
[  1072.675] 	WinASegment: 0xa000
[  1072.675] 	WinBSegment: 0x0
[  1072.675] 	WinFuncPtr: 0xc0009fa9
[  1072.675] 	BytesPerScanline: 100
[  1072.675] 	XResolution: 800
[  1072.675] 	YResolution: 600
[  1072.675] 	XCharSize: 8
[  1072.675] 	YCharSize: 16
[  1072.675] 	NumberOfPlanes: 4
[  1072.675] 	BitsPerPixel: 4
[  1072.675] 	NumberOfBanks: 1
[  1072.675] 	MemoryModel: 3
[  1072.675] 	BankSize: 0
[  1072.675] 	NumberOfImages: 14
[  1072.676] 	RedMaskSize: 0
[  1072.676] 	RedFieldPosition: 0
[  1072.676] 	GreenMaskSize: 0
[  1072.676] 	GreenFieldPosition: 0
[  1072.676] 	BlueMaskSize: 0
[  1072.676] 	BlueFieldPosition: 0
[  1072.676] 	RsvdMaskSize: 0
[  1072.676] 	RsvdFieldPosition: 0
[  1072.676] 	DirectColorModeInfo: 0
[  1072.676] 	PhysBasePtr: 0x0
[  1072.676] 	LinBytesPerScanLine: 100
[  1072.676] 	BnkNumberOfImagePages: 14
[  1072.676] 	LinNumberOfImagePages: 14
[  1072.676] 	LinRedMaskSize: 0
[  1072.676] 	LinRedFieldPosition: 0
[  1072.676] 	LinGreenMaskSize: 0
[  1072.676] 	LinGreenFieldPosition: 0
[  1072.676] 	LinBlueMaskSize: 0
[  1072.676] 	LinBlueFieldPosition: 0
[  1072.676] 	LinRsvdMaskSize: 0
[  1072.676] 	LinRsvdFieldPosition: 0
[  1072.676] 	MaxPixelClock: 108500000
[  1072.677] Mode: 103 (800x600)
[  1072.677] 	ModeAttributes: 0x39f
[  1072.677] 	WinAAttributes: 0x7
[  1072.677] 	WinBAttributes: 0x0
[  1072.677] 	WinGranularity: 64
[  1072.677] 	WinSize: 64
[  1072.677] 	WinASegment: 0xa000
[  1072.677] 	WinBSegment: 0x0
[  1072.677] 	WinFuncPtr: 0xc0009fa9
[  1072.677] 	BytesPerScanline: 800
[  1072.677] 	XResolution: 800
[  1072.677] 	YResolution: 600
[  1072.677] 	XCharSize: 8
[  1072.677] 	YCharSize: 16
[  1072.677] 	NumberOfPlanes: 1
[  1072.677] 	BitsPerPixel: 8
[  1072.677] 	NumberOfBanks: 1
[  1072.677] 	MemoryModel: 4
[  1072.677] 	BankSize: 0
[  1072.677] 	NumberOfImages: 6
[  1072.677] 	RedMaskSize: 0
[  1072.677] 	RedFieldPosition: 0
[  1072.677] 	GreenMaskSize: 0
[  1072.677] 	GreenFieldPosition: 0
[  1072.677] 	BlueMaskSize: 0
[  1072.677] 	BlueFieldPosition: 0
[  1072.677] 	RsvdMaskSize: 0
[  1072.677] 	RsvdFieldPosition: 0
[  1072.677] 	DirectColorModeInfo: 0
[  1072.677] 	PhysBasePtr: 0xe0000000
[  1072.677] 	LinBytesPerScanLine: 800
[  1072.677] 	BnkNumberOfImagePages: 6
[  1072.677] 	LinNumberOfImagePages: 6
[  1072.677] 	LinRedMaskSize: 0
[  1072.677] 	LinRedFieldPosition: 0
[  1072.677] 	LinGreenMaskSize: 0
[  1072.677] 	LinGreenFieldPosition: 0
[  1072.677] 	LinBlueMaskSize: 0
[  1072.677] 	LinBlueFieldPosition: 0
[  1072.677] 	LinRsvdMaskSize: 0
[  1072.677] 	LinRsvdFieldPosition: 0
[  1072.677] 	MaxPixelClock: 229500000
[  1072.678] Mode: 104 (1024x768)
[  1072.678] 	ModeAttributes: 0x31f
[  1072.678] 	WinAAttributes: 0x7
[  1072.678] 	WinBAttributes: 0x0
[  1072.678] 	WinGranularity: 64
[  1072.678] 	WinSize: 64
[  1072.678] 	WinASegment: 0xa000
[  1072.678] 	WinBSegment: 0x0
[  1072.678] 	WinFuncPtr: 0xc0009fa9
[  1072.678] 	BytesPerScanline: 128
[  1072.678] 	XResolution: 1024
[  1072.678] 	YResolution: 768
[  1072.678] 	XCharSize: 8
[  1072.678] 	YCharSize: 16
[  1072.678] 	NumberOfPlanes: 4
[  1072.678] 	BitsPerPixel: 4
[  1072.678] 	NumberOfBanks: 1
[  1072.678] 	MemoryModel: 3
[  1072.678] 	BankSize: 0
[  1072.678] 	NumberOfImages: 6
[  1072.678] 	RedMaskSize: 0
[  1072.678] 	RedFieldPosition: 0
[  1072.678] 	GreenMaskSize: 0
[  1072.678] 	GreenFieldPosition: 0
[  1072.678] 	BlueMaskSize: 0
[  1072.678] 	BlueFieldPosition: 0
[  1072.678] 	RsvdMaskSize: 0
[  1072.678] 	RsvdFieldPosition: 0
[  1072.678] 	DirectColorModeInfo: 0
[  1072.678] 	PhysBasePtr: 0x0
[  1072.678] 	LinBytesPerScanLine: 128
[  1072.678] 	BnkNumberOfImagePages: 6
[  1072.678] 	LinNumberOfImagePages: 6
[  1072.678] 	LinRedMaskSize: 0
[  1072.678] 	LinRedFieldPosition: 0
[  1072.678] 	LinGreenMaskSize: 0
[  1072.678] 	LinGreenFieldPosition: 0
[  1072.678] 	LinBlueMaskSize: 0
[  1072.678] 	LinBlueFieldPosition: 0
[  1072.678] 	LinRsvdMaskSize: 0
[  1072.678] 	LinRsvdFieldPosition: 0
[  1072.678] 	MaxPixelClock: 108500000
[  1072.679] Mode: 105 (1024x768)
[  1072.679] 	ModeAttributes: 0x39f
[  1072.679] 	WinAAttributes: 0x7
[  1072.679] 	WinBAttributes: 0x0
[  1072.679] 	WinGranularity: 64
[  1072.679] 	WinSize: 64
[  1072.679] 	WinASegment: 0xa000
[  1072.679] 	WinBSegment: 0x0
[  1072.679] 	WinFuncPtr: 0xc0009fa9
[  1072.679] 	BytesPerScanline: 1024
[  1072.679] 	XResolution: 1024
[  1072.679] 	YResolution: 768
[  1072.679] 	XCharSize: 8
[  1072.679] 	YCharSize: 16
[  1072.679] 	NumberOfPlanes: 1
[  1072.679] 	BitsPerPixel: 8
[  1072.679] 	NumberOfBanks: 1
[  1072.679] 	MemoryModel: 4
[  1072.679] 	BankSize: 0
[  1072.679] 	NumberOfImages: 3
[  1072.679] 	RedMaskSize: 0
[  1072.679] 	RedFieldPosition: 0
[  1072.679] 	GreenMaskSize: 0
[  1072.679] 	GreenFieldPosition: 0
[  1072.679] 	BlueMaskSize: 0
[  1072.679] 	BlueFieldPosition: 0
[  1072.679] 	RsvdMaskSize: 0
[  1072.679] 	RsvdFieldPosition: 0
[  1072.679] 	DirectColorModeInfo: 0
[  1072.679] 	PhysBasePtr: 0xe0000000
[  1072.680] 	LinBytesPerScanLine: 1024
[  1072.680] 	BnkNumberOfImagePages: 3
[  1072.680] 	LinNumberOfImagePages: 3
[  1072.680] 	LinRedMaskSize: 0
[  1072.680] 	LinRedFieldPosition: 0
[  1072.680] 	LinGreenMaskSize: 0
[  1072.680] 	LinGreenFieldPosition: 0
[  1072.680] 	LinBlueMaskSize: 0
[  1072.680] 	LinBlueFieldPosition: 0
[  1072.680] 	LinRsvdMaskSize: 0
[  1072.680] 	LinRsvdFieldPosition: 0
[  1072.680] 	MaxPixelClock: 229500000
[  1072.680] Mode: 106 (1280x1024)
[  1072.680] 	ModeAttributes: 0x31f
[  1072.680] 	WinAAttributes: 0x7
[  1072.680] 	WinBAttributes: 0x0
[  1072.680] 	WinGranularity: 64
[  1072.680] 	WinSize: 64
[  1072.680] 	WinASegment: 0xa000
[  1072.681] 	WinBSegment: 0x0
[  1072.681] 	WinFuncPtr: 0xc0009fa9
[  1072.681] 	BytesPerScanline: 160
[  1072.681] 	XResolution: 1280
[  1072.681] 	YResolution: 1024
[  1072.681] 	XCharSize: 8
[  1072.681] 	YCharSize: 16
[  1072.681] 	NumberOfPlanes: 4
[  1072.681] 	BitsPerPixel: 4
[  1072.681] 	NumberOfBanks: 1
[  1072.681] 	MemoryModel: 3
[  1072.681] 	BankSize: 0
[  1072.681] 	NumberOfImages: 3
[  1072.681] 	RedMaskSize: 0
[  1072.681] 	RedFieldPosition: 0
[  1072.681] 	GreenMaskSize: 0
[  1072.681] 	GreenFieldPosition: 0
[  1072.681] 	BlueMaskSize: 0
[  1072.681] 	BlueFieldPosition: 0
[  1072.681] 	RsvdMaskSize: 0
[  1072.681] 	RsvdFieldPosition: 0
[  1072.681] 	DirectColorModeInfo: 0
[  1072.681] 	PhysBasePtr: 0x0
[  1072.681] 	LinBytesPerScanLine: 160
[  1072.681] 	BnkNumberOfImagePages: 3
[  1072.681] 	LinNumberOfImagePages: 3
[  1072.681] 	LinRedMaskSize: 0
[  1072.681] 	LinRedFieldPosition: 0
[  1072.681] 	LinGreenMaskSize: 0
[  1072.681] 	LinGreenFieldPosition: 0
[  1072.681] 	LinBlueMaskSize: 0
[  1072.681] 	LinBlueFieldPosition: 0
[  1072.681] 	LinRsvdMaskSize: 0
[  1072.681] 	LinRsvdFieldPosition: 0
[  1072.681] 	MaxPixelClock: 108500000
[  1072.682] Mode: 107 (1280x1024)
[  1072.682] 	ModeAttributes: 0x39f
[  1072.682] 	WinAAttributes: 0x7
[  1072.682] 	WinBAttributes: 0x0
[  1072.682] 	WinGranularity: 64
[  1072.682] 	WinSize: 64
[  1072.682] 	WinASegment: 0xa000
[  1072.682] 	WinBSegment: 0x0
[  1072.682] 	WinFuncPtr: 0xc0009fa9
[  1072.682] 	BytesPerScanline: 1280
[  1072.682] 	XResolution: 1280
[  1072.682] 	YResolution: 1024
[  1072.682] 	XCharSize: 8
[  1072.682] 	YCharSize: 16
[  1072.682] 	NumberOfPlanes: 1
[  1072.682] 	BitsPerPixel: 8
[  1072.682] 	NumberOfBanks: 1
[  1072.682] 	MemoryModel: 4
[  1072.682] 	BankSize: 0
[  1072.682] 	NumberOfImages: 1
[  1072.682] 	RedMaskSize: 0
[  1072.682] 	RedFieldPosition: 0
[  1072.682] 	GreenMaskSize: 0
[  1072.682] 	GreenFieldPosition: 0
[  1072.682] 	BlueMaskSize: 0
[  1072.682] 	BlueFieldPosition: 0
[  1072.682] 	RsvdMaskSize: 0
[  1072.682] 	RsvdFieldPosition: 0
[  1072.682] 	DirectColorModeInfo: 0
[  1072.682] 	PhysBasePtr: 0xe0000000
[  1072.682] 	LinBytesPerScanLine: 1280
[  1072.682] 	BnkNumberOfImagePages: 1
[  1072.682] 	LinNumberOfImagePages: 1
[  1072.682] 	LinRedMaskSize: 0
[  1072.682] 	LinRedFieldPosition: 0
[  1072.682] 	LinGreenMaskSize: 0
[  1072.682] 	LinGreenFieldPosition: 0
[  1072.682] 	LinBlueMaskSize: 0
[  1072.682] 	LinBlueFieldPosition: 0
[  1072.682] 	LinRsvdMaskSize: 0
[  1072.682] 	LinRsvdFieldPosition: 0
[  1072.682] 	MaxPixelClock: 229500000
[  1072.683] Mode: 10e (320x200)
[  1072.683] 	ModeAttributes: 0x39f
[  1072.683] 	WinAAttributes: 0x7
[  1072.683] 	WinBAttributes: 0x0
[  1072.683] 	WinGranularity: 64
[  1072.683] 	WinSize: 64
[  1072.683] 	WinASegment: 0xa000
[  1072.683] 	WinBSegment: 0x0
[  1072.683] 	WinFuncPtr: 0xc0009fa9
[  1072.683] 	BytesPerScanline: 640
[  1072.683] 	XResolution: 320
[  1072.683] 	YResolution: 200
[  1072.683] 	XCharSize: 8
[  1072.683] 	YCharSize: 8
[  1072.683] 	NumberOfPlanes: 1
[  1072.683] 	BitsPerPixel: 16
[  1072.683] 	NumberOfBanks: 1
[  1072.683] 	MemoryModel: 6
[  1072.683] 	BankSize: 0
[  1072.683] 	NumberOfImages: 30
[  1072.683] 	RedMaskSize: 5
[  1072.683] 	RedFieldPosition: 11
[  1072.683] 	GreenMaskSize: 6
[  1072.683] 	GreenFieldPosition: 5
[  1072.683] 	BlueMaskSize: 5
[  1072.684] 	BlueFieldPosition: 0
[  1072.684] 	RsvdMaskSize: 0
[  1072.684] 	RsvdFieldPosition: 0
[  1072.684] 	DirectColorModeInfo: 0
[  1072.684] 	PhysBasePtr: 0xe0000000
[  1072.684] 	LinBytesPerScanLine: 640
[  1072.684] 	BnkNumberOfImagePages: 30
[  1072.684] 	LinNumberOfImagePages: 30
[  1072.684] 	LinRedMaskSize: 5
[  1072.684] 	LinRedFieldPosition: 11
[  1072.684] 	LinGreenMaskSize: 6
[  1072.684] 	LinGreenFieldPosition: 5
[  1072.684] 	LinBlueMaskSize: 5
[  1072.684] 	LinBlueFieldPosition: 0
[  1072.684] 	LinRsvdMaskSize: 0
[  1072.684] 	LinRsvdFieldPosition: 0
[  1072.684] 	MaxPixelClock: 229500000
[  1072.685] *Mode: 10f (320x200)
[  1072.685] 	ModeAttributes: 0x39f
[  1072.685] 	WinAAttributes: 0x7
[  1072.685] 	WinBAttributes: 0x0
[  1072.685] 	WinGranularity: 64
[  1072.685] 	WinSize: 64
[  1072.685] 	WinASegment: 0xa000
[  1072.685] 	WinBSegment: 0x0
[  1072.685] 	WinFuncPtr: 0xc0009fa9
[  1072.685] 	BytesPerScanline: 1280
[  1072.685] 	XResolution: 320
[  1072.685] 	YResolution: 200
[  1072.685] 	XCharSize: 8
[  1072.685] 	YCharSize: 8
[  1072.685] 	NumberOfPlanes: 1
[  1072.685] 	BitsPerPixel: 32
[  1072.685] 	NumberOfBanks: 1
[  1072.685] 	MemoryModel: 6
[  1072.685] 	BankSize: 0
[  1072.685] 	NumberOfImages: 14
[  1072.685] 	RedMaskSize: 8
[  1072.685] 	RedFieldPosition: 16
[  1072.685] 	GreenMaskSize: 8
[  1072.685] 	GreenFieldPosition: 8
[  1072.685] 	BlueMaskSize: 8
[  1072.685] 	BlueFieldPosition: 0
[  1072.685] 	RsvdMaskSize: 8
[  1072.685] 	RsvdFieldPosition: 24
[  1072.685] 	DirectColorModeInfo: 0
[  1072.685] 	PhysBasePtr: 0xe0000000
[  1072.685] 	LinBytesPerScanLine: 1280
[  1072.685] 	BnkNumberOfImagePages: 14
[  1072.685] 	LinNumberOfImagePages: 14
[  1072.685] 	LinRedMaskSize: 8
[  1072.685] 	LinRedFieldPosition: 16
[  1072.685] 	LinGreenMaskSize: 8
[  1072.685] 	LinGreenFieldPosition: 8
[  1072.685] 	LinBlueMaskSize: 8
[  1072.685] 	LinBlueFieldPosition: 0
[  1072.685] 	LinRsvdMaskSize: 8
[  1072.685] 	LinRsvdFieldPosition: 24
[  1072.685] 	MaxPixelClock: 229500000
[  1072.686] Mode: 111 (640x480)
[  1072.686] 	ModeAttributes: 0x39f
[  1072.686] 	WinAAttributes: 0x7
[  1072.686] 	WinBAttributes: 0x0
[  1072.686] 	WinGranularity: 64
[  1072.686] 	WinSize: 64
[  1072.686] 	WinASegment: 0xa000
[  1072.686] 	WinBSegment: 0x0
[  1072.686] 	WinFuncPtr: 0xc0009fa9
[  1072.686] 	BytesPerScanline: 1280
[  1072.686] 	XResolution: 640
[  1072.686] 	YResolution: 480
[  1072.686] 	XCharSize: 8
[  1072.686] 	YCharSize: 16
[  1072.686] 	NumberOfPlanes: 1
[  1072.686] 	BitsPerPixel: 16
[  1072.686] 	NumberOfBanks: 1
[  1072.686] 	MemoryModel: 6
[  1072.686] 	BankSize: 0
[  1072.686] 	NumberOfImages: 4
[  1072.686] 	RedMaskSize: 5
[  1072.686] 	RedFieldPosition: 11
[  1072.686] 	GreenMaskSize: 6
[  1072.686] 	GreenFieldPosition: 5
[  1072.686] 	BlueMaskSize: 5
[  1072.686] 	BlueFieldPosition: 0
[  1072.686] 	RsvdMaskSize: 0
[  1072.686] 	RsvdFieldPosition: 0
[  1072.686] 	DirectColorModeInfo: 0
[  1072.686] 	PhysBasePtr: 0xe0000000
[  1072.686] 	LinBytesPerScanLine: 1280
[  1072.686] 	BnkNumberOfImagePages: 4
[  1072.686] 	LinNumberOfImagePages: 4
[  1072.686] 	LinRedMaskSize: 5
[  1072.686] 	LinRedFieldPosition: 11
[  1072.686] 	LinGreenMaskSize: 6
[  1072.686] 	LinGreenFieldPosition: 5
[  1072.686] 	LinBlueMaskSize: 5
[  1072.686] 	LinBlueFieldPosition: 0
[  1072.686] 	LinRsvdMaskSize: 0
[  1072.686] 	LinRsvdFieldPosition: 0
[  1072.686] 	MaxPixelClock: 229500000
[  1072.687] *Mode: 112 (640x480)
[  1072.687] 	ModeAttributes: 0x39f
[  1072.687] 	WinAAttributes: 0x7
[  1072.687] 	WinBAttributes: 0x0
[  1072.687] 	WinGranularity: 64
[  1072.687] 	WinSize: 64
[  1072.687] 	WinASegment: 0xa000
[  1072.687] 	WinBSegment: 0x0
[  1072.687] 	WinFuncPtr: 0xc0009fa9
[  1072.687] 	BytesPerScanline: 2560
[  1072.687] 	XResolution: 640
[  1072.687] 	YResolution: 480
[  1072.687] 	XCharSize: 8
[  1072.687] 	YCharSize: 16
[  1072.687] 	NumberOfPlanes: 1
[  1072.687] 	BitsPerPixel: 32
[  1072.687] 	NumberOfBanks: 1
[  1072.687] 	MemoryModel: 6
[  1072.687] 	BankSize: 0
[  1072.687] 	NumberOfImages: 1
[  1072.687] 	RedMaskSize: 8
[  1072.687] 	RedFieldPosition: 16
[  1072.687] 	GreenMaskSize: 8
[  1072.687] 	GreenFieldPosition: 8
[  1072.688] 	BlueMaskSize: 8
[  1072.688] 	BlueFieldPosition: 0
[  1072.688] 	RsvdMaskSize: 8
[  1072.688] 	RsvdFieldPosition: 24
[  1072.688] 	DirectColorModeInfo: 0
[  1072.688] 	PhysBasePtr: 0xe0000000
[  1072.688] 	LinBytesPerScanLine: 2560
[  1072.688] 	BnkNumberOfImagePages: 1
[  1072.688] 	LinNumberOfImagePages: 1
[  1072.688] 	LinRedMaskSize: 8
[  1072.688] 	LinRedFieldPosition: 16
[  1072.688] 	LinGreenMaskSize: 8
[  1072.688] 	LinGreenFieldPosition: 8
[  1072.688] 	LinBlueMaskSize: 8
[  1072.688] 	LinBlueFieldPosition: 0
[  1072.688] 	LinRsvdMaskSize: 8
[  1072.688] 	LinRsvdFieldPosition: 24
[  1072.688] 	MaxPixelClock: 229500000
[  1072.689] Mode: 114 (800x600)
[  1072.689] 	ModeAttributes: 0x39f
[  1072.689] 	WinAAttributes: 0x7
[  1072.689] 	WinBAttributes: 0x0
[  1072.689] 	WinGranularity: 64
[  1072.689] 	WinSize: 64
[  1072.689] 	WinASegment: 0xa000
[  1072.689] 	WinBSegment: 0x0
[  1072.689] 	WinFuncPtr: 0xc0009fa9
[  1072.689] 	BytesPerScanline: 1600
[  1072.689] 	XResolution: 800
[  1072.689] 	YResolution: 600
[  1072.689] 	XCharSize: 8
[  1072.689] 	YCharSize: 16
[  1072.689] 	NumberOfPlanes: 1
[  1072.689] 	BitsPerPixel: 16
[  1072.689] 	NumberOfBanks: 1
[  1072.689] 	MemoryModel: 6
[  1072.689] 	BankSize: 0
[  1072.689] 	NumberOfImages: 2
[  1072.689] 	RedMaskSize: 5
[  1072.689] 	RedFieldPosition: 11
[  1072.689] 	GreenMaskSize: 6
[  1072.689] 	GreenFieldPosition: 5
[  1072.689] 	BlueMaskSize: 5
[  1072.689] 	BlueFieldPosition: 0
[  1072.689] 	RsvdMaskSize: 0
[  1072.689] 	RsvdFieldPosition: 0
[  1072.689] 	DirectColorModeInfo: 0
[  1072.689] 	PhysBasePtr: 0xe0000000
[  1072.689] 	LinBytesPerScanLine: 1600
[  1072.689] 	BnkNumberOfImagePages: 2
[  1072.689] 	LinNumberOfImagePages: 2
[  1072.689] 	LinRedMaskSize: 5
[  1072.689] 	LinRedFieldPosition: 11
[  1072.689] 	LinGreenMaskSize: 6
[  1072.689] 	LinGreenFieldPosition: 5
[  1072.689] 	LinBlueMaskSize: 5
[  1072.689] 	LinBlueFieldPosition: 0
[  1072.689] 	LinRsvdMaskSize: 0
[  1072.689] 	LinRsvdFieldPosition: 0
[  1072.689] 	MaxPixelClock: 229500000
[  1072.690] *Mode: 115 (800x600)
[  1072.690] 	ModeAttributes: 0x39f
[  1072.690] 	WinAAttributes: 0x7
[  1072.690] 	WinBAttributes: 0x0
[  1072.690] 	WinGranularity: 64
[  1072.690] 	WinSize: 64
[  1072.690] 	WinASegment: 0xa000
[  1072.690] 	WinBSegment: 0x0
[  1072.690] 	WinFuncPtr: 0xc0009fa9
[  1072.690] 	BytesPerScanline: 3200
[  1072.690] 	XResolution: 800
[  1072.690] 	YResolution: 600
[  1072.690] 	XCharSize: 8
[  1072.690] 	YCharSize: 16
[  1072.690] 	NumberOfPlanes: 1
[  1072.690] 	BitsPerPixel: 32
[  1072.690] 	NumberOfBanks: 1
[  1072.690] 	MemoryModel: 6
[  1072.690] 	BankSize: 0
[  1072.690] 	NumberOfImages: 1
[  1072.690] 	RedMaskSize: 8
[  1072.690] 	RedFieldPosition: 16
[  1072.690] 	GreenMaskSize: 8
[  1072.690] 	GreenFieldPosition: 8
[  1072.690] 	BlueMaskSize: 8
[  1072.690] 	BlueFieldPosition: 0
[  1072.690] 	RsvdMaskSize: 8
[  1072.690] 	RsvdFieldPosition: 24
[  1072.690] 	DirectColorModeInfo: 0
[  1072.690] 	PhysBasePtr: 0xe0000000
[  1072.690] 	LinBytesPerScanLine: 3200
[  1072.690] 	BnkNumberOfImagePages: 1
[  1072.690] 	LinNumberOfImagePages: 1
[  1072.690] 	LinRedMaskSize: 8
[  1072.690] 	LinRedFieldPosition: 16
[  1072.690] 	LinGreenMaskSize: 8
[  1072.690] 	LinGreenFieldPosition: 8
[  1072.690] 	LinBlueMaskSize: 8
[  1072.690] 	LinBlueFieldPosition: 0
[  1072.690] 	LinRsvdMaskSize: 8
[  1072.690] 	LinRsvdFieldPosition: 24
[  1072.690] 	MaxPixelClock: 229500000
[  1072.691] Mode: 117 (1024x768)
[  1072.691] 	ModeAttributes: 0x39f
[  1072.691] 	WinAAttributes: 0x7
[  1072.691] 	WinBAttributes: 0x0
[  1072.691] 	WinGranularity: 64
[  1072.691] 	WinSize: 64
[  1072.691] 	WinASegment: 0xa000
[  1072.691] 	WinBSegment: 0x0
[  1072.691] 	WinFuncPtr: 0xc0009fa9
[  1072.691] 	BytesPerScanline: 2048
[  1072.691] 	XResolution: 1024
[  1072.691] 	YResolution: 768
[  1072.691] 	XCharSize: 8
[  1072.691] 	YCharSize: 16
[  1072.691] 	NumberOfPlanes: 1
[  1072.692] 	BitsPerPixel: 16
[  1072.692] 	NumberOfBanks: 1
[  1072.692] 	MemoryModel: 6
[  1072.692] 	BankSize: 0
[  1072.692] 	NumberOfImages: 1
[  1072.692] 	RedMaskSize: 5
[  1072.692] 	RedFieldPosition: 11
[  1072.692] 	GreenMaskSize: 6
[  1072.692] 	GreenFieldPosition: 5
[  1072.692] 	BlueMaskSize: 5
[  1072.692] 	BlueFieldPosition: 0
[  1072.692] 	RsvdMaskSize: 0
[  1072.692] 	RsvdFieldPosition: 0
[  1072.692] 	DirectColorModeInfo: 0
[  1072.692] 	PhysBasePtr: 0xe0000000
[  1072.692] 	LinBytesPerScanLine: 2048
[  1072.692] 	BnkNumberOfImagePages: 1
[  1072.692] 	LinNumberOfImagePages: 1
[  1072.692] 	LinRedMaskSize: 5
[  1072.692] 	LinRedFieldPosition: 11
[  1072.692] 	LinGreenMaskSize: 6
[  1072.692] 	LinGreenFieldPosition: 5
[  1072.692] 	LinBlueMaskSize: 5
[  1072.692] 	LinBlueFieldPosition: 0
[  1072.692] 	LinRsvdMaskSize: 0
[  1072.692] 	LinRsvdFieldPosition: 0
[  1072.692] 	MaxPixelClock: 229500000
[  1072.693] *Mode: 118 (1024x768)
[  1072.693] 	ModeAttributes: 0x39f
[  1072.693] 	WinAAttributes: 0x7
[  1072.693] 	WinBAttributes: 0x0
[  1072.693] 	WinGranularity: 64
[  1072.693] 	WinSize: 64
[  1072.693] 	WinASegment: 0xa000
[  1072.693] 	WinBSegment: 0x0
[  1072.693] 	WinFuncPtr: 0xc0009fa9
[  1072.693] 	BytesPerScanline: 4096
[  1072.693] 	XResolution: 1024
[  1072.693] 	YResolution: 768
[  1072.693] 	XCharSize: 8
[  1072.693] 	YCharSize: 16
[  1072.693] 	NumberOfPlanes: 1
[  1072.693] 	BitsPerPixel: 32
[  1072.693] 	NumberOfBanks: 1
[  1072.693] 	MemoryModel: 6
[  1072.693] 	BankSize: 0
[  1072.693] 	NumberOfImages: 1
[  1072.693] 	RedMaskSize: 8
[  1072.693] 	RedFieldPosition: 16
[  1072.693] 	GreenMaskSize: 8
[  1072.693] 	GreenFieldPosition: 8
[  1072.693] 	BlueMaskSize: 8
[  1072.693] 	BlueFieldPosition: 0
[  1072.693] 	RsvdMaskSize: 8
[  1072.693] 	RsvdFieldPosition: 24
[  1072.693] 	DirectColorModeInfo: 0
[  1072.693] 	PhysBasePtr: 0xe0000000
[  1072.693] 	LinBytesPerScanLine: 4096
[  1072.693] 	BnkNumberOfImagePages: 1
[  1072.693] 	LinNumberOfImagePages: 1
[  1072.693] 	LinRedMaskSize: 8
[  1072.693] 	LinRedFieldPosition: 16
[  1072.693] 	LinGreenMaskSize: 8
[  1072.693] 	LinGreenFieldPosition: 8
[  1072.693] 	LinBlueMaskSize: 8
[  1072.693] 	LinBlueFieldPosition: 0
[  1072.693] 	LinRsvdMaskSize: 8
[  1072.693] 	LinRsvdFieldPosition: 24
[  1072.693] 	MaxPixelClock: 229500000
[  1072.694] Mode: 11a (1280x1024)
[  1072.694] 	ModeAttributes: 0x39f
[  1072.694] 	WinAAttributes: 0x7
[  1072.694] 	WinBAttributes: 0x0
[  1072.694] 	WinGranularity: 64
[  1072.694] 	WinSize: 64
[  1072.694] 	WinASegment: 0xa000
[  1072.694] 	WinBSegment: 0x0
[  1072.694] 	WinFuncPtr: 0xc0009fa9
[  1072.694] 	BytesPerScanline: 2560
[  1072.694] 	XResolution: 1280
[  1072.694] 	YResolution: 1024
[  1072.694] 	XCharSize: 8
[  1072.694] 	YCharSize: 16
[  1072.694] 	NumberOfPlanes: 1
[  1072.694] 	BitsPerPixel: 16
[  1072.694] 	NumberOfBanks: 1
[  1072.694] 	MemoryModel: 6
[  1072.694] 	BankSize: 0
[  1072.694] 	NumberOfImages: 1
[  1072.694] 	RedMaskSize: 5
[  1072.694] 	RedFieldPosition: 11
[  1072.694] 	GreenMaskSize: 6
[  1072.694] 	GreenFieldPosition: 5
[  1072.694] 	BlueMaskSize: 5
[  1072.694] 	BlueFieldPosition: 0
[  1072.694] 	RsvdMaskSize: 0
[  1072.694] 	RsvdFieldPosition: 0
[  1072.694] 	DirectColorModeInfo: 0
[  1072.694] 	PhysBasePtr: 0xe0000000
[  1072.694] 	LinBytesPerScanLine: 2560
[  1072.694] 	BnkNumberOfImagePages: 1
[  1072.694] 	LinNumberOfImagePages: 1
[  1072.694] 	LinRedMaskSize: 5
[  1072.694] 	LinRedFieldPosition: 11
[  1072.694] 	LinGreenMaskSize: 6
[  1072.694] 	LinGreenFieldPosition: 5
[  1072.694] 	LinBlueMaskSize: 5
[  1072.695] 	LinBlueFieldPosition: 0
[  1072.695] 	LinRsvdMaskSize: 0
[  1072.695] 	LinRsvdFieldPosition: 0
[  1072.695] 	MaxPixelClock: 229500000
[  1072.695] *Mode: 11b (1280x1024)
[  1072.695] 	ModeAttributes: 0x39f
[  1072.695] 	WinAAttributes: 0x7
[  1072.695] 	WinBAttributes: 0x0
[  1072.695] 	WinGranularity: 64
[  1072.695] 	WinSize: 64
[  1072.695] 	WinASegment: 0xa000
[  1072.695] 	WinBSegment: 0x0
[  1072.695] 	WinFuncPtr: 0xc0009fa9
[  1072.695] 	BytesPerScanline: 5120
[  1072.695] 	XResolution: 1280
[  1072.695] 	YResolution: 1024
[  1072.695] 	XCharSize: 8
[  1072.695] 	YCharSize: 16
[  1072.696] 	NumberOfPlanes: 1
[  1072.696] 	BitsPerPixel: 32
[  1072.696] 	NumberOfBanks: 1
[  1072.696] 	MemoryModel: 6
[  1072.696] 	BankSize: 0
[  1072.696] 	NumberOfImages: 0
[  1072.696] 	RedMaskSize: 8
[  1072.696] 	RedFieldPosition: 16
[  1072.696] 	GreenMaskSize: 8
[  1072.696] 	GreenFieldPosition: 8
[  1072.696] 	BlueMaskSize: 8
[  1072.696] 	BlueFieldPosition: 0
[  1072.696] 	RsvdMaskSize: 8
[  1072.696] 	RsvdFieldPosition: 24
[  1072.696] 	DirectColorModeInfo: 0
[  1072.696] 	PhysBasePtr: 0xe0000000
[  1072.696] 	LinBytesPerScanLine: 5120
[  1072.696] 	BnkNumberOfImagePages: 0
[  1072.696] 	LinNumberOfImagePages: 0
[  1072.696] 	LinRedMaskSize: 8
[  1072.696] 	LinRedFieldPosition: 16
[  1072.696] 	LinGreenMaskSize: 8
[  1072.696] 	LinGreenFieldPosition: 8
[  1072.696] 	LinBlueMaskSize: 8
[  1072.696] 	LinBlueFieldPosition: 0
[  1072.696] 	LinRsvdMaskSize: 8
[  1072.696] 	LinRsvdFieldPosition: 24
[  1072.696] 	MaxPixelClock: 229500000
[  1072.697] Mode: 130 (320x200)
[  1072.697] 	ModeAttributes: 0x39f
[  1072.697] 	WinAAttributes: 0x7
[  1072.697] 	WinBAttributes: 0x0
[  1072.697] 	WinGranularity: 64
[  1072.697] 	WinSize: 64
[  1072.697] 	WinASegment: 0xa000
[  1072.697] 	WinBSegment: 0x0
[  1072.697] 	WinFuncPtr: 0xc0009fa9
[  1072.697] 	BytesPerScanline: 320
[  1072.697] 	XResolution: 320
[  1072.697] 	YResolution: 200
[  1072.697] 	XCharSize: 8
[  1072.697] 	YCharSize: 8
[  1072.697] 	NumberOfPlanes: 1
[  1072.697] 	BitsPerPixel: 8
[  1072.697] 	NumberOfBanks: 1
[  1072.697] 	MemoryModel: 4
[  1072.697] 	BankSize: 0
[  1072.697] 	NumberOfImages: 62
[  1072.697] 	RedMaskSize: 0
[  1072.697] 	RedFieldPosition: 0
[  1072.697] 	GreenMaskSize: 0
[  1072.697] 	GreenFieldPosition: 0
[  1072.697] 	BlueMaskSize: 0
[  1072.697] 	BlueFieldPosition: 0
[  1072.697] 	RsvdMaskSize: 0
[  1072.697] 	RsvdFieldPosition: 0
[  1072.697] 	DirectColorModeInfo: 0
[  1072.697] 	PhysBasePtr: 0xe0000000
[  1072.697] 	LinBytesPerScanLine: 320
[  1072.697] 	BnkNumberOfImagePages: 62
[  1072.697] 	LinNumberOfImagePages: 62
[  1072.697] 	LinRedMaskSize: 0
[  1072.697] 	LinRedFieldPosition: 0
[  1072.697] 	LinGreenMaskSize: 0
[  1072.697] 	LinGreenFieldPosition: 0
[  1072.697] 	LinBlueMaskSize: 0
[  1072.697] 	LinBlueFieldPosition: 0
[  1072.697] 	LinRsvdMaskSize: 0
[  1072.697] 	LinRsvdFieldPosition: 0
[  1072.697] 	MaxPixelClock: 229500000
[  1072.698] Mode: 131 (320x400)
[  1072.698] 	ModeAttributes: 0x39f
[  1072.698] 	WinAAttributes: 0x7
[  1072.698] 	WinBAttributes: 0x0
[  1072.698] 	WinGranularity: 64
[  1072.698] 	WinSize: 64
[  1072.698] 	WinASegment: 0xa000
[  1072.698] 	WinBSegment: 0x0
[  1072.698] 	WinFuncPtr: 0xc0009fa9
[  1072.698] 	BytesPerScanline: 320
[  1072.698] 	XResolution: 320
[  1072.698] 	YResolution: 400
[  1072.698] 	XCharSize: 8
[  1072.698] 	YCharSize: 16
[  1072.698] 	NumberOfPlanes: 1
[  1072.698] 	BitsPerPixel: 8
[  1072.698] 	NumberOfBanks: 1
[  1072.698] 	MemoryModel: 4
[  1072.698] 	BankSize: 0
[  1072.698] 	NumberOfImages: 30
[  1072.698] 	RedMaskSize: 0
[  1072.698] 	RedFieldPosition: 0
[  1072.698] 	GreenMaskSize: 0
[  1072.698] 	GreenFieldPosition: 0
[  1072.698] 	BlueMaskSize: 0
[  1072.698] 	BlueFieldPosition: 0
[  1072.698] 	RsvdMaskSize: 0
[  1072.698] 	RsvdFieldPosition: 0
[  1072.699] 	DirectColorModeInfo: 0
[  1072.699] 	PhysBasePtr: 0xe0000000
[  1072.699] 	LinBytesPerScanLine: 320
[  1072.699] 	BnkNumberOfImagePages: 30
[  1072.699] 	LinNumberOfImagePages: 30
[  1072.699] 	LinRedMaskSize: 0
[  1072.699] 	LinRedFieldPosition: 0
[  1072.699] 	LinGreenMaskSize: 0
[  1072.699] 	LinGreenFieldPosition: 0
[  1072.699] 	LinBlueMaskSize: 0
[  1072.699] 	LinBlueFieldPosition: 0
[  1072.699] 	LinRsvdMaskSize: 0
[  1072.699] 	LinRsvdFieldPosition: 0
[  1072.699] 	MaxPixelClock: 229500000
[  1072.699] Mode: 132 (320x400)
[  1072.699] 	ModeAttributes: 0x39f
[  1072.699] 	WinAAttributes: 0x7
[  1072.699] 	WinBAttributes: 0x0
[  1072.699] 	WinGranularity: 64
[  1072.699] 	WinSize: 64
[  1072.699] 	WinASegment: 0xa000
[  1072.699] 	WinBSegment: 0x0
[  1072.699] 	WinFuncPtr: 0xc0009fa9
[  1072.699] 	BytesPerScanline: 640
[  1072.700] 	XResolution: 320
[  1072.700] 	YResolution: 400
[  1072.700] 	XCharSize: 8
[  1072.700] 	YCharSize: 16
[  1072.700] 	NumberOfPlanes: 1
[  1072.700] 	BitsPerPixel: 16
[  1072.700] 	NumberOfBanks: 1
[  1072.700] 	MemoryModel: 6
[  1072.700] 	BankSize: 0
[  1072.700] 	NumberOfImages: 14
[  1072.700] 	RedMaskSize: 5
[  1072.700] 	RedFieldPosition: 11
[  1072.700] 	GreenMaskSize: 6
[  1072.700] 	GreenFieldPosition: 5
[  1072.700] 	BlueMaskSize: 5
[  1072.700] 	BlueFieldPosition: 0
[  1072.700] 	RsvdMaskSize: 0
[  1072.700] 	RsvdFieldPosition: 0
[  1072.700] 	DirectColorModeInfo: 0
[  1072.700] 	PhysBasePtr: 0xe0000000
[  1072.700] 	LinBytesPerScanLine: 640
[  1072.700] 	BnkNumberOfImagePages: 14
[  1072.700] 	LinNumberOfImagePages: 14
[  1072.700] 	LinRedMaskSize: 5
[  1072.700] 	LinRedFieldPosition: 11
[  1072.700] 	LinGreenMaskSize: 6
[  1072.700] 	LinGreenFieldPosition: 5
[  1072.700] 	LinBlueMaskSize: 5
[  1072.700] 	LinBlueFieldPosition: 0
[  1072.700] 	LinRsvdMaskSize: 0
[  1072.700] 	LinRsvdFieldPosition: 0
[  1072.700] 	MaxPixelClock: 229500000
[  1072.701] *Mode: 133 (320x400)
[  1072.701] 	ModeAttributes: 0x39f
[  1072.701] 	WinAAttributes: 0x7
[  1072.701] 	WinBAttributes: 0x0
[  1072.701] 	WinGranularity: 64
[  1072.701] 	WinSize: 64
[  1072.701] 	WinASegment: 0xa000
[  1072.701] 	WinBSegment: 0x0
[  1072.701] 	WinFuncPtr: 0xc0009fa9
[  1072.701] 	BytesPerScanline: 1280
[  1072.701] 	XResolution: 320
[  1072.701] 	YResolution: 400
[  1072.701] 	XCharSize: 8
[  1072.701] 	YCharSize: 16
[  1072.701] 	NumberOfPlanes: 1
[  1072.701] 	BitsPerPixel: 32
[  1072.701] 	NumberOfBanks: 1
[  1072.701] 	MemoryModel: 6
[  1072.701] 	BankSize: 0
[  1072.701] 	NumberOfImages: 6
[  1072.701] 	RedMaskSize: 8
[  1072.701] 	RedFieldPosition: 16
[  1072.701] 	GreenMaskSize: 8
[  1072.701] 	GreenFieldPosition: 8
[  1072.701] 	BlueMaskSize: 8
[  1072.701] 	BlueFieldPosition: 0
[  1072.701] 	RsvdMaskSize: 8
[  1072.701] 	RsvdFieldPosition: 24
[  1072.701] 	DirectColorModeInfo: 0
[  1072.701] 	PhysBasePtr: 0xe0000000
[  1072.701] 	LinBytesPerScanLine: 1280
[  1072.701] 	BnkNumberOfImagePages: 6
[  1072.701] 	LinNumberOfImagePages: 6
[  1072.701] 	LinRedMaskSize: 8
[  1072.701] 	LinRedFieldPosition: 16
[  1072.701] 	LinGreenMaskSize: 8
[  1072.701] 	LinGreenFieldPosition: 8
[  1072.701] 	LinBlueMaskSize: 8
[  1072.701] 	LinBlueFieldPosition: 0
[  1072.701] 	LinRsvdMaskSize: 8
[  1072.701] 	LinRsvdFieldPosition: 24
[  1072.701] 	MaxPixelClock: 229500000
[  1072.702] Mode: 134 (320x240)
[  1072.702] 	ModeAttributes: 0x39f
[  1072.702] 	WinAAttributes: 0x7
[  1072.702] 	WinBAttributes: 0x0
[  1072.702] 	WinGranularity: 64
[  1072.702] 	WinSize: 64
[  1072.702] 	WinASegment: 0xa000
[  1072.702] 	WinBSegment: 0x0
[  1072.702] 	WinFuncPtr: 0xc0009fa9
[  1072.702] 	BytesPerScanline: 320
[  1072.702] 	XResolution: 320
[  1072.702] 	YResolution: 240
[  1072.702] 	XCharSize: 8
[  1072.702] 	YCharSize: 8
[  1072.702] 	NumberOfPlanes: 1
[  1072.702] 	BitsPerPixel: 8
[  1072.702] 	NumberOfBanks: 1
[  1072.702] 	MemoryModel: 4
[  1072.702] 	BankSize: 0
[  1072.702] 	NumberOfImages: 30
[  1072.702] 	RedMaskSize: 0
[  1072.702] 	RedFieldPosition: 0
[  1072.702] 	GreenMaskSize: 0
[  1072.702] 	GreenFieldPosition: 0
[  1072.702] 	BlueMaskSize: 0
[  1072.703] 	BlueFieldPosition: 0
[  1072.703] 	RsvdMaskSize: 0
[  1072.703] 	RsvdFieldPosition: 0
[  1072.703] 	DirectColorModeInfo: 0
[  1072.703] 	PhysBasePtr: 0xe0000000
[  1072.703] 	LinBytesPerScanLine: 320
[  1072.703] 	BnkNumberOfImagePages: 30
[  1072.703] 	LinNumberOfImagePages: 30
[  1072.703] 	LinRedMaskSize: 0
[  1072.703] 	LinRedFieldPosition: 0
[  1072.703] 	LinGreenMaskSize: 0
[  1072.703] 	LinGreenFieldPosition: 0
[  1072.703] 	LinBlueMaskSize: 0
[  1072.703] 	LinBlueFieldPosition: 0
[  1072.703] 	LinRsvdMaskSize: 0
[  1072.703] 	LinRsvdFieldPosition: 0
[  1072.703] 	MaxPixelClock: 229500000
[  1072.703] Mode: 135 (320x240)
[  1072.703] 	ModeAttributes: 0x39f
[  1072.703] 	WinAAttributes: 0x7
[  1072.703] 	WinBAttributes: 0x0
[  1072.703] 	WinGranularity: 64
[  1072.703] 	WinSize: 64
[  1072.703] 	WinASegment: 0xa000
[  1072.704] 	WinBSegment: 0x0
[  1072.704] 	WinFuncPtr: 0xc0009fa9
[  1072.704] 	BytesPerScanline: 640
[  1072.704] 	XResolution: 320
[  1072.704] 	YResolution: 240
[  1072.704] 	XCharSize: 8
[  1072.704] 	YCharSize: 8
[  1072.704] 	NumberOfPlanes: 1
[  1072.704] 	BitsPerPixel: 16
[  1072.704] 	NumberOfBanks: 1
[  1072.704] 	MemoryModel: 6
[  1072.704] 	BankSize: 0
[  1072.704] 	NumberOfImages: 19
[  1072.704] 	RedMaskSize: 5
[  1072.704] 	RedFieldPosition: 11
[  1072.704] 	GreenMaskSize: 6
[  1072.704] 	GreenFieldPosition: 5
[  1072.704] 	BlueMaskSize: 5
[  1072.704] 	BlueFieldPosition: 0
[  1072.704] 	RsvdMaskSize: 0
[  1072.704] 	RsvdFieldPosition: 0
[  1072.704] 	DirectColorModeInfo: 0
[  1072.704] 	PhysBasePtr: 0xe0000000
[  1072.704] 	LinBytesPerScanLine: 640
[  1072.704] 	BnkNumberOfImagePages: 19
[  1072.704] 	LinNumberOfImagePages: 19
[  1072.704] 	LinRedMaskSize: 5
[  1072.704] 	LinRedFieldPosition: 11
[  1072.704] 	LinGreenMaskSize: 6
[  1072.704] 	LinGreenFieldPosition: 5
[  1072.704] 	LinBlueMaskSize: 5
[  1072.704] 	LinBlueFieldPosition: 0
[  1072.704] 	LinRsvdMaskSize: 0
[  1072.704] 	LinRsvdFieldPosition: 0
[  1072.704] 	MaxPixelClock: 229500000
[  1072.705] *Mode: 136 (320x240)
[  1072.705] 	ModeAttributes: 0x39f
[  1072.705] 	WinAAttributes: 0x7
[  1072.705] 	WinBAttributes: 0x0
[  1072.705] 	WinGranularity: 64
[  1072.705] 	WinSize: 64
[  1072.705] 	WinASegment: 0xa000
[  1072.705] 	WinBSegment: 0x0
[  1072.705] 	WinFuncPtr: 0xc0009fa9
[  1072.705] 	BytesPerScanline: 1280
[  1072.705] 	XResolution: 320
[  1072.705] 	YResolution: 240
[  1072.705] 	XCharSize: 8
[  1072.705] 	YCharSize: 8
[  1072.705] 	NumberOfPlanes: 1
[  1072.705] 	BitsPerPixel: 32
[  1072.705] 	NumberOfBanks: 1
[  1072.705] 	MemoryModel: 6
[  1072.705] 	BankSize: 0
[  1072.705] 	NumberOfImages: 10
[  1072.705] 	RedMaskSize: 8
[  1072.705] 	RedFieldPosition: 16
[  1072.705] 	GreenMaskSize: 8
[  1072.705] 	GreenFieldPosition: 8
[  1072.705] 	BlueMaskSize: 8
[  1072.705] 	BlueFieldPosition: 0
[  1072.705] 	RsvdMaskSize: 8
[  1072.705] 	RsvdFieldPosition: 24
[  1072.705] 	DirectColorModeInfo: 0
[  1072.705] 	PhysBasePtr: 0xe0000000
[  1072.705] 	LinBytesPerScanLine: 1280
[  1072.705] 	BnkNumberOfImagePages: 10
[  1072.705] 	LinNumberOfImagePages: 10
[  1072.705] 	LinRedMaskSize: 8
[  1072.705] 	LinRedFieldPosition: 16
[  1072.705] 	LinGreenMaskSize: 8
[  1072.705] 	LinGreenFieldPosition: 8
[  1072.705] 	LinBlueMaskSize: 8
[  1072.705] 	LinBlueFieldPosition: 0
[  1072.705] 	LinRsvdMaskSize: 8
[  1072.705] 	LinRsvdFieldPosition: 24
[  1072.705] 	MaxPixelClock: 229500000
[  1072.706] Mode: 13d (640x400)
[  1072.706] 	ModeAttributes: 0x39f
[  1072.706] 	WinAAttributes: 0x7
[  1072.706] 	WinBAttributes: 0x0
[  1072.706] 	WinGranularity: 64
[  1072.706] 	WinSize: 64
[  1072.706] 	WinASegment: 0xa000
[  1072.706] 	WinBSegment: 0x0
[  1072.706] 	WinFuncPtr: 0xc0009fa9
[  1072.706] 	BytesPerScanline: 1280
[  1072.706] 	XResolution: 640
[  1072.706] 	YResolution: 400
[  1072.706] 	XCharSize: 8
[  1072.706] 	YCharSize: 16
[  1072.706] 	NumberOfPlanes: 1
[  1072.706] 	BitsPerPixel: 16
[  1072.706] 	NumberOfBanks: 1
[  1072.706] 	MemoryModel: 6
[  1072.706] 	BankSize: 0
[  1072.706] 	NumberOfImages: 6
[  1072.706] 	RedMaskSize: 5
[  1072.706] 	RedFieldPosition: 11
[  1072.706] 	GreenMaskSize: 6
[  1072.706] 	GreenFieldPosition: 5
[  1072.706] 	BlueMaskSize: 5
[  1072.706] 	BlueFieldPosition: 0
[  1072.706] 	RsvdMaskSize: 0
[  1072.706] 	RsvdFieldPosition: 0
[  1072.706] 	DirectColorModeInfo: 0
[  1072.706] 	PhysBasePtr: 0xe0000000
[  1072.706] 	LinBytesPerScanLine: 1280
[  1072.707] 	BnkNumberOfImagePages: 6
[  1072.707] 	LinNumberOfImagePages: 6
[  1072.707] 	LinRedMaskSize: 5
[  1072.707] 	LinRedFieldPosition: 11
[  1072.707] 	LinGreenMaskSize: 6
[  1072.707] 	LinGreenFieldPosition: 5
[  1072.707] 	LinBlueMaskSize: 5
[  1072.707] 	LinBlueFieldPosition: 0
[  1072.707] 	LinRsvdMaskSize: 0
[  1072.707] 	LinRsvdFieldPosition: 0
[  1072.707] 	MaxPixelClock: 229500000
[  1072.707] *Mode: 13e (640x400)
[  1072.707] 	ModeAttributes: 0x39f
[  1072.707] 	WinAAttributes: 0x7
[  1072.707] 	WinBAttributes: 0x0
[  1072.707] 	WinGranularity: 64
[  1072.707] 	WinSize: 64
[  1072.707] 	WinASegment: 0xa000
[  1072.708] 	WinBSegment: 0x0
[  1072.708] 	WinFuncPtr: 0xc0009fa9
[  1072.708] 	BytesPerScanline: 2560
[  1072.708] 	XResolution: 640
[  1072.708] 	YResolution: 400
[  1072.708] 	XCharSize: 8
[  1072.708] 	YCharSize: 16
[  1072.708] 	NumberOfPlanes: 1
[  1072.708] 	BitsPerPixel: 32
[  1072.708] 	NumberOfBanks: 1
[  1072.708] 	MemoryModel: 6
[  1072.708] 	BankSize: 0
[  1072.708] 	NumberOfImages: 2
[  1072.708] 	RedMaskSize: 8
[  1072.708] 	RedFieldPosition: 16
[  1072.708] 	GreenMaskSize: 8
[  1072.708] 	GreenFieldPosition: 8
[  1072.708] 	BlueMaskSize: 8
[  1072.708] 	BlueFieldPosition: 0
[  1072.708] 	RsvdMaskSize: 8
[  1072.708] 	RsvdFieldPosition: 24
[  1072.708] 	DirectColorModeInfo: 0
[  1072.708] 	PhysBasePtr: 0xe0000000
[  1072.708] 	LinBytesPerScanLine: 2560
[  1072.708] 	BnkNumberOfImagePages: 2
[  1072.708] 	LinNumberOfImagePages: 2
[  1072.708] 	LinRedMaskSize: 8
[  1072.708] 	LinRedFieldPosition: 16
[  1072.708] 	LinGreenMaskSize: 8
[  1072.708] 	LinGreenFieldPosition: 8
[  1072.708] 	LinBlueMaskSize: 8
[  1072.708] 	LinBlueFieldPosition: 0
[  1072.708] 	LinRsvdMaskSize: 8
[  1072.708] 	LinRsvdFieldPosition: 24
[  1072.708] 	MaxPixelClock: 229500000
[  1072.709] Mode: 145 (1600x1200)
[  1072.709] 	ModeAttributes: 0x39f
[  1072.709] 	WinAAttributes: 0x7
[  1072.709] 	WinBAttributes: 0x0
[  1072.709] 	WinGranularity: 64
[  1072.709] 	WinSize: 64
[  1072.709] 	WinASegment: 0xa000
[  1072.709] 	WinBSegment: 0x0
[  1072.709] 	WinFuncPtr: 0xc0009fa9
[  1072.709] 	BytesPerScanline: 1600
[  1072.709] 	XResolution: 1600
[  1072.709] 	YResolution: 1200
[  1072.709] 	XCharSize: 8
[  1072.709] 	YCharSize: 16
[  1072.709] 	NumberOfPlanes: 1
[  1072.709] 	BitsPerPixel: 8
[  1072.709] 	NumberOfBanks: 1
[  1072.709] 	MemoryModel: 4
[  1072.709] 	BankSize: 0
[  1072.709] 	NumberOfImages: 1
[  1072.709] 	RedMaskSize: 0
[  1072.709] 	RedFieldPosition: 0
[  1072.709] 	GreenMaskSize: 0
[  1072.709] 	GreenFieldPosition: 0
[  1072.709] 	BlueMaskSize: 0
[  1072.709] 	BlueFieldPosition: 0
[  1072.709] 	RsvdMaskSize: 0
[  1072.709] 	RsvdFieldPosition: 0
[  1072.709] 	DirectColorModeInfo: 0
[  1072.709] 	PhysBasePtr: 0xe0000000
[  1072.709] 	LinBytesPerScanLine: 1600
[  1072.709] 	BnkNumberOfImagePages: 1
[  1072.709] 	LinNumberOfImagePages: 1
[  1072.709] 	LinRedMaskSize: 0
[  1072.709] 	LinRedFieldPosition: 0
[  1072.709] 	LinGreenMaskSize: 0
[  1072.709] 	LinGreenFieldPosition: 0
[  1072.709] 	LinBlueMaskSize: 0
[  1072.709] 	LinBlueFieldPosition: 0
[  1072.709] 	LinRsvdMaskSize: 0
[  1072.709] 	LinRsvdFieldPosition: 0
[  1072.709] 	MaxPixelClock: 229500000
[  1072.710] Mode: 146 (1600x1200)
[  1072.710] 	ModeAttributes: 0x39f
[  1072.710] 	WinAAttributes: 0x7
[  1072.710] 	WinBAttributes: 0x0
[  1072.710] 	WinGranularity: 64
[  1072.710] 	WinSize: 64
[  1072.710] 	WinASegment: 0xa000
[  1072.710] 	WinBSegment: 0x0
[  1072.710] 	WinFuncPtr: 0xc0009fa9
[  1072.710] 	BytesPerScanline: 3200
[  1072.710] 	XResolution: 1600
[  1072.710] 	YResolution: 1200
[  1072.710] 	XCharSize: 8
[  1072.710] 	YCharSize: 16
[  1072.710] 	NumberOfPlanes: 1
[  1072.710] 	BitsPerPixel: 16
[  1072.710] 	NumberOfBanks: 1
[  1072.710] 	MemoryModel: 6
[  1072.710] 	BankSize: 0
[  1072.710] 	NumberOfImages: 1
[  1072.710] 	RedMaskSize: 5
[  1072.710] 	RedFieldPosition: 11
[  1072.710] 	GreenMaskSize: 6
[  1072.710] 	GreenFieldPosition: 5
[  1072.710] 	BlueMaskSize: 5
[  1072.710] 	BlueFieldPosition: 0
[  1072.710] 	RsvdMaskSize: 0
[  1072.710] 	RsvdFieldPosition: 0
[  1072.710] 	DirectColorModeInfo: 0
[  1072.710] 	PhysBasePtr: 0xe0000000
[  1072.710] 	LinBytesPerScanLine: 3200
[  1072.710] 	BnkNumberOfImagePages: 1
[  1072.710] 	LinNumberOfImagePages: 1
[  1072.711] 	LinRedMaskSize: 5
[  1072.711] 	LinRedFieldPosition: 11
[  1072.711] 	LinGreenMaskSize: 6
[  1072.711] 	LinGreenFieldPosition: 5
[  1072.711] 	LinBlueMaskSize: 5
[  1072.711] 	LinBlueFieldPosition: 0
[  1072.711] 	LinRsvdMaskSize: 0
[  1072.711] 	LinRsvdFieldPosition: 0
[  1072.711] 	MaxPixelClock: 229500000
[  1072.711] Mode: 147 (1400x1050)
[  1072.711] 	ModeAttributes: 0x39f
[  1072.711] 	WinAAttributes: 0x7
[  1072.711] 	WinBAttributes: 0x0
[  1072.711] 	WinGranularity: 64
[  1072.711] 	WinSize: 64
[  1072.711] 	WinASegment: 0xa000
[  1072.711] 	WinBSegment: 0x0
[  1072.711] 	WinFuncPtr: 0xc0009fa9
[  1072.711] 	BytesPerScanline: 1400
[  1072.711] 	XResolution: 1400
[  1072.711] 	YResolution: 1050
[  1072.711] 	XCharSize: 8
[  1072.712] 	YCharSize: 14
[  1072.712] 	NumberOfPlanes: 1
[  1072.712] 	BitsPerPixel: 8
[  1072.712] 	NumberOfBanks: 1
[  1072.712] 	MemoryModel: 4
[  1072.712] 	BankSize: 0
[  1072.712] 	NumberOfImages: 1
[  1072.712] 	RedMaskSize: 0
[  1072.712] 	RedFieldPosition: 0
[  1072.712] 	GreenMaskSize: 0
[  1072.712] 	GreenFieldPosition: 0
[  1072.712] 	BlueMaskSize: 0
[  1072.712] 	BlueFieldPosition: 0
[  1072.712] 	RsvdMaskSize: 0
[  1072.712] 	RsvdFieldPosition: 0
[  1072.712] 	DirectColorModeInfo: 0
[  1072.712] 	PhysBasePtr: 0xe0000000
[  1072.712] 	LinBytesPerScanLine: 1400
[  1072.712] 	BnkNumberOfImagePages: 1
[  1072.712] 	LinNumberOfImagePages: 1
[  1072.712] 	LinRedMaskSize: 0
[  1072.712] 	LinRedFieldPosition: 0
[  1072.712] 	LinGreenMaskSize: 0
[  1072.712] 	LinGreenFieldPosition: 0
[  1072.712] 	LinBlueMaskSize: 0
[  1072.712] 	LinBlueFieldPosition: 0
[  1072.712] 	LinRsvdMaskSize: 0
[  1072.712] 	LinRsvdFieldPosition: 0
[  1072.712] 	MaxPixelClock: 229500000
[  1072.713] Mode: 148 (1400x1050)
[  1072.713] 	ModeAttributes: 0x39f
[  1072.713] 	WinAAttributes: 0x7
[  1072.713] 	WinBAttributes: 0x0
[  1072.713] 	WinGranularity: 64
[  1072.713] 	WinSize: 64
[  1072.713] 	WinASegment: 0xa000
[  1072.713] 	WinBSegment: 0x0
[  1072.713] 	WinFuncPtr: 0xc0009fa9
[  1072.713] 	BytesPerScanline: 2800
[  1072.713] 	XResolution: 1400
[  1072.713] 	YResolution: 1050
[  1072.713] 	XCharSize: 8
[  1072.713] 	YCharSize: 14
[  1072.713] 	NumberOfPlanes: 1
[  1072.713] 	BitsPerPixel: 16
[  1072.713] 	NumberOfBanks: 1
[  1072.713] 	MemoryModel: 6
[  1072.713] 	BankSize: 0
[  1072.713] 	NumberOfImages: 1
[  1072.713] 	RedMaskSize: 5
[  1072.713] 	RedFieldPosition: 11
[  1072.713] 	GreenMaskSize: 6
[  1072.713] 	GreenFieldPosition: 5
[  1072.713] 	BlueMaskSize: 5
[  1072.713] 	BlueFieldPosition: 0
[  1072.713] 	RsvdMaskSize: 0
[  1072.713] 	RsvdFieldPosition: 0
[  1072.713] 	DirectColorModeInfo: 0
[  1072.713] 	PhysBasePtr: 0xe0000000
[  1072.713] 	LinBytesPerScanLine: 2800
[  1072.713] 	BnkNumberOfImagePages: 1
[  1072.713] 	LinNumberOfImagePages: 1
[  1072.713] 	LinRedMaskSize: 5
[  1072.713] 	LinRedFieldPosition: 11
[  1072.713] 	LinGreenMaskSize: 6
[  1072.713] 	LinGreenFieldPosition: 5
[  1072.713] 	LinBlueMaskSize: 5
[  1072.713] 	LinBlueFieldPosition: 0
[  1072.713] 	LinRsvdMaskSize: 0
[  1072.713] 	LinRsvdFieldPosition: 0
[  1072.713] 	MaxPixelClock: 229500000
[  1072.714] *Mode: 152 (2048x1536)
[  1072.714] 	ModeAttributes: 0x3db
[  1072.714] 	WinAAttributes: 0x7
[  1072.714] 	WinBAttributes: 0x0
[  1072.714] 	WinGranularity: 64
[  1072.714] 	WinSize: 64
[  1072.714] 	WinASegment: 0xa000
[  1072.714] 	WinBSegment: 0x0
[  1072.714] 	WinFuncPtr: 0xc0009fa9
[  1072.714] 	BytesPerScanline: 8192
[  1072.714] 	XResolution: 2048
[  1072.714] 	YResolution: 1536
[  1072.714] 	XCharSize: 8
[  1072.714] 	YCharSize: 16
[  1072.714] 	NumberOfPlanes: 1
[  1072.714] 	BitsPerPixel: 32
[  1072.714] 	NumberOfBanks: 1
[  1072.714] 	MemoryModel: 6
[  1072.714] 	BankSize: 0
[  1072.714] 	NumberOfImages: 0
[  1072.714] 	RedMaskSize: 8
[  1072.714] 	RedFieldPosition: 16
[  1072.714] 	GreenMaskSize: 8
[  1072.715] 	GreenFieldPosition: 8
[  1072.715] 	BlueMaskSize: 8
[  1072.715] 	BlueFieldPosition: 0
[  1072.715] 	RsvdMaskSize: 8
[  1072.715] 	RsvdFieldPosition: 24
[  1072.715] 	DirectColorModeInfo: 0
[  1072.715] 	PhysBasePtr: 0xe0000000
[  1072.715] 	LinBytesPerScanLine: 8192
[  1072.715] 	BnkNumberOfImagePages: 0
[  1072.715] 	LinNumberOfImagePages: 0
[  1072.715] 	LinRedMaskSize: 8
[  1072.715] 	LinRedFieldPosition: 16
[  1072.715] 	LinGreenMaskSize: 8
[  1072.715] 	LinGreenFieldPosition: 8
[  1072.715] 	LinBlueMaskSize: 8
[  1072.715] 	LinBlueFieldPosition: 0
[  1072.715] 	LinRsvdMaskSize: 8
[  1072.715] 	LinRsvdFieldPosition: 24
[  1072.715] 	MaxPixelClock: 229500000
[  1072.715]
[  1072.715] (II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
[  1072.715] (II) VESA(0): <default monitor>: Using hsync range of 30.00-82.00 kHz
[  1072.715] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-85.00 Hz
[  1072.715] (II) VESA(0): <default monitor>: Using maximum pixel clock of 145.00 MHz
[  1072.715] (WW) VESA(0): Unable to estimate virtual size
[  1072.715] (II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
[  1072.720] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[  1072.720] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[  1072.720] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[  1072.720] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[  1072.720] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[  1072.720] (**) VESA(0): *Built-in mode "1280x1024"
[  1072.720] (**) VESA(0): *Built-in mode "1024x768"
[  1072.720] (**) VESA(0): *Built-in mode "800x600"
[  1072.720] (**) VESA(0): *Built-in mode "640x480"
[  1072.720] (**) VESA(0): Display dimensions: (380, 300) mm
[  1072.720] (**) VESA(0): DPI set to (85, 86)
[  1072.720] (**) VESA(0): Using "Shadow Framebuffer"
[  1072.720] (II) Loading sub module "shadow"
[  1072.720] (II) LoadModule: "shadow"
[  1072.720] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  1072.740] (II) Module shadow: vendor="X.Org Foundation"
[  1072.740] 	compiled for 1.15.1, module version = 1.1.0
[  1072.740] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1072.740] (II) Loading sub module "fb"
[  1072.740] (II) LoadModule: "fb"
[  1072.741] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1072.741] (II) Module fb: vendor="X.Org Foundation"
[  1072.741] 	compiled for 1.15.1, module version = 1.0.0
[  1072.741] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1072.741] (==) Depth 24 pixmap format is 32 bpp
[  1072.741] (II) Loading sub module "int10"
[  1072.741] (II) LoadModule: "int10"
[  1072.741] (II) Loading /usr/lib/xorg/modules/libint10.so
[  1072.741] (II) Module int10: vendor="X.Org Foundation"
[  1072.741] 	compiled for 1.15.1, module version = 1.0.0
[  1072.741] 	ABI class: X.Org Video Driver, version 15.0
[  1072.741] (II) VESA(0): initializing int10
[  1072.744] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[  1072.752] (II) VESA(0): VESA BIOS detected
[  1072.752] (II) VESA(0): VESA VBE Version 3.0
[  1072.752] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[  1072.752] (II) VESA(0): VESA VBE OEM: NVIDIA
[  1072.752] (II) VESA(0): VESA VBE OEM Software Rev: 5.81
[  1072.752] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[  1072.752] (II) VESA(0): VESA VBE OEM Product: Crush50 Board - c51pvg0
[  1072.752] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev
[  1072.753] (II) VESA(0): virtual address = 0xb0886000,
	physical address = 0xe0000000, size = 67108864
[  1072.777] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[  1072.823] (==) VESA(0): Default visual is TrueColor
[  1072.823] (==) VESA(0): Backing store enabled
[  1072.823] (==) VESA(0): DPMS enabled
[  1072.824] (==) RandR enabled
[  1072.834] (II) SELinux: Disabled on system
[  1072.859] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[  1072.881] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1072.886] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1072.886] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1072.886] (II) LoadModule: "evdev"
[  1072.886] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1072.905] (II) Module evdev: vendor="X.Org Foundation"
[  1072.905] 	compiled for 1.15.0, module version = 2.8.2
[  1072.905] 	Module class: X.Org XInput Driver
[  1072.905] 	ABI class: X.Org XInput driver, version 20.0
[  1072.905] (II) Using input driver 'evdev' for 'Power Button'
[  1072.905] (**) Power Button: always reports core events
[  1072.905] (**) evdev: Power Button: Device: "/dev/input/event1"
[  1072.905] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1072.905] (--) evdev: Power Button: Found keys
[  1072.905] (II) evdev: Power Button: Configuring as keyboard
[  1072.906] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1072.906] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  1072.906] (**) Option "xkb_rules" "evdev"
[  1072.906] (**) Option "xkb_model" "pc105"
[  1072.906] (**) Option "xkb_layout" "us"
[  1072.906] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1072.906] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1072.907] (II) Using input driver 'evdev' for 'Power Button'
[  1072.907] (**) Power Button: always reports core events
[  1072.907] (**) evdev: Power Button: Device: "/dev/input/event0"
[  1072.907] (--) evdev: Power Button: Vendor 0 Product 0x1
[  1072.907] (--) evdev: Power Button: Found keys
[  1072.907] (II) evdev: Power Button: Configuring as keyboard
[  1072.907] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1072.907] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[  1072.907] (**) Option "xkb_rules" "evdev"
[  1072.907] (**) Option "xkb_model" "pc105"
[  1072.907] (**) Option "xkb_layout" "us"
[  1072.907] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event6)
[  1072.907] (II) No input driver specified, ignoring this device.
[  1072.907] (II) This device may have been added with another device file.
[  1072.908] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event5)
[  1072.908] (II) No input driver specified, ignoring this device.
[  1072.908] (II) This device may have been added with another device file.
[  1072.908] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event4)
[  1072.908] (II) No input driver specified, ignoring this device.
[  1072.908] (II) This device may have been added with another device file.
[  1072.909] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1072.909] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1072.909] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1072.909] (**) AT Translated Set 2 keyboard: always reports core events
[  1072.909] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1072.909] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  1072.909] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  1072.909] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  1072.909] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  1072.909] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[  1072.909] (**) Option "xkb_rules" "evdev"
[  1072.909] (**) Option "xkb_model" "pc105"
[  1072.909] (**) Option "xkb_layout" "us"
[  1072.910] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event3)
[  1072.910] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[  1072.910] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[  1072.910] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[  1072.910] (**) evdev: ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
[  1072.910] (--) evdev: ImExPS/2 Generic Explorer Mouse: Vendor 0x2 Product 0x6
[  1072.910] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[  1072.910] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[  1072.910] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found relative axes
[  1072.910] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[  1072.910] (II) evdev: ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[  1072.910] (II) evdev: ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[  1072.910] (**) evdev: ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[  1072.910] (**) evdev: ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1072.910] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event3"
[  1072.910] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE, id 9)
[  1072.910] (II) evdev: ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[  1072.910] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[  1072.910] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[  1072.910] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[  1072.910] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[  1072.911] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[  1072.911] (II) No input driver specified, ignoring this device.
[  1072.911] (II) This device may have been added with another device file.
[ 14607.912] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[ 19390.952] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[ 22157.842] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)

```

I notice specifically that it has a lot of errors related to the nvidia driver:
[  1072.446] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  1072.446] (EE) NVIDIA:     system's kernel log for additional error messages.
and
[  1072.859] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

/var/log/apt/history.log shows:
```
Start-Date: 2015-09-01  06:54:42
Commandline: aptdaemon role='role-commit-packages' sender=':1.92'
Upgrade: libexpat1:i386 (2.1.0-4ubuntu1, 2.1.0-4ubuntu1.1), minetest:i386 (201508270701-0~4077~ubuntu14.04.1, 201508311902-0~4082~ubuntu14.04.1)
End-Date: 2015-09-01  06:55:14

Start-Date: 2015-09-01  17:22:18
Remove: libreoffice-help-en-us:i386 (4.2.8-0ubuntu1), libreoffice-l10n-en-gb:i386 (4.2.8-0ubuntu1), mythes-en-au:i386 (2.1-5.4), libreoffice-l10n-en-za:i386 (4.2.8-0ubuntu1), wine-compholio:i386 (1.7.50~ubuntu14.04.1), wine-compholio-i386:i386 (1.7.50~ubuntu14.04.1), linux-headers-generic:i386 (3.13.0.62.69), hyphen-en-us:i386 (2.8.6-3ubuntu2), libreoffice-help-en-gb:i386 (4.2.8-0ubuntu1), mythes-en-us:i386 (4.2.1-0ubuntu1.1), openoffice.org-hyphenation:i386 (0.7.1)
End-Date: 2015-09-01  17:22:37

Start-Date: 2015-09-03  06:58:08
Commandline: aptdaemon role='role-commit-packages' sender=':1.82'
Upgrade: libisccc90:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), libisc95:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), libbind9-90:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), libdns100:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), liblwres90:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), libisccfg90:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), dnsutils:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), bind9-host:i386 (9.9.5.dfsg-3ubuntu0.4, 9.9.5.dfsg-3ubuntu0.5), minetest:i386 (201508311902-0~4082~ubuntu14.04.1, 201509021901-0~4090~ubuntu14.04.1), google-chrome-stable:i386 (44.0.2403.157-1, 45.0.2454.85-1)
End-Date: 2015-09-03  06:59:21

Start-Date: 2015-09-04  07:17:28
Commandline: aptdaemon role='role-commit-packages' sender=':1.80'
Install: linux-image-3.13.0-63-generic:i386 (3.13.0-63.103), linux-image-extra-3.13.0-63-generic:i386 (3.13.0-63.103)
Upgrade: linux-libc-dev:i386 (3.13.0-62.102, 3.13.0-63.103), linux-image-generic:i386 (3.13.0.62.69, 3.13.0.63.71), libvdpau1:i386 (0.7-1, 0.7-1ubuntu0.1), minetest:i386 (201509021901-0~4090~ubuntu14.04.1, 201509031901-0~4093~ubuntu14.04.1)
End-Date: 2015-09-04  07:20:08

Start-Date: 2015-09-06  21:44:31
Commandline: aptdaemon role='role-remove-packages' sender=':1.86'
Remove: libleveldb1:i386 (1.15.0-2), libluajit-5.1-2:i386 (2.0.2+dfsg-1), minetest:i386 (201509061901-0~4097~ubuntu14.04.1), libsnappy1:i386 (1.1.0-1ubuntu1), libluajit-5.1-common:i386 (2.0.2+dfsg-1)
End-Date: 2015-09-06  21:45:00

Start-Date: 2015-09-06  21:47:41
Commandline: aptdaemon role='role-install-file' sender=':1.86'
Install: libleveldb1:i386 (1.15.0-2, automatic), libluajit-5.1-2:i386 (2.0.2+dfsg-1, automatic), libsnappy1:i386 (1.1.0-1ubuntu1, automatic), libluajit-5.1-common:i386 (2.0.2+dfsg-1, automatic)
End-Date: 2015-09-06  21:47:47

```

Nothing there specifically NVIDIA related.  But I am WAY out of my depth here.  OpenGL was working just fine middle of last week.  What do I need to uninstall or re-install to get it working again?

Thank you VERY much for any help.

---

### Post by Kilarin on 2015-09-08
Ok, problem resolved.  This is what I did:

App button > all settings button, went to additional drivers tab, and switched from nvidia 304.125 proprietary tested to X.org X server nouveau.
restarted and glxinfo now showed that opengl was working, but as soon as I tried to run an application that would use opengl, everything locked up.
So I restarted, went back to the additional drivers tab again, and switched BACK to nvidia 3014.125 proprietary tested, and restarted.
And lo and behold!  Suddenly glxinfo is showing:

server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

And I can run applications that use opengl without locking up!

I don't know what caused the problem, but apparently just switching the driver and then switching it back fixed it.

---

### Post by Habitual on 2015-09-08
> **Kilarin said:**
> I don't know what caused the problem, but apparently just switching the driver and then switching it back fixed it.
Gremlins?
Good job and well done.

---

