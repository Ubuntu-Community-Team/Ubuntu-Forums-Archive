---
title: "Ubuntu X server settings"
date: 2011-05-24
forum: Desktop Environments
---

### Post by sweBers on 2011-05-24
Can anyone help me understand now Ubuntu obtains its server settings?  I'm looking for an in-depth explanation.  It seems to me that the xorg.conf file is no longer in /etc/X11/, and I was having problems getting my display to be anything other than 640X480.  I ended up booting to a 10.10 disk and performing a reinstall (yes, I know this isn't Windows, but I didn't have anything to preserve).  The problem is, I'm afraid that the system might go back to the previous setup.

I'm trying to run Ubuntu 11.4 on a [Gericom Hummer 755ll0]("http://download.gericom.com/NOTEBOOK/Hummer-Serie/Humer-755II0/DATASHEET/").  I've upgraded the memory to 1gb, but I honestly am thinking that I am asking too much of it.

---

### Post by cayphed on 2011-05-24
You need to read the Xorg log for errors,  [B]/var/log/Xorg.0.log 

Futher information is availible here for the sever settings. [http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)
[/B]

---

### Post by sweBers on 2011-05-24
That's where I'm getting confused, actually.  It tells me to edit my xorg.conf, but I don't seem to have one:

```
swebers@gericom-hummer:/etc/X11$ ls
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config

```

This also seems to coincide with the errors I'm seeing in my Xorg.0.log

```

[    21.501] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.501] X Protocol Version 11, Revision 0
[    21.501] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    21.501] Current Operating System: Linux gericom-hummer 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    21.501] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=30d28f3a-26fd-4f0c-9481-92ac51662b40 ro quiet splash vt.handoff=7
[    21.502] Build Date: 19 April 2011  03:33:17PM
[    21.502] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    21.502] Current version of pixman: 0.20.2
[    21.502] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.502] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.502] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 24 08:06:43 2011
[    21.559] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.629] (==) No Layout section.  Using the first Screen section.
[    21.629] (==) No screen section available. Using defaults.
[    21.629] (**) |-->Screen "Default Screen Section" (0)
[    21.629] (**) |   |-->Monitor "<default monitor>"
[    21.630] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    21.630] (==) Automatically adding devices
[    21.630] (==) Automatically enabling devices
[    21.644] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.644] 	Entry deleted from font path.
[    21.678] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.678] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.678] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.678] (II) Loader magic: 0x81ffde0
[    21.678] (II) Module ABI versions:
[    21.678] 	X.Org ANSI C Emulation: 0.4
[    21.678] 	X.Org Video Driver: 10.0
[    21.678] 	X.Org XInput driver : 12.3
[    21.678] 	X.Org Server Extension : 5.0
[    21.681] (--) PCI:*(0:0:2:0) 8086:2562:1584:9000 rev 3, Mem @ 0xd0000000/134217728, 0xdff80000/524288
[    21.681] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.682] (II) LoadModule: "extmod"
[    21.726] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.754] (II) Module extmod: vendor="X.Org Foundation"
[    21.754] 	compiled for 1.10.1, module version = 1.0.0
[    21.754] 	Module class: X.Org Server Extension
[    21.754] 	ABI class: X.Org Server Extension, version 5.0
[    21.754] (II) Loading extension MIT-SCREEN-SAVER
[    21.754] (II) Loading extension XFree86-VidModeExtension
[    21.754] (II) Loading extension XFree86-DGA
[    21.754] (II) Loading extension DPMS
[    21.754] (II) Loading extension XVideo
[    21.754] (II) Loading extension XVideo-MotionCompensation
[    21.754] (II) Loading extension X-Resource
[    21.754] (II) LoadModule: "dbe"
[    21.755] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.757] (II) Module dbe: vendor="X.Org Foundation"
[    21.757] 	compiled for 1.10.1, module version = 1.0.0
[    21.757] 	Module class: X.Org Server Extension
[    21.757] 	ABI class: X.Org Server Extension, version 5.0
[    21.757] (II) Loading extension DOUBLE-BUFFER
[    21.757] (II) LoadModule: "glx"
[    21.757] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.771] (II) Module glx: vendor="X.Org Foundation"
[    21.771] 	compiled for 1.10.1, module version = 1.0.0
[    21.771] 	ABI class: X.Org Server Extension, version 5.0
[    21.772] (==) AIGLX enabled
[    21.772] (II) Loading extension GLX
[    21.773] (II) LoadModule: "record"
[    21.773] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.775] (II) Module record: vendor="X.Org Foundation"
[    21.775] 	compiled for 1.10.1, module version = 1.13.0
[    21.775] 	Module class: X.Org Server Extension
[    21.775] 	ABI class: X.Org Server Extension, version 5.0
[    21.775] (II) Loading extension RECORD
[    21.775] (II) LoadModule: "dri"
[    21.775] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.839] (II) Module dri: vendor="X.Org Foundation"
[    21.839] 	compiled for 1.10.1, module version = 1.0.0
[    21.839] 	ABI class: X.Org Server Extension, version 5.0
[    21.839] (II) Loading extension XFree86-DRI
[    21.839] (II) LoadModule: "dri2"
[    21.844] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.869] (II) Module dri2: vendor="X.Org Foundation"
[    21.869] 	compiled for 1.10.1, module version = 1.2.0
[    21.870] 	ABI class: X.Org Server Extension, version 5.0
[    21.870] (II) Loading extension DRI2
[    21.870] (==) Matched vesa as autoconfigured driver 0
[    21.870] (==) Matched fbdev as autoconfigured driver 1
[    21.870] (==) Assigned the driver to the xf86ConfigLayout
[    21.870] (II) LoadModule: "vesa"
[    21.871] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.888] (II) Module vesa: vendor="X.Org Foundation"
[    21.888] 	compiled for 1.10.0, module version = 2.3.0
[    21.889] 	Module class: X.Org Video Driver
[    21.889] 	ABI class: X.Org Video Driver, version 10.0
[    21.889] (II) LoadModule: "fbdev"
[    21.889] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.891] (II) Module fbdev: vendor="X.Org Foundation"
[    21.891] 	compiled for 1.10.0, module version = 0.4.2
[    21.891] 	ABI class: X.Org Video Driver, version 10.0
[    21.891] (II) VESA: driver for VESA chipsets: vesa
[    21.891] (II) FBDEV: driver for framebuffer: fbdev
[    21.891] (++) using VT number 7

[    21.892] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    21.892] (WW) Falling back to old probe method for vesa
[    21.892] (II) Loading sub module "fbdevhw"
[    21.892] (II) LoadModule: "fbdevhw"
[    21.893] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.894] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.894] 	compiled for 1.10.1, module version = 0.0.2
[    21.894] 	ABI class: X.Org Video Driver, version 10.0
[    21.894] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.894] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.895] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    21.895] (II) FBDEV(0): using default device
[    21.895] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.895] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    21.895] (==) FBDEV(0): RGB weight 888
[    21.896] (==) FBDEV(0): Default visual is TrueColor
[    21.896] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.896] (II) FBDEV(0): hardware: inteldrmfb (video memory: 1200kB)
[    21.896] (II) FBDEV(0): checking modes against framebuffer device...
[    21.896] (II) FBDEV(0): checking modes against monitor...
[    21.896] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    21.896] (**) FBDEV(0):  Built-in mode "current"
[    21.896] (==) FBDEV(0): DPI set to (96, 96)
[    21.896] (II) Loading sub module "fb"
[    21.896] (II) LoadModule: "fb"
[    21.897] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.924] (II) Module fb: vendor="X.Org Foundation"
[    21.924] 	compiled for 1.10.1, module version = 1.0.0
[    21.924] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.924] (**) FBDEV(0): using shadow framebuffer
[    21.924] (II) Loading sub module "shadow"
[    21.924] (II) LoadModule: "shadow"
[    21.925] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.926] (II) Module shadow: vendor="X.Org Foundation"
[    21.926] 	compiled for 1.10.1, module version = 1.1.0
[    21.927] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.927] (==) Depth 24 pixmap format is 32 bpp
[    22.001] (==) FBDEV(0): Backing store disabled
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.004] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.005] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.006] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.007] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.008] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.009] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.010] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.011] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.012] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.013] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.014] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.015] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.016] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.017] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.018] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.019] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.024] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.024] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.024] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.024] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.024] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.024] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.024] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.025] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.025] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.025] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.025] (==) FBDEV(0): DPMS enabled
[    22.025] (==) RandR enabled
[    22.025] (II) Initializing built-in extension Generic Event Extension
[    22.025] (II) Initializing built-in extension SHAPE
[    22.025] (II) Initializing built-in extension MIT-SHM
[    22.025] (II) Initializing built-in extension XInputExtension
[    22.025] (II) Initializing built-in extension XTEST
[    22.025] (II) Initializing built-in extension BIG-REQUESTS
[    22.025] (II) Initializing built-in extension SYNC
[    22.025] (II) Initializing built-in extension XKEYBOARD
[    22.026] (II) Initializing built-in extension XC-MISC
[    22.026] (II) Initializing built-in extension SECURITY
[    22.026] (II) Initializing built-in extension XINERAMA
[    22.026] (II) Initializing built-in extension XFIXES
[    22.026] (II) Initializing built-in extension RENDER
[    22.026] (II) Initializing built-in extension RANDR
[    22.026] (II) Initializing built-in extension COMPOSITE
[    22.026] (II) Initializing built-in extension DAMAGE
[    22.026] (II) Initializing built-in extension GESTURE
[    22.085] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.085] (II) AIGLX: Screen 0 is not DRI capable
[    22.085] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    22.360] (II) AIGLX: Loaded and initialized swrast
[    22.360] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    22.724] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.011] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    23.012] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.012] (II) LoadModule: "evdev"
[    23.027] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.061] (II) Module evdev: vendor="X.Org Foundation"
[    23.061] 	compiled for 1.10.0.902, module version = 2.6.0
[    23.061] 	Module class: X.Org XInput Driver
[    23.061] 	ABI class: X.Org XInput driver, version 12.3
[    23.062] (II) Using input driver 'evdev' for 'Power Button'
[    23.062] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.062] (**) Power Button: always reports core events
[    23.062] (**) Power Button: Device: "/dev/input/event3"
[    23.062] (--) Power Button: Found keys
[    23.062] (II) Power Button: Configuring as keyboard
[    23.063] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    23.063] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.063] (**) Option "xkb_rules" "evdev"
[    23.063] (**) Option "xkb_model" "pc105"
[    23.063] (**) Option "xkb_layout" "us"
[    23.187] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    23.187] (II) No input driver/identifier specified (ignoring)
[    23.206] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.207] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.207] (II) Using input driver 'evdev' for 'Power Button'
[    23.207] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.207] (**) Power Button: always reports core events
[    23.207] (**) Power Button: Device: "/dev/input/event2"
[    23.207] (--) Power Button: Found keys
[    23.207] (II) Power Button: Configuring as keyboard
[    23.207] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    23.207] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.228] (**) Option "xkb_rules" "evdev"
[    23.229] (**) Option "xkb_model" "pc105"
[    23.232] (**) Option "xkb_layout" "us"
[    23.234] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    23.234] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    23.234] (II) Using input driver 'evdev' for 'Sleep Button'
[    23.235] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.235] (**) Sleep Button: always reports core events
[    23.235] (**) Sleep Button: Device: "/dev/input/event1"
[    23.235] (--) Sleep Button: Found keys
[    23.235] (II) Sleep Button: Configuring as keyboard
[    23.235] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    23.235] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    23.235] (**) Option "xkb_rules" "evdev"
[    23.235] (**) Option "xkb_model" "pc105"
[    23.256] (**) Option "xkb_layout" "us"
[    23.434] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    23.434] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.434] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.434] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.434] (**) AT Translated Set 2 keyboard: always reports core events
[    23.435] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    23.435] (--) AT Translated Set 2 keyboard: Found keys
[    23.435] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    23.435] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    23.435] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    23.435] (**) Option "xkb_rules" "evdev"
[    23.435] (**) Option "xkb_model" "pc105"
[    23.435] (**) Option "xkb_layout" "us"
[    23.446] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    23.446] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.446] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.446] (II) LoadModule: "synaptics"
[    23.447] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.463] (II) Module synaptics: vendor="X.Org Foundation"
[    23.463] 	compiled for 1.10.0.902, module version = 1.3.99
[    23.463] 	Module class: X.Org XInput Driver
[    23.463] 	ABI class: X.Org XInput driver, version 12.3
[    23.464] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    23.464] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.464] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.464] (**) Option "Device" "/dev/input/event5"
[    23.464] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    23.464] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    23.464] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.465] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    23.465] (--) SynPS/2 Synaptics TouchPad: invalid finger width range.  defaulting to 0 - 16
[    23.465] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.465] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.465] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input5/event5"
[    23.465] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    23.465] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    23.465] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    23.465] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    23.466] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.466] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    23.466] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.466] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.467] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    23.467] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.472] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    23.472] (II) No input driver/identifier specified (ignoring)

```


I'm sure I should be able to figure it out, but after implementing several other people's fixes from the forums I felt as if I had made very little progress.

---

### Post by sweBers on 2011-05-24
While waiting, I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=1713043](http://ubuntuforums.org/showthread.php?t=1713043)
and got the below xorg configuration file.  I used cp to move it to /etc/X11/xorg.conf.  Now, my monitor is defined as laptop, but I don't see that name anywhere in the config file.

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "glx"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

This is where I got stuck like last time, because I can't find any display named "Laptop."

---

### Post by alex2399 on 2011-05-24
X11 now autoconifgures itself and the Xorg.conf file is no longer used. This is done by "X -configure" at the terminal. But i'm not completely sure how it all works. It does seem to use some fallback files. Perhaps go into recovery console and issue "X -configure". It reports on how it is configured then.

---

### Post by sweBers on 2011-05-24
Thanks!  I was pretty sure of that point, which is why I first approached the question at that angle.  I'm at work now, but I'll be able to do that when I get home.  Can anyone confirm if the X server will fall back to the xorg.conf if I were to delete some key files?

---

### Post by Krytarik on 2011-05-24
> **sweBers said:**
> Can anyone confirm if the X server will fall back to the xorg.conf if I were to delete some key files?
The settings of "/etc/X11/xorg.conf" precedence those specified in "/usr/share/X11/xorg.conf.d" if it is in place. So, no need to delete anything.

Make sure to set it up right, your current one looks kinda weird and excessive.

Greetings.

---

### Post by sweBers on 2011-05-24
> **Krytarik said:**
> The settings of "/etc/X11/xorg.conf" precedence those specified in "/usr/share/X11/xorg.conf.d" if it is in place. So, no need to delete anything.

Make sure to set it up right, your current one looks kinda weird and excessive.

Greetings.

The excessiveness you see there is the result of **sudo Xorg -configure**.  Will that do the same as **X -configure**?  What I'm realy asking if I need to run **X -configure** as alex2399 had suggested or if I should just try to rewrite my xorg.conf?

---

### Post by Krytarik on 2011-05-24
> **sweBers said:**
> The excessiveness you see there is the result of **sudo Xorg -configure**.  Will that do the same as **X -configure**?  What I'm realy asking if I need to run **X -configure** as alex2399 had suggested or if I should just try to rewrite my xorg.conf?
I've never used any of these commands to set up an xorg.conf. But since the manpage of "X" doesn't state a "-configure" option, whereas those of "Xorg" does, so the latter seems to be correct.

You could try to modify the created xorg.conf to fit your needs. I'm curious if you are really having 3 cards and 3 monitors!?

Another, and perhaps easier way, is to run xrandr commands upon boot to add/set the desired solution:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

But your issue may be the result of your monitor specs not being detected correctly. If that is the case, you need to pass them through an xorg.conf. See this guide on how to do so:
[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

It may also be that you need to pass certain options through it.

Good luck!

---

### Post by tgalati4 on 2011-05-24
Find the native resolution for your display(s) then run gtf:


tgalati4@tpad-Gloria7 ~ $ gtf 1400 1050 50

  # 1400x1050 @ 50.00 Hz (GTF) hsync: 54.05 kHz; pclk: 99.88 MHz
  Modeline "1400x1050_50.00"  99.88  1400 1480 1624 1848  1050 1051 1054 1081  -HSync +Vsync


My thinkpad t43p runs 1400 by 1050 at 50 or 60 Hz.  Cut and paste the modeline into your xorg.conf in the screen subsection.  Control-Alt-Backspace to reboot graphics or just reboot the machine if Control-Alt-Backspace is turned off.  Sometimes you can log out and log back in, but not all video cards get reset completely that way.

---

### Post by sweBers on 2011-05-25
> **Krytarik said:**
> I've never used any of these commands to set up an xorg.conf. But since the manpage of "X" doesn't state a "-configure" option, whereas those of "Xorg" does, so the latter seems to be correct.

It looks like each command does the same; both commands create an xorg.conf.new file in the working directory.

>  You could try to modify the created xorg.conf to fit your needs. I'm curious if you are really having 3 cards and 3 monitors!? 

That's what I'm going to have to do, I think.  I actually only have one card and one monitor on my laptop.  I'm actually at a loss as to why my machine reports back a monitor named "Laptop" when there is no display with that name.

>  Another, and perhaps easier way, is to run xrandr commands upon boot to add/set the desired solution:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")   I was working this angle before, and I couldn't get anywhere

>  But your issue may be the result of your monitor specs not being detected correctly. If that is the case, you need to pass them through an xorg.conf. See this guide on how to do so:
[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html) 

After going to grenage.com/xorg.html, I tried editing my xorg.conf.  I think I'm missing something fundamental here, though, so here's what I got:

```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1024x768"
	EndSubSection
EndSection


```

With this setting, my monitor application goes from defining my monitor as Laptop instead of unknown.  I don't know where it's getting the word "Laptop" from, as it's not in my xorg.conf.  I'm still getting 640x480 as my only possible configuration.  

Also, when running dccprobe, this is what I get:

[code]
webers@gericom-hummer:~$ sudo ddcprobe
[sudo] password for swebers: 
vbe: VESA 3.0 detected.
oem: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)845G/845GL/845GE/845GV Graphics Controller Hardware Version 0.0
memory: 8000kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail
[/quote]

---

### Post by Krytarik on 2011-05-25
Try to get the monitor's specs by using either of these methods:

- "hwinfo":
```
sudo apt-get install hwinfo
hwinfo --monitor
```- "xvidtune"
```
xvidtune
```[INDENT]press "Cancel"
[/INDENT]- manual of your monitor
- web search

Some of them may report different values.

Btw., is it a CRT or a LCD?

What exact make/model?

---

### Post by sweBers on 2011-05-25
> **Krytarik said:**
> Try to get the monitor's specs by using either of these methods:

- "hwinfo":
```
sudo apt-get install hwinfo
hwinfo --monitor
```- "xvidtune"
```
xvidtune
```[INDENT]press "Cancel"
[/INDENT]- manual of your monitor
- web search

Some of them may report different values.

Btw., is it a CRT or a LCD?

What exact make/model?

I'll try one of those methods later today.  It's either a 14" or 15" TFT LCD.  I'd have to disassemble the top half of the laptop in order to get a model.  Since it's such an obscure brand, [this link is the only info I can get for it]("http://download.gericom.com/NOTEBOOK/Hummer-Serie/Humer-755II0/DATASHEET/755II0.pdf").

---

### Post by sweBers on 2011-05-25
So, I still can't seem to retrieve my monitor's info.  I really don't want to have to disassemble my LCD screen to find out the exact model.  I get great settings under 10.10 running the live CD, 1024x768 @0hz, but can't seem to obtain the actual hardware info.

```


ubuntu@ubuntu:~$ hwinfo --monitor
> hal.1: read hal dataprocess 4601: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files


```

---

### Post by Krytarik on 2011-05-25
No need to disassemble your screen.

What about "xvidtune" then?

Or just use the output of the "cvt" modeline generation, like described in Grenage's guide.

---

### Post by sweBers on 2011-05-25
> **Krytarik said:**
> No need to disassemble your screen.

What about "xvidtune" then?

Or just use the output of the "cvt" modeline generation, like described in Grenage's guide.

```
ubuntu@ubuntu:~$ xvidtune
Vendor: (null), Model: (null)
Num hsync: 0, Num vsync: 0

```

```
ubuntu@ubuntu:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```

---

### Post by sweBers on 2011-05-25
I used the output of CVT to come up with the following info.  I will post it and try to reboot into 11.4.  If I don't post again in the next few minutes it's because I'm having trouble getting an X session up.

```


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync 59.5 - 63.50
	VertRefresh 47.82
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1024x768"
	EndSubSection
EndSection


```

---

### Post by sweBers on 2011-05-25
It worked for a few minutes, then when I was responding to the topic the screen froze and I rebooted to 640 x480.  Now I can't get back to 1024 X 768.

This is what I get with xrandr, btw

```

swebers@gericom-hummer:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Output VGA1 is not disconnected but has no modes
swebers@gericom-hummer:~$ xrandr
xrandr: Output VGA1 is not disconnected but has no modes
Screen 0: minimum 320 x 200, current 640 x 480, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9  
  1024x768_60.00 (0xac)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
swebers@gericom-hummer:~$ 

```

---

### Post by tgalati4 on 2011-05-25
Is your video card failing?  Perhaps it is getting too hot and the GPU is throttling back to less resolution?

---

### Post by sweBers on 2011-05-26
> **tgalati4 said:**
> Is your video card failing?  Perhaps it is getting too hot and the GPU is throttling back to less resolution?

I thought the same myself for a bit, but it seems to be that the LCD can't be probed by 11.04.  My reasoning is that 10.10 and all other previous versions work at 1024 x 768, as well as XP. It also ran Linux Mint for a while with no real problems.  I have no problems if I were to install 10.10 or run the live CD for 10.10.  I cannot boot to 11.04 via live CD or after upgrading from 10.10.  I also don't have a previous xorg.conf to rely upon.

Also, after letting the machine sit overnight, I was unable to obtain full resolution with a cold start.

Just to make sure, I ran the machine for 45 minutes at low resoution, inserted the 11.04 desktop disk, and reran the install.  The install ran at 1024x768 with no issues, but I did hold shift to get to a menu and chose to do an install only.  Once the install ended, the machine rebooted again at 640x480.

Edit:
So, I found some settings online and will modify my xorg.conf to reflect what I found.  I'm worried that I might have misinterpreted these settings, so will someone check what I've got against what is on page 3 of [http://www.notebook-lcd.ru/pdf/QD15XL06_REV_01.pdf?](http://www.notebook-lcd.ru/pdf/QD15XL06_REV_01.pdf?)

```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync 19.2 - 20.677
	VertRefresh 16.667
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync -vsync

```

---

### Post by Krytarik on 2011-05-26
> **sweBers said:**
> 
Edit:
So, I found some settings online and will modify my xorg.conf to reflect  what I found.  I'm worried that I might have misinterpreted these  settings, so will someone check what I've got against what is on page 3  of [http://www.notebook-lcd.ru/pdf/QD15XL06_REV_01.pdf?](http://www.notebook-lcd.ru/pdf/QD15XL06_REV_01.pdf?)

```

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync **19.2 - 20.677**
    VertRefresh **16.667**
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync -vsync

```
No, these values seem to have nothing to do with the values we need, at least not directly.

But I just noticed that you incorrectly translated the output of this:
> **sweBers said:**
> ```
ubuntu@ubuntu:~$ cvt 1024 768
# 1024x768 **59.92 Hz** (CVT 0.79M3) hsync: **47.82 kHz**; pclk: **63.50 MHz**
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```
into this:
> **sweBers said:**
> I used the output of CVT to come up with the following info.  I will post it and try to reboot into 11.4.  If I don't post again in the next few minutes it's because I'm having trouble getting an X session up.

```


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync **59.5 - 63.50**
    VertRefresh **47.82**
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

EndSection

```
Following the guide, it would be like this:
```

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync **47.82**
     VertRefresh **59.92**
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

```If that still doesn't work, try a lower refresh rate, for example 55 Hz:
```
cvt 1024 768 55
```

---

### Post by sweBers on 2011-05-27
> **Krytarik said:**
> No, these values seem to have nothing to do with the values we need, at least not directly.

But I just noticed that you incorrectly translated the output of this:

into this:

Following the guide, it would be like this:
```

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync **47.82**
     VertRefresh **59.92**
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

```If that still doesn't work, try a lower refresh rate, for example 55 Hz:
```
cvt 1024 768 55
```

I still seem to be having difficulty with this.  Is there anything I could take from a working x session that I could reuse with the malfunctioning install?  I have no problems getting to 1024X768 with the live CD.

---

### Post by alex2399 on 2011-05-27
Maybe you should install the Xorg-edgers PPA, and if there is a PPA for intel drivers then that one too. Perhaps there is a fix in there somewhere.

And as I said, the Xorg configuration has changed along with the drivers it uses causing problems. I have had my fair share of problems too and no amount of fiddling around with the Xorg configuration files helped. Video worked as expected with all the bling under special circumstances (from recovery mode) but caused a PC reboot & power-off consistently under others(normal start).

Just to illustrate that screwing with the files may take a lot of time and not bring you anywhere. I spent 2 weeks doing this using various versions of the video software, kernels etc... 
In my case installing a restricted driver for the video card was the solution.

---

### Post by Krytarik on 2011-05-27
> **sweBers said:**
> Is there anything I could take from a working x session that I could reuse with the malfunctioning install?  I have no problems getting to 1024X768 with the live CD.
Well, I thought of this, too, before, of course. But I don't know if you can 'install' hwinfo in it. But you can at least try xvidtune, which reports the correct values in my system.

---

### Post by sweBers on 2011-05-27
> **Krytarik said:**
> Well, I thought of this, too, before, of course. But I don't know if you can 'install' hwinfo in it. But you can at least try xvidtune, which reports the correct values in my system.

Well, running xvidtune, I get the following:

```

Num hsync: 0, Num vsync: 0

```

Using it to report back the current settings, I get this:

```

"1024x768"      0.00   1024 1024 1024 1024    768  768  768  768 -hsync -vsync -csync

```

Even when running from the live CD and using 1024/768, I still get the following output with hwinfo:

```

ubuntu@ubuntu:~$ hwinfo --monitor
> hal.1: read hal dataprocess 3986: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files

```

Do you think I ought to try running with the modeline info that xvidtune is telling me?

---

### Post by Krytarik on 2011-05-28
> **sweBers said:**
> 
```

"1024x768"      0.00   1024 1024 1024 1024    768  768  768  768 -hsync -vsync -csync

```Do you think I ought to try running with the modeline info that xvidtune is telling me?
It doesn't seem to be a correct modeline, but why not?! You may just try it.

Did you try both of my earlier suggestions?

---

### Post by sweBers on 2011-05-28
> **RYTARIC said:**
> 
Did you try both of my earlier suggestions?


Did you mean these?  I can't seem to find any documentation about the Gericom Hummer 755ll0.  I don't even know why it was even sold in the U.S.!

> **Krytarik said:**
> 
- manual of your monitor
- web search

Some of them may report different values.

Btw., is it a CRT or a LCD?

What exact make/model?

---

### Post by Krytarik on 2011-05-28
> **sweBers said:**
> Did you mean these?
No, those in my post #21.

The followed reply isn't that clear to me.

---

### Post by sweBers on 2011-05-28
> **Krytarik said:**
> No, those in my post #21.

The followed reply isn't that clear to me.

Yes, sorry, I have tried the values you suggested.  I went as low as 45 before I gave up.  

I feel like I've tried everything.  I've even installed xubuntu, lubuntu, (both 11.04) and linux mint 11 to all be greeted with the same issue.  I'm starting to feel like I'm going to be restricted to 10.04 LTS.  

I'm completely blown away that the installer cannot install the same video configuration that I am using.  All of the installers provide 1024x768 resolution before installing, but I cannot change from 640X480 after.  Besides this, everything else works just fine.

Also, regarding Ubuntu-X, this PPA only seems to address Nvidia installs for Natty.  I'm not really sure how I'd go about installing this, if it is for old Intel chipsets too.

---

### Post by Krytarik on 2011-05-29
> **sweBers said:**
> All of the installers provide 1024x768 resolution before installing, but I cannot change from 640X480 after.Did you upgrade your system each time after installation?
Or is it even without upgrading, thus running the same driver as during the installation/liveCD?

When running the Ubuntu 11.04 liveCD, check what driver is running:
```
lshw -c video
```> **sweBers said:**
> 
Also, regarding Ubuntu-X, this PPA only seems to address Nvidia installs for Natty.
Actually, *alex2399* was referring to Xorg-Edgers' PPA, which offers the most recent versions for every video driver, excluding the proprietary "fglrx" driver for ATI/AMD cards/chips. So, you may try it.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by sweBers on 2011-05-30
> **Krytarik said:**
> Did you upgrade your system each time after installation?
Or is it even without upgrading, thus running the same driver as during the installation/liveCD?

When running the Ubuntu 11.04 liveCD, check what driver is running:
```
lshw -c video
```
Actually, *alex2399* was referring to Xorg-Edgers' PPA, which offers the most recent versions for every video driver, excluding the proprietary "fglrx" driver for ATI/AMD cards/chips. So, you may try it.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

I think you were asking if I was updating my system aver the installs.  Sometimes I did, sometimes I did not.  I tried a mixed variety in order to see if I could stumble upon a working combination.  

This is the output under my fresh install of Linux Mint 11 (I tried one Ubuntu after another, all with the same results.  All my configuration changes are as good as the next.  I will boot into the CD, provide the output, install, and provide the output again.  These have all been fresh installs, but I had originally experienced difficulty with an upgrade:

```

swebers@Gericom-Hummer ~ $ sudo lshw -c video
[sudo] password for swebers: 
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d0000000-d7ffffff memory:dff80000-dfffffff

```

This is what I get when I am booting from the live CD:

```

ubuntu@ubuntu:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d0000000-d7ffffff memory:dff80000-dfffffff

```

This is the output of Xorg.0.log from the live CD, if it helps.  I'm going to start an install of 11.04 and choose to not update as I install for once.  I"ll post back again once I have more info.

```

[   309.310] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   309.310] X Protocol Version 11, Revision 0
[   309.310] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   309.310] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[   309.310] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[   309.310] Build Date: 19 April 2011  03:33:17PM
[   309.310] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   309.849] Current version of pixman: 0.20.2
[   309.850] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   309.850] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   309.850] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May 30 05:37:04 2011
[   312.596] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   312.710] (==) No Layout section.  Using the first Screen section.
[   312.710] (==) No screen section available. Using defaults.
[   312.710] (**) |-->Screen "Default Screen Section" (0)
[   312.710] (**) |   |-->Monitor "<default monitor>"
[   312.736] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   312.737] (==) Automatically adding devices
[   312.737] (==) Automatically enabling devices
[   312.744] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   312.744] 	Entry deleted from font path.
[   312.744] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   312.745] 	Entry deleted from font path.
[   312.745] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   312.745] 	Entry deleted from font path.
[   313.481] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   313.481] 	Entry deleted from font path.
[   313.481] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   313.481] 	Entry deleted from font path.
[   313.482] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   313.482] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   313.482] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   313.482] (II) Loader magic: 0x81ffde0
[   313.482] (II) Module ABI versions:
[   313.482] 	X.Org ANSI C Emulation: 0.4
[   313.482] 	X.Org Video Driver: 10.0
[   313.482] 	X.Org XInput driver : 12.3
[   313.482] 	X.Org Server Extension : 5.0
[   313.498] (--) PCI:*(0:0:2:0) 8086:2562:1584:9000 rev 3, Mem @ 0xd0000000/134217728, 0xdff80000/524288
[   313.501] (II) Open ACPI successful (/var/run/acpid.socket)
[   313.502] (II) LoadModule: "extmod"
[   315.935] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   316.409] (II) Module extmod: vendor="X.Org Foundation"
[   316.409] 	compiled for 1.10.1, module version = 1.0.0
[   316.409] 	Module class: X.Org Server Extension
[   316.409] 	ABI class: X.Org Server Extension, version 5.0
[   316.409] (II) Loading extension MIT-SCREEN-SAVER
[   316.409] (II) Loading extension XFree86-VidModeExtension
[   316.409] (II) Loading extension XFree86-DGA
[   316.409] (II) Loading extension DPMS
[   316.409] (II) Loading extension XVideo
[   316.409] (II) Loading extension XVideo-MotionCompensation
[   316.409] (II) Loading extension X-Resource
[   316.410] (II) LoadModule: "dbe"
[   316.425] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   316.758] (II) Module dbe: vendor="X.Org Foundation"
[   316.758] 	compiled for 1.10.1, module version = 1.0.0
[   316.758] 	Module class: X.Org Server Extension
[   316.758] 	ABI class: X.Org Server Extension, version 5.0
[   316.758] (II) Loading extension DOUBLE-BUFFER
[   316.758] (II) LoadModule: "glx"
[   317.347] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   318.493] (II) Module glx: vendor="X.Org Foundation"
[   318.493] 	compiled for 1.10.1, module version = 1.0.0
[   318.493] 	ABI class: X.Org Server Extension, version 5.0
[   318.931] (==) AIGLX enabled
[   318.931] (II) Loading extension GLX
[   318.931] (II) LoadModule: "record"
[   319.040] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   320.735] (II) Module record: vendor="X.Org Foundation"
[   320.735] 	compiled for 1.10.1, module version = 1.13.0
[   320.735] 	Module class: X.Org Server Extension
[   320.735] 	ABI class: X.Org Server Extension, version 5.0
[   320.735] (II) Loading extension RECORD
[   320.735] (II) LoadModule: "dri"
[   320.736] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   321.255] (II) Module dri: vendor="X.Org Foundation"
[   321.255] 	compiled for 1.10.1, module version = 1.0.0
[   321.255] 	ABI class: X.Org Server Extension, version 5.0
[   321.255] (II) Loading extension XFree86-DRI
[   321.255] (II) LoadModule: "dri2"
[   321.257] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   322.098] (II) Module dri2: vendor="X.Org Foundation"
[   322.098] 	compiled for 1.10.1, module version = 1.2.0
[   322.099] 	ABI class: X.Org Server Extension, version 5.0
[   322.099] (II) Loading extension DRI2
[   322.099] (==) Matched vesa as autoconfigured driver 0
[   322.099] (==) Matched fbdev as autoconfigured driver 1
[   322.099] (==) Assigned the driver to the xf86ConfigLayout
[   322.099] (II) LoadModule: "vesa"
[   322.100] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   323.321] (II) Module vesa: vendor="X.Org Foundation"
[   323.321] 	compiled for 1.10.0, module version = 2.3.0
[   323.321] 	Module class: X.Org Video Driver
[   323.321] 	ABI class: X.Org Video Driver, version 10.0
[   323.321] (II) LoadModule: "fbdev"
[   323.322] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   325.171] (II) Module fbdev: vendor="X.Org Foundation"
[   325.171] 	compiled for 1.10.0, module version = 0.4.2
[   325.171] 	ABI class: X.Org Video Driver, version 10.0
[   325.171] (II) VESA: driver for VESA chipsets: vesa
[   325.172] (II) FBDEV: driver for framebuffer: fbdev
[   325.172] (++) using VT number 7

[   325.172] (EE) VESA: Kernel modesetting driver in use, refusing to load
[   325.173] (WW) Falling back to old probe method for vesa
[   325.173] (II) Loading sub module "fbdevhw"
[   325.173] (II) LoadModule: "fbdevhw"
[   325.203] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   325.218] (II) Module fbdevhw: vendor="X.Org Foundation"
[   325.218] 	compiled for 1.10.1, module version = 0.0.2
[   325.218] 	ABI class: X.Org Video Driver, version 10.0
[   325.218] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   325.218] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   325.219] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[   325.219] (II) FBDEV(0): using default device
[   325.219] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   325.219] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   325.219] (==) FBDEV(0): RGB weight 888
[   325.219] (==) FBDEV(0): Default visual is TrueColor
[   325.219] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   325.224] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[   325.224] (II) FBDEV(0): checking modes against framebuffer device...
[   325.224] (II) FBDEV(0): checking modes against monitor...
[   325.224] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[   325.224] (**) FBDEV(0):  Built-in mode "current"
[   325.224] (==) FBDEV(0): DPI set to (96, 96)
[   325.224] (II) Loading sub module "fb"
[   325.224] (II) LoadModule: "fb"
[   325.226] (II) Loading /usr/lib/xorg/modules/libfb.so
[   325.734] (II) Module fb: vendor="X.Org Foundation"
[   325.734] 	compiled for 1.10.1, module version = 1.0.0
[   325.734] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   325.734] (**) FBDEV(0): using shadow framebuffer
[   325.734] (II) Loading sub module "shadow"
[   325.734] (II) LoadModule: "shadow"
[   325.744] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   325.889] (II) Module shadow: vendor="X.Org Foundation"
[   325.889] 	compiled for 1.10.1, module version = 1.1.0
[   325.889] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   325.890] (==) Depth 24 pixmap format is 32 bpp
[   325.991] (==) FBDEV(0): Backing store disabled
[   326.028] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

***238 iterations of the same line removed for simplicity purposes.***

[   326.224] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   326.224] (==) FBDEV(0): DPMS enabled
[   326.225] (==) RandR enabled
[   326.225] (II) Initializing built-in extension Generic Event Extension
[   326.225] (II) Initializing built-in extension SHAPE
[   326.225] (II) Initializing built-in extension MIT-SHM
[   326.225] (II) Initializing built-in extension XInputExtension
[   326.225] (II) Initializing built-in extension XTEST
[   326.225] (II) Initializing built-in extension BIG-REQUESTS
[   326.225] (II) Initializing built-in extension SYNC
[   326.225] (II) Initializing built-in extension XKEYBOARD
[   326.225] (II) Initializing built-in extension XC-MISC
[   326.225] (II) Initializing built-in extension SECURITY
[   326.225] (II) Initializing built-in extension XINERAMA
[   326.225] (II) Initializing built-in extension XFIXES
[   326.225] (II) Initializing built-in extension RENDER
[   326.225] (II) Initializing built-in extension RANDR
[   326.225] (II) Initializing built-in extension COMPOSITE
[   326.225] (II) Initializing built-in extension DAMAGE
[   326.225] (II) Initializing built-in extension GESTURE
[   326.580] (II) AIGLX: Screen 0 is not DRI2 capable
[   326.580] (II) AIGLX: Screen 0 is not DRI capable
[   326.580] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[   338.990] (II) AIGLX: Loaded and initialized swrast
[   338.990] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   344.998] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   351.524] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   351.525] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   351.525] (II) LoadModule: "evdev"
[   351.799] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   352.358] (II) Module evdev: vendor="X.Org Foundation"
[   352.358] 	compiled for 1.10.0.902, module version = 2.6.0
[   352.358] 	Module class: X.Org XInput Driver
[   352.359] 	ABI class: X.Org XInput driver, version 12.3
[   352.359] (II) Using input driver 'evdev' for 'Power Button'
[   352.359] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   352.359] (**) Power Button: always reports core events
[   352.359] (**) Power Button: Device: "/dev/input/event3"
[   352.359] (--) Power Button: Found keys
[   352.359] (II) Power Button: Configuring as keyboard
[   352.359] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   352.377] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   352.378] (**) Option "xkb_rules" "evdev"
[   352.378] (**) Option "xkb_model" "pc105"
[   352.378] (**) Option "xkb_layout" "us"
[   352.571] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   352.571] (II) No input driver/identifier specified (ignoring)
[   352.575] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   352.575] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   352.575] (II) Using input driver 'evdev' for 'Power Button'
[   352.575] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   352.576] (**) Power Button: always reports core events
[   352.576] (**) Power Button: Device: "/dev/input/event2"
[   352.576] (--) Power Button: Found keys
[   352.576] (II) Power Button: Configuring as keyboard
[   352.576] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[   352.576] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   352.576] (**) Option "xkb_rules" "evdev"
[   352.576] (**) Option "xkb_model" "pc105"
[   352.576] (**) Option "xkb_layout" "us"
[   352.579] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   352.579] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   352.579] (II) Using input driver 'evdev' for 'Sleep Button'
[   352.579] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   352.579] (**) Sleep Button: always reports core events
[   352.579] (**) Sleep Button: Device: "/dev/input/event1"
[   352.580] (--) Sleep Button: Found keys
[   352.580] (II) Sleep Button: Configuring as keyboard
[   352.580] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   352.580] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   352.580] (**) Option "xkb_rules" "evdev"
[   352.580] (**) Option "xkb_model" "pc105"
[   352.580] (**) Option "xkb_layout" "us"
[   352.627] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   352.627] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   352.627] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   352.627] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   352.627] (**) AT Translated Set 2 keyboard: always reports core events
[   352.627] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   352.627] (--) AT Translated Set 2 keyboard: Found keys
[   352.628] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   352.628] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   352.628] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   352.628] (**) Option "xkb_rules" "evdev"
[   352.628] (**) Option "xkb_model" "pc105"
[   352.628] (**) Option "xkb_layout" "us"
[   352.631] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   352.631] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   352.631] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   352.631] (II) LoadModule: "synaptics"
[   352.633] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   353.323] (II) Module synaptics: vendor="X.Org Foundation"
[   353.323] 	compiled for 1.10.0.902, module version = 1.3.99
[   353.324] 	Module class: X.Org XInput Driver
[   353.324] 	ABI class: X.Org XInput driver, version 12.3
[   353.324] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   353.324] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   353.324] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   353.324] (**) Option "Device" "/dev/input/event5"
[   353.324] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   353.324] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   353.324] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   353.324] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[   353.325] (--) SynPS/2 Synaptics TouchPad: invalid finger width range.  defaulting to 0 - 16
[   353.325] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   353.325] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   353.325] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input5/event5"
[   353.325] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   353.325] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   353.325] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   353.325] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[   353.326] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   353.326] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   353.326] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   353.326] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   353.326] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[   353.327] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   353.362] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   353.362] (II) No input driver/identifier specified (ignoring)

```

These are my driver settings when booting for the first time after a clean install (at 640X480):

```

swebers@Gericom-Hummer:~$ sudo lshw -c video
[sudo] password for swebers: 
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d0000000-d7ffffff memory:dff80000-dfffffff

```

Finally, this is the output of Xorg.0.log after booting for the first time after a clean install:

```

[    22.615] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    22.615] X Protocol Version 11, Revision 0
[    22.615] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    22.615] Current Operating System: Linux Gericom-Hummer 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    22.615] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=6c0a3911-4611-42cd-9e63-885f4ae9ff1a ro quiet splash vt.handoff=7
[    22.616] Build Date: 19 April 2011  03:33:17PM
[    22.616] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    22.616] Current version of pixman: 0.20.2
[    22.616] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.616] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.616] (==) Log file: "/var/log/Xorg.0.log", Time: Mon May 30 09:09:35 2011
[    22.650] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.668] (==) No Layout section.  Using the first Screen section.
[    22.668] (==) No screen section available. Using defaults.
[    22.668] (**) |-->Screen "Default Screen Section" (0)
[    22.668] (**) |   |-->Monitor "<default monitor>"
[    22.669] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.669] (==) Automatically adding devices
[    22.670] (==) Automatically enabling devices
[    22.670] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.670] 	Entry deleted from font path.
[    22.670] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.670] 	Entry deleted from font path.
[    22.670] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.670] 	Entry deleted from font path.
[    22.670] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.670] 	Entry deleted from font path.
[    22.671] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.671] 	Entry deleted from font path.
[    22.692] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.692] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.692] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.692] (II) Loader magic: 0x81ffde0
[    22.692] (II) Module ABI versions:
[    22.692] 	X.Org ANSI C Emulation: 0.4
[    22.692] 	X.Org Video Driver: 10.0
[    22.692] 	X.Org XInput driver : 12.3
[    22.692] 	X.Org Server Extension : 5.0
[    22.695] (--) PCI:*(0:0:2:0) 8086:2562:1584:9000 rev 3, Mem @ 0xd0000000/134217728, 0xdff80000/524288
[    22.695] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.695] (II) LoadModule: "extmod"
[    22.719] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.737] (II) Module extmod: vendor="X.Org Foundation"
[    22.738] 	compiled for 1.10.1, module version = 1.0.0
[    22.738] 	Module class: X.Org Server Extension
[    22.738] 	ABI class: X.Org Server Extension, version 5.0
[    22.738] (II) Loading extension MIT-SCREEN-SAVER
[    22.738] (II) Loading extension XFree86-VidModeExtension
[    22.738] (II) Loading extension XFree86-DGA
[    22.738] (II) Loading extension DPMS
[    22.738] (II) Loading extension XVideo
[    22.738] (II) Loading extension XVideo-MotionCompensation
[    22.738] (II) Loading extension X-Resource
[    22.738] (II) LoadModule: "dbe"
[    22.739] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.746] (II) Module dbe: vendor="X.Org Foundation"
[    22.746] 	compiled for 1.10.1, module version = 1.0.0
[    22.746] 	Module class: X.Org Server Extension
[    22.746] 	ABI class: X.Org Server Extension, version 5.0
[    22.746] (II) Loading extension DOUBLE-BUFFER
[    22.746] (II) LoadModule: "glx"
[    22.746] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.758] (II) Module glx: vendor="X.Org Foundation"
[    22.758] 	compiled for 1.10.1, module version = 1.0.0
[    22.758] 	ABI class: X.Org Server Extension, version 5.0
[    22.759] (==) AIGLX enabled
[    22.759] (II) Loading extension GLX
[    22.759] (II) LoadModule: "record"
[    22.760] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.761] (II) Module record: vendor="X.Org Foundation"
[    22.761] 	compiled for 1.10.1, module version = 1.13.0
[    22.761] 	Module class: X.Org Server Extension
[    22.761] 	ABI class: X.Org Server Extension, version 5.0
[    22.761] (II) Loading extension RECORD
[    22.761] (II) LoadModule: "dri"
[    22.762] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.764] (II) Module dri: vendor="X.Org Foundation"
[    22.764] 	compiled for 1.10.1, module version = 1.0.0
[    22.764] 	ABI class: X.Org Server Extension, version 5.0
[    22.764] (II) Loading extension XFree86-DRI
[    22.764] (II) LoadModule: "dri2"
[    22.765] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.766] (II) Module dri2: vendor="X.Org Foundation"
[    22.766] 	compiled for 1.10.1, module version = 1.2.0
[    22.766] 	ABI class: X.Org Server Extension, version 5.0
[    22.766] (II) Loading extension DRI2
[    22.766] (==) Matched vesa as autoconfigured driver 0
[    22.766] (==) Matched fbdev as autoconfigured driver 1
[    22.766] (==) Assigned the driver to the xf86ConfigLayout
[    22.766] (II) LoadModule: "vesa"
[    22.768] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.777] (II) Module vesa: vendor="X.Org Foundation"
[    22.777] 	compiled for 1.10.0, module version = 2.3.0
[    22.777] 	Module class: X.Org Video Driver
[    22.777] 	ABI class: X.Org Video Driver, version 10.0
[    22.777] (II) LoadModule: "fbdev"
[    22.778] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.790] (II) Module fbdev: vendor="X.Org Foundation"
[    22.790] 	compiled for 1.10.0, module version = 0.4.2
[    22.790] 	ABI class: X.Org Video Driver, version 10.0
[    22.791] (II) VESA: driver for VESA chipsets: vesa
[    22.791] (II) FBDEV: driver for framebuffer: fbdev
[    22.791] (++) using VT number 7

[    22.792] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    22.792] (WW) Falling back to old probe method for vesa
[    22.792] (II) Loading sub module "fbdevhw"
[    22.792] (II) LoadModule: "fbdevhw"
[    22.794] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.799] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.799] 	compiled for 1.10.1, module version = 0.0.2
[    22.799] 	ABI class: X.Org Video Driver, version 10.0
[    22.799] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.799] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.800] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    22.800] (II) FBDEV(0): using default device
[    22.800] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.800] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    22.800] (==) FBDEV(0): RGB weight 888
[    22.801] (==) FBDEV(0): Default visual is TrueColor
[    22.801] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.801] (II) FBDEV(0): hardware: inteldrmfb (video memory: 1200kB)
[    22.801] (II) FBDEV(0): checking modes against framebuffer device...
[    22.801] (II) FBDEV(0): checking modes against monitor...
[    22.801] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    22.801] (**) FBDEV(0):  Built-in mode "current"
[    22.801] (==) FBDEV(0): DPI set to (96, 96)
[    22.801] (II) Loading sub module "fb"
[    22.801] (II) LoadModule: "fb"
[    22.802] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.813] (II) Module fb: vendor="X.Org Foundation"
[    22.813] 	compiled for 1.10.1, module version = 1.0.0
[    22.813] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.813] (**) FBDEV(0): using shadow framebuffer
[    22.813] (II) Loading sub module "shadow"
[    22.813] (II) LoadModule: "shadow"
[    22.814] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    22.835] (II) Module shadow: vendor="X.Org Foundation"
[    22.835] 	compiled for 1.10.1, module version = 1.1.0
[    22.835] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.835] (==) Depth 24 pixmap format is 32 bpp237
[    22.915] (==) FBDEV(0): Backing store disabled
[    22.916] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

***237 iterations of the same line removed for simplicity purposes***

[    22.946] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.947] (==) FBDEV(0): DPMS enabled
[    22.947] (==) RandR enabled
[    22.947] (II) Initializing built-in extension Generic Event Extension
[    22.947] (II) Initializing built-in extension SHAPE
[    22.947] (II) Initializing built-in extension MIT-SHM
[    22.947] (II) Initializing built-in extension XInputExtension
[    22.947] (II) Initializing built-in extension XTEST
[    22.947] (II) Initializing built-in extension BIG-REQUESTS
[    22.947] (II) Initializing built-in extension SYNC
[    22.947] (II) Initializing built-in extension XKEYBOARD
[    22.947] (II) Initializing built-in extension XC-MISC
[    22.947] (II) Initializing built-in extension SECURITY
[    22.947] (II) Initializing built-in extension XINERAMA
[    22.947] (II) Initializing built-in extension XFIXES
[    22.947] (II) Initializing built-in extension RENDER
[    22.947] (II) Initializing built-in extension RANDR
[    22.947] (II) Initializing built-in extension COMPOSITE
[    22.947] (II) Initializing built-in extension DAMAGE
[    22.948] (II) Initializing built-in extension GESTURE
[    22.992] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.992] (II) AIGLX: Screen 0 is not DRI capable
[    22.992] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    23.121] (II) AIGLX: Loaded and initialized swrast
[    23.121] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.241] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.006] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    24.006] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.006] (II) LoadModule: "evdev"
[    24.015] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.082] (II) Module evdev: vendor="X.Org Foundation"
[    24.082] 	compiled for 1.10.0.902, module version = 2.6.0
[    24.082] 	Module class: X.Org XInput Driver
[    24.082] 	ABI class: X.Org XInput driver, version 12.3
[    24.082] (II) Using input driver 'evdev' for 'Power Button'
[    24.082] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.082] (**) Power Button: always reports core events
[    24.082] (**) Power Button: Device: "/dev/input/event3"
[    24.083] (--) Power Button: Found keys
[    24.083] (II) Power Button: Configuring as keyboard
[    24.083] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    24.083] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.083] (**) Option "xkb_rules" "evdev"
[    24.083] (**) Option "xkb_model" "pc105"
[    24.083] (**) Option "xkb_layout" "us"
[    24.297] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    24.297] (II) No input driver/identifier specified (ignoring)
[    24.303] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    24.303] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.303] (II) Using input driver 'evdev' for 'Power Button'
[    24.303] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.303] (**) Power Button: always reports core events
[    24.304] (**) Power Button: Device: "/dev/input/event2"
[    24.304] (--) Power Button: Found keys
[    24.304] (II) Power Button: Configuring as keyboard
[    24.304] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    24.304] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.304] (**) Option "xkb_rules" "evdev"
[    24.304] (**) Option "xkb_model" "pc105"
[    24.304] (**) Option "xkb_layout" "us"
[    24.307] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    24.307] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    24.307] (II) Using input driver 'evdev' for 'Sleep Button'
[    24.307] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.307] (**) Sleep Button: always reports core events
[    24.307] (**) Sleep Button: Device: "/dev/input/event1"
[    24.307] (--) Sleep Button: Found keys
[    24.308] (II) Sleep Button: Configuring as keyboard
[    24.308] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    24.308] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    24.308] (**) Option "xkb_rules" "evdev"
[    24.308] (**) Option "xkb_model" "pc105"
[    24.308] (**) Option "xkb_layout" "us"
[    24.378] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    24.378] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    24.378] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    24.378] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.378] (**) AT Translated Set 2 keyboard: always reports core events
[    24.378] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    24.379] (--) AT Translated Set 2 keyboard: Found keys
[    24.379] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    24.379] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    24.379] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    24.379] (**) Option "xkb_rules" "evdev"
[    24.379] (**) Option "xkb_model" "pc105"
[    24.379] (**) Option "xkb_layout" "us"
[    24.386] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    24.386] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    24.386] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    24.386] (II) LoadModule: "synaptics"
[    24.387] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    24.410] (II) Module synaptics: vendor="X.Org Foundation"
[    24.410] 	compiled for 1.10.0.902, module version = 1.3.99
[    24.410] 	Module class: X.Org XInput Driver
[    24.411] 	ABI class: X.Org XInput driver, version 12.3
[    24.411] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    24.411] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    24.411] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.411] (**) Option "Device" "/dev/input/event5"
[    24.411] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    24.411] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    24.411] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    24.411] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    24.412] (--) SynPS/2 Synaptics TouchPad: invalid finger width range.  defaulting to 0 - 16
[    24.412] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    24.412] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.412] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input5/event5"
[    24.412] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    24.412] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    24.412] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    24.412] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    24.413] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    24.413] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    24.413] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    24.413] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    24.414] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    24.414] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    24.415] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    24.415] (II) No input driver/identifier specified (ignoring)
[   431.546] (II) XKB: generating xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm

```

---

### Post by Krytarik on 2011-05-30
So, you are definitely running exactly the same driver before and after the installation. And the Xorg.0.log's seem to be almost the same, too. So, it's really weird that you get your desired resolution before but not after installation.

I did a bit of web search regarding the repeated "FBDEV" errors being logged, and your chipset in general. Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1748717](http://ubuntuforums.org/showthread.php?t=1748717)

As you noticed, setting up an xorg.conf with the "intel" driver specified does make a difference in the Monitor settings. Set up a minimum xorg.conf, then try adding/setting the desired video mode with xrandr.

---

### Post by sweBers on 2011-05-31
> **Krytarik said:**
> So, you are definitely running exactly the same driver before and after the installation. And the Xorg.0.log's seem to be almost the same, too. So, it's really weird that you get your desired resolution before but not after installation.

I did a bit of web search regarding the repeated "FBDEV" errors being logged, and your chipset in general. Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1748717](http://ubuntuforums.org/showthread.php?t=1748717)

As you noticed, setting up an xorg.conf with the "intel" driver specified does make a difference in the Monitor settings. Set up a minimum xorg.conf, then try adding/setting the desired video mode with xrandr.

Thanks!  I saw that being output and will try that.  I did notice that the install was not properly probing my ACPI settings versus the live CD:

```

[   313.498] (--) PCI:*(0:0:2:0) 8086:2562:1584:9000 rev 3, Mem @ 0xd0000000/134217728, 0xdff80000/524288
[   313.501] (II) Open ACPI successful (/var/run/acpid.socket)
[   313.502] (II) LoadModule: "extmod"

```

```

[    22.695] (--) PCI:*(0:0:2:0) 8086:2562:1584:9000 rev 3, Mem @ 0xd0000000/134217728, 0xdff80000/524288
[    22.695] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.695] (II) LoadModule: "extmod"

```

It doesn't seem to be an issue now, as my machine did not have that same error today.

I can also see where the different modes were chosen:
```

[   325.218] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   325.219] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[   325.219] (II) FBDEV(0): using default device
[   325.219] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   325.219] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   325.219] (==) FBDEV(0): RGB weight 888
[   325.219] (==) FBDEV(0): Default visual is TrueColor
[   325.219] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   325.224] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[   325.224] (II) FBDEV(0): checking modes against framebuffer device...
[   325.224] (II) FBDEV(0): checking modes against monitor...
[   325.224] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[   325.224] (**) FBDEV(0):  Built-in mode "current"

```

```

[    22.800] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    22.800] (II) FBDEV(0): using default device
[    22.800] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.800] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    22.800] (==) FBDEV(0): RGB weight 888
[    22.801] (==) FBDEV(0): Default visual is TrueColor
[    22.801] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.801] (II) FBDEV(0): hardware: inteldrmfb (video memory: 1200kB)
[    22.801] (II) FBDEV(0): checking modes against framebuffer device...
[    22.801] (II) FBDEV(0): checking modes against monitor...
[    22.801] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    22.801] (**) FBDEV(0):  Built-in mode "current"
[    22.801] (==) FBDEV(0): DPI set to (96, 96)

```

If these suggestions solve the FBDEV problems, I'm almost willing to bet that all my problem will be solved.

---

### Post by sweBers on 2011-05-31
so, I was trying to rebuild my xorg.conf because xrandr was not working.  Here is what I am using now that doesn't seem to be doing anything for me:

```

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection 

```

Here is what I am trying to use:

```

Section "Device"
	Identifier "Intel(r)845G/845GL/845GE/845GV Graphics Controller"
	Driver "intel"       
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier "Laptop Display" 
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Laptop Display"
	Device "Intel(r)845G/845GL/845GE/845GV Graphics Controller"      
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"       		EndSubSection

EndSection 

   Section "ServerLayout"
       Identifier	"Default Layout"
       Screen		"Default Screen"
       InputDevice	"Generic Keyboard"
       InputDevice	"Configured Mouse"
       InputDevice     "stylus"	"SendCoreEvents"
       InputDevice     "cursor"	"SendCoreEvents"
       InputDevice     "eraser"	"SendCoreEvents"
       InputDevice	"Synaptics Touchpad"
   EndSection

```

When I try using xrandr with the one first one, I get error messages.  I need to reboot from low graphics mode in order to show you the output.  When I boot into the second one, it looks like it is trying to load it as 1024x768, but the screen blanks.  It accepts commands, typing blind, and will allow me to us ctrl+alt+del.

---

### Post by sweBers on 2011-05-31
So, I got 1024X768 resolution after rebooting using the first setting.  The thing that disturbs me is that I've booted using these settings before, so I'm certain that it will break again.  I have only seen this happen when I reboot from low resolution graphics mode to a regular boot, and it tends to freeze.  I won't mark this as solved unless I get several boots at 1024X768.  Here is what happened at boot:

```

[    18.062] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    18.062] X Protocol Version 11, Revision 0
[    18.062] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    18.062] Current Operating System: Linux Gericom-Hummer 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    18.062] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=6c0a3911-4611-42cd-9e63-885f4ae9ff1a ro quiet splash i915.nomodeset vt.handoff=7
[    18.062] Build Date: 21 May 2011  11:38:35AM
[    18.063] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    18.063] Current version of pixman: 0.20.2
[    18.063] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.063] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.063] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 31 10:46:22 2011
[    18.078] (==) Using config file: "/etc/X11/xorg.conf"
[    18.078] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.086] (==) No Layout section.  Using the first Screen section.
[    18.086] (**) |-->Screen "Default Screen" (0)
[    18.086] (**) |   |-->Monitor "Configured Monitor"
[    18.087] (**) |   |-->Device "Configured Video Device"
[    18.087] (==) Automatically adding devices
[    18.087] (==) Automatically enabling devices
[    18.087] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.087] 	Entry deleted from font path.
[    18.088] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.088] 	Entry deleted from font path.
[    18.088] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.088] 	Entry deleted from font path.
[    18.088] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.088] 	Entry deleted from font path.
[    18.088] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.088] 	Entry deleted from font path.
[    18.088] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.088] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.088] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.088] (II) Loader magic: 0x81ffde0
[    18.089] (II) Module ABI versions:
[    18.089] 	X.Org ANSI C Emulation: 0.4
[    18.089] 	X.Org Video Driver: 10.0
[    18.089] 	X.Org XInput driver : 12.3
[    18.089] 	X.Org Server Extension : 5.0
[    18.091] (--) PCI:*(0:0:2:0) 8086:2562:1584:9000 rev 3, Mem @ 0xd0000000/134217728, 0xdff80000/524288
[    18.103] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.104] (II) LoadModule: "extmod"
[    18.108] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.108] (II) Module extmod: vendor="X.Org Foundation"
[    18.109] 	compiled for 1.10.1, module version = 1.0.0
[    18.109] 	Module class: X.Org Server Extension
[    18.109] 	ABI class: X.Org Server Extension, version 5.0
[    18.109] (II) Loading extension MIT-SCREEN-SAVER
[    18.109] (II) Loading extension XFree86-VidModeExtension
[    18.109] (II) Loading extension XFree86-DGA
[    18.109] (II) Loading extension DPMS
[    18.109] (II) Loading extension XVideo
[    18.109] (II) Loading extension XVideo-MotionCompensation
[    18.109] (II) Loading extension X-Resource
[    18.109] (II) LoadModule: "dbe"
[    18.109] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.110] (II) Module dbe: vendor="X.Org Foundation"
[    18.110] 	compiled for 1.10.1, module version = 1.0.0
[    18.110] 	Module class: X.Org Server Extension
[    18.110] 	ABI class: X.Org Server Extension, version 5.0
[    18.110] (II) Loading extension DOUBLE-BUFFER
[    18.110] (II) LoadModule: "glx"
[    18.111] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.111] (II) Module glx: vendor="X.Org Foundation"
[    18.111] 	compiled for 1.10.1, module version = 1.0.0
[    18.111] 	ABI class: X.Org Server Extension, version 5.0
[    18.118] (==) AIGLX enabled
[    18.118] (II) Loading extension GLX
[    18.118] (II) LoadModule: "record"
[    18.118] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.119] (II) Module record: vendor="X.Org Foundation"
[    18.119] 	compiled for 1.10.1, module version = 1.13.0
[    18.119] 	Module class: X.Org Server Extension
[    18.119] 	ABI class: X.Org Server Extension, version 5.0
[    18.119] (II) Loading extension RECORD
[    18.119] (II) LoadModule: "dri"
[    18.120] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.120] (II) Module dri: vendor="X.Org Foundation"
[    18.121] 	compiled for 1.10.1, module version = 1.0.0
[    18.121] 	ABI class: X.Org Server Extension, version 5.0
[    18.121] (II) Loading extension XFree86-DRI
[    18.121] (II) LoadModule: "dri2"
[    18.121] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.122] (II) Module dri2: vendor="X.Org Foundation"
[    18.122] 	compiled for 1.10.1, module version = 1.2.0
[    18.122] 	ABI class: X.Org Server Extension, version 5.0
[    18.122] (II) Loading extension DRI2
[    18.122] (II) LoadModule: "intel"
[    18.144] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.167] (II) Module intel: vendor="X.Org Foundation"
[    18.167] 	compiled for 1.10.1, module version = 2.14.0
[    18.167] 	Module class: X.Org Video Driver
[    18.167] 	ABI class: X.Org Video Driver, version 10.0
[    18.168] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    18.170] (++) using VT number 7

[    18.193] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.194] drmOpenDevice: node name is /dev/dri/card0
[    18.194] drmOpenDevice: open result is 9, (OK)
[    18.194] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    18.194] drmOpenDevice: node name is /dev/dri/card0
[    18.194] drmOpenDevice: open result is 9, (OK)
[    18.194] drmOpenByBusid: drmOpenMinor returns 9
[    18.194] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    18.195] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    18.195] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.195] (==) intel(0): RGB weight 888
[    18.195] (==) intel(0): Default visual is TrueColor
[    18.195] (II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
[    18.195] (--) intel(0): Chipset: "845G"
[    18.195] (**) intel(0): Relaxed fencing disabled
[    18.195] (**) intel(0): Tiling enabled
[    18.195] (**) intel(0): SwapBuffers wait enabled
[    18.218] (==) intel(0): video overlay key set to 0x101fe
[    18.301] (II) intel(0): Output VGA1 using monitor section Configured Monitor
[    18.317] (II) intel(0): Output LVDS1 has no monitor section
[    18.365] (II) intel(0): EDID for output VGA1
[    18.365] (II) intel(0): Not using default mode "640x350" (vrefresh out of range)
[    18.365] (II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
[    18.365] (II) intel(0): Not using default mode "640x400" (vrefresh out of range)
[    18.365] (II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "720x400" (vrefresh out of range)
[    18.366] (II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    18.366] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    18.366] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "640x480" (vrefresh out of range)
[    18.366] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    18.366] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    18.366] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    18.366] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.366] (II) intel(0): Not using default mode "800x600" (vrefresh out of range)
[    18.367] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1024x768i" (vrefresh out of range)
[    18.367] (II) intel(0): Not using default mode "512x384i" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    18.367] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    18.367] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
[    18.367] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    18.367] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1280x960" (hsync out of range)
[    18.367] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
[    18.367] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.367] (II) intel(0): Not using default mode "1280x1024" (hsync out of range)
[    18.373] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.373] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    18.373] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.373] (II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
[    18.373] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.373] (II) intel(0): Not using default mode "1600x1200" (hsync out of range)
[    18.373] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.373] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    18.373] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.373] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    18.373] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.373] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    18.373] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.373] (II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
[    18.373] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.374] (II) intel(0): Not using default mode "1792x1344" (hsync out of range)
[    18.374] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.374] (II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
[    18.374] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.374] (II) intel(0): Not using default mode "1856x1392" (hsync out of range)
[    18.384] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.384] (II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
[    18.384] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.384] (II) intel(0): Not using default mode "1920x1440" (hsync out of range)
[    18.384] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.384] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    18.384] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "832x624" (vrefresh out of range)
[    18.385] (II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    18.385] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    18.385] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    18.385] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    18.385] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
[    18.385] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    18.385] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.385] (II) intel(0): Not using default mode "1400x1050" (hsync out of range)
[    18.386] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    18.386] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    18.386] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
[    18.386] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1440x900" (hsync out of range)
[    18.386] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1600x1024" (hsync out of range)
[    18.386] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    18.386] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1680x1050" (hsync out of range)
[    18.386] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    18.386] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.386] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    18.387] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.387] (II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
[    18.387] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.387] (II) intel(0): Not using default mode "1920x1080" (hsync out of range)
[    18.387] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.387] (II) intel(0): Not using default mode "1920x1200" (hsync out of range)
[    18.387] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.387] (II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
[    18.387] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.387] (II) intel(0): Not using default mode "2048x1536" (hsync out of range)
[    18.387] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.387] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    18.387] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.387] (II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
[    18.387] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.410] (II) intel(0): Printing probed modes for output VGA1
[    18.410] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.410] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    18.410] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.410] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.410] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.421] (II) intel(0): EDID for output LVDS1
[    18.422] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.422] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.423] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.423] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.423] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.423] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.423] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.423] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.423] (II) intel(0): Printing probed modes for output LVDS1
[    18.423] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 (48.4 kHz)
[    18.423] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.423] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.423] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.423] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.423] (II) intel(0): Output VGA1 disconnected
[    18.423] (II) intel(0): Output LVDS1 connected
[    18.432] (II) intel(0): Using exact sizes for initial modes
[    18.432] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    18.432] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.432] (II) intel(0): Kernel page flipping support detected, enabling
[    18.432] (==) intel(0): DPI set to (96, 96)
[    18.432] (II) Loading sub module "fb"
[    18.432] (II) LoadModule: "fb"
[    18.434] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.434] (II) Module fb: vendor="X.Org Foundation"
[    18.434] 	compiled for 1.10.1, module version = 1.0.0
[    18.434] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.434] (==) Depth 24 pixmap format is 32 bpp
[    18.435] (==) intel(0): VideoRam: 131072 KB
[    18.435] (II) intel(0): [DRI2] Setup complete
[    18.435] (II) intel(0): [DRI2]   DRI driver: i915
[    18.435] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    18.446] (II) UXA(0): Driver registered support for the following operations:
[    18.446] (II)         solid
[    18.446] (II)         copy
[    18.446] (II)         composite (RENDER acceleration)
[    18.447] (II)         put_image
[    18.447] (II)         get_image
[    18.447] (==) intel(0): Backing store disabled
[    18.447] (==) intel(0): Silken mouse enabled
[    18.447] (II) intel(0): Initializing HW Cursor
[    18.584] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.584] (==) intel(0): DPMS enabled
[    18.584] (==) intel(0): Intel XvMC decoder disabled
[    18.585] (II) intel(0): Set up overlay video
[    18.585] (II) intel(0): direct rendering: DRI2 Enabled
[    18.585] (==) intel(0): hotplug detection: "enabled"
[    18.585] (--) RandR disabled
[    18.585] (II) Initializing built-in extension Generic Event Extension
[    18.585] (II) Initializing built-in extension SHAPE
[    18.586] (II) Initializing built-in extension MIT-SHM
[    18.586] (II) Initializing built-in extension XInputExtension
[    18.586] (II) Initializing built-in extension XTEST
[    18.586] (II) Initializing built-in extension BIG-REQUESTS
[    18.586] (II) Initializing built-in extension SYNC
[    18.586] (II) Initializing built-in extension XKEYBOARD
[    18.586] (II) Initializing built-in extension XC-MISC
[    18.586] (II) Initializing built-in extension SECURITY
[    18.586] (II) Initializing built-in extension XINERAMA
[    18.586] (II) Initializing built-in extension XFIXES
[    18.586] (II) Initializing built-in extension RENDER
[    18.586] (II) Initializing built-in extension RANDR
[    18.586] (II) Initializing built-in extension COMPOSITE
[    18.586] (II) Initializing built-in extension DAMAGE
[    18.586] (II) Initializing built-in extension GESTURE
[    18.611] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    18.657] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.657] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.658] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.658] (II) AIGLX: enabled GLX_SGI_make_current_read
[    18.658] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.658] (II) AIGLX: Loaded and initialized i915
[    18.658] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.660] (II) intel(0): Setting screen physical size to 270 x 203
[    18.689] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.730] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    18.730] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.730] (II) LoadModule: "evdev"
[    18.732] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.734] (II) Module evdev: vendor="X.Org Foundation"
[    18.734] 	compiled for 1.10.0.902, module version = 2.6.0
[    18.734] 	Module class: X.Org XInput Driver
[    18.734] 	ABI class: X.Org XInput driver, version 12.3
[    18.734] (II) Using input driver 'evdev' for 'Power Button'
[    18.734] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.734] (**) Power Button: always reports core events
[    18.734] (**) Power Button: Device: "/dev/input/event3"
[    18.735] (--) Power Button: Found keys
[    18.735] (II) Power Button: Configuring as keyboard
[    18.735] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    18.735] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.735] (**) Option "xkb_rules" "evdev"
[    18.735] (**) Option "xkb_model" "pc105"
[    18.735] (**) Option "xkb_layout" "us"
[    18.764] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    18.764] (II) No input driver/identifier specified (ignoring)
[    18.767] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.767] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.767] (II) Using input driver 'evdev' for 'Power Button'
[    18.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.768] (**) Power Button: always reports core events
[    18.768] (**) Power Button: Device: "/dev/input/event2"
[    18.768] (--) Power Button: Found keys
[    18.768] (II) Power Button: Configuring as keyboard
[    18.768] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2"
[    18.768] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.768] (**) Option "xkb_rules" "evdev"
[    18.768] (**) Option "xkb_model" "pc105"
[    18.768] (**) Option "xkb_layout" "us"
[    18.771] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    18.771] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.771] (II) Using input driver 'evdev' for 'Sleep Button'
[    18.771] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.771] (**) Sleep Button: always reports core events
[    18.771] (**) Sleep Button: Device: "/dev/input/event1"
[    18.772] (--) Sleep Button: Found keys
[    18.772] (II) Sleep Button: Configuring as keyboard
[    18.772] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    18.772] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    18.772] (**) Option "xkb_rules" "evdev"
[    18.772] (**) Option "xkb_model" "pc105"
[    18.772] (**) Option "xkb_layout" "us"
[    18.814] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.814] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.814] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.814] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.814] (**) AT Translated Set 2 keyboard: always reports core events
[    18.814] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.814] (--) AT Translated Set 2 keyboard: Found keys
[    18.815] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.815] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    18.815] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.815] (**) Option "xkb_rules" "evdev"
[    18.815] (**) Option "xkb_model" "pc105"
[    18.815] (**) Option "xkb_layout" "us"
[    18.818] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    18.818] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.818] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.818] (II) LoadModule: "synaptics"
[    18.819] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.820] (II) Module synaptics: vendor="X.Org Foundation"
[    18.820] 	compiled for 1.10.0.902, module version = 1.3.99
[    18.820] 	Module class: X.Org XInput Driver
[    18.820] 	ABI class: X.Org XInput driver, version 12.3
[    18.820] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.820] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.820] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.820] (**) Option "Device" "/dev/input/event5"
[    18.821] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    18.821] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    18.821] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.821] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    18.821] (--) SynPS/2 Synaptics TouchPad: invalid finger width range.  defaulting to 0 - 16
[    18.821] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.821] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.821] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input5/event5"
[    18.821] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.822] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.822] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    18.822] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    18.822] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.822] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.822] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.823] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.823] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    18.823] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.824] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    18.824] (II) No input driver/identifier specified (ignoring)
[  2288.027] (EE) intel(0): Detected a hung GPU, disabling acceleration.
[  2367.839] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.840] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.841] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.841] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.841] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.842] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.843] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.843] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.843] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.847] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.848] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.848] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.848] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.849] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.849] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.849] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.849] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.849] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.849] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.850] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.850] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.850] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.850] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2367.852] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.073] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.074] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.074] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.075] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.075] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.076] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.077] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.077] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.077] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.078] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.078] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.082] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.082] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2368.794] (EE) intel(0): failed to set cursor: Input/output error
[  2368.806] (EE) intel(0): failed to set cursor: Input/output error
[  2369.250] (EE) intel(0): failed to set cursor: Input/output error
[  2369.262] (EE) intel(0): failed to set cursor: Input/output error
[  2369.703] (EE) intel(0): failed to set cursor: Input/output error
[  2369.731] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2369.731] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2369.731] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2369.732] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2369.732] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.506] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.507] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.525] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.527] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.527] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.542] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.544] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.544] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.559] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.561] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.561] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.575] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.578] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.578] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.593] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.595] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.595] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.609] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.610] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.611] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.928] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.930] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2370.930] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.123] (EE) intel(0): failed to set cursor: Input/output error
[  2372.124] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.155] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.156] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.156] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.156] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.156] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.156] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.198] (EE) intel(0): failed to set cursor: Input/output error
[  2372.214] (EE) intel(0): failed to set cursor: Input/output error
[  2372.233] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.235] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.235] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.394] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.395] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.789] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2372.789] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2374.535] (EE) intel(0): failed to set cursor: Input/output error
[  2374.576] (EE) intel(0): failed to set cursor: Input/output error
[  2374.763] (EE) intel(0): failed to set cursor: Input/output error
[  2374.782] (EE) intel(0): failed to set cursor: Input/output error
[  2374.815] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2374.815] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2374.815] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2374.815] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2374.816] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.427] (EE) intel(0): failed to set cursor: Input/output error
[  2375.456] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.456] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.456] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.457] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.457] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.551] (EE) intel(0): failed to set cursor: Input/output error
[  2375.580] (EE) intel(0): failed to set cursor: Input/output error
[  2375.609] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.609] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.609] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.609] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.711] (EE) intel(0): failed to set cursor: Input/output error
[  2375.741] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.742] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.742] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.742] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2375.826] (EE) intel(0): failed to set cursor: Input/output error
[  2376.822] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.824] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.837] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.867] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.868] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.869] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.870] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.871] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.871] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.871] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.872] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.876] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.876] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.877] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.878] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.878] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.878] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.879] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.879] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.882] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.888] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.888] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.889] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.889] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.889] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.889] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.889] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.889] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.890] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.890] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.890] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.890] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.901] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.901] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.910] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.968] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.969] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.971] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.972] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.972] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.972] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.972] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.972] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.973] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.973] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.973] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.974] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.974] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2376.976] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.050] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.053] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.081] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.082] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.085] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.085] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.086] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.086] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.092] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.092] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.093] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.093] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.094] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.094] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.095] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.095] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.095] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.095] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.097] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.097] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.097] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.097] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.097] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.104] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.104] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.105] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.105] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.105] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.125] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.157] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.158] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.161] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.161] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.161] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.161] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.162] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.162] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.162] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.162] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.162] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.164] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.164] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.164] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.816] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.899] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.902] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.930] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.931] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.932] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.933] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.934] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.934] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.934] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.935] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.940] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.940] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.941] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.942] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.942] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.942] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.943] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.943] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.945] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.945] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.946] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.946] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.946] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.946] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.946] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.946] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.952] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.952] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.952] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.953] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.953] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2377.976] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.012] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.013] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.016] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.016] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.016] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.016] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.017] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.017] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.017] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.017] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.017] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.018] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.018] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.019] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2378.689] (EE) intel(0): failed to set cursor: Input/output error
[  2378.915] (EE) intel(0): failed to set cursor: Input/output error
[  2378.926] (EE) intel(0): failed to set cursor: Input/output error
[  2379.255] (EE) intel(0): failed to set cursor: Input/output error
[  2379.269] (EE) intel(0): failed to set cursor: Input/output error
[  2379.274] (EE) intel(0): failed to set cursor: Input/output error
[  2379.306] (EE) intel(0): failed to set cursor: Input/output error
[  2379.330] (EE) intel(0): failed to set cursor: Input/output error
[  2379.352] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.352] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.352] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.352] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.373] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.373] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.850] (EE) intel(0): failed to set cursor: Input/output error
[  2379.883] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.884] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.940] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.941] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.941] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2379.942] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.821] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.822] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.822] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.822] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.823] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.823] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.823] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.836] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.844] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.847] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.868] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.924] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.925] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.947] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.947] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.948] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.949] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.983] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.984] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2380.984] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.001] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.001] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.001] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.490] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.490] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.490] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.535] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.537] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.537] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.537] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.537] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.537] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2381.539] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.157] (EE) intel(0): failed to set cursor: Input/output error
[  2382.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.168] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.181] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.181] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.193] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.193] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.214] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.214] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.631] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.631] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.648] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.648] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.649] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.663] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.663] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2382.663] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.683] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.684] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.684] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.710] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.711] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.711] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.746] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2383.747] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2384.868] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2384.870] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2385.786] (EE) intel(0): failed to set cursor: Input/output error
[  2385.791] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2385.792] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2385.798] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2385.799] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2385.812] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2385.812] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2385.816] (EE) intel(0): failed to set cursor: Input/output error
[  2385.846] (EE) intel(0): failed to set cursor: Input/output error
[  2385.877] (EE) intel(0): failed to set cursor: Input/output error
[  2385.907] (EE) intel(0): failed to set cursor: Input/output error
[  2385.937] (EE) intel(0): failed to set cursor: Input/output error
[  2385.967] (EE) intel(0): failed to set cursor: Input/output error
[  2385.997] (EE) intel(0): failed to set cursor: Input/output error
[  2386.027] (EE) intel(0): failed to set cursor: Input/output error
[  2386.057] (EE) intel(0): failed to set cursor: Input/output error
[  2386.088] (EE) intel(0): failed to set cursor: Input/output error
[  2386.118] (EE) intel(0): failed to set cursor: Input/output error
[  2386.148] (EE) intel(0): failed to set cursor: Input/output error
[  2386.179] (EE) intel(0): failed to set cursor: Input/output error
[  2386.208] (EE) intel(0): failed to set cursor: Input/output error
[  2386.239] (EE) intel(0): failed to set cursor: Input/output error
[  2386.260] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.260] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.268] (EE) intel(0): failed to set cursor: Input/output error
[  2386.299] (EE) intel(0): failed to set cursor: Input/output error
[  2386.329] (EE) intel(0): failed to set cursor: Input/output error
[  2386.359] (EE) intel(0): failed to set cursor: Input/output error
[  2386.390] (EE) intel(0): failed to set cursor: Input/output error
[  2386.419] (EE) intel(0): failed to set cursor: Input/output error
[  2386.449] (EE) intel(0): failed to set cursor: Input/output error
[  2386.480] (EE) intel(0): failed to set cursor: Input/output error
[  2386.511] (EE) intel(0): failed to set cursor: Input/output error
[  2386.542] (EE) intel(0): failed to set cursor: Input/output error
[  2386.572] (EE) intel(0): failed to set cursor: Input/output error
[  2386.603] (EE) intel(0): failed to set cursor: Input/output error
[  2386.633] (EE) intel(0): failed to set cursor: Input/output error
[  2386.664] (EE) intel(0): failed to set cursor: Input/output error
[  2386.666] (EE) intel(0): failed to set cursor: Input/output error
[  2386.684] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.684] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.688] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.688] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.989] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.989] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2386.990] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.094] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.098] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.101] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.101] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.107] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.107] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.149] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.150] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.150] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.235] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.236] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.236] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.362] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.362] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.362] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.566] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.765] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.766] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2387.766] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2388.144] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2388.792] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2390.003] (EE) intel(0): failed to set cursor: Input/output error
[  2390.022] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2390.133] (EE) intel(0): failed to set cursor: Input/output error
[  2390.223] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2390.724] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2390.746] (EE) intel(0): failed to set cursor: Input/output error
[  2391.413] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2391.496] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2393.775] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2394.241] (EE) intel(0): failed to set cursor: Input/output error
[  2394.264] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2396.301] (EE) intel(0): failed to set cursor: Input/output error
[  2396.385] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2397.329] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2397.329] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2397.330] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2399.122] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2399.130] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2399.712] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2400.172] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2400.264] (EE) intel(0): failed to set cursor: Input/output error
[  2400.342] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2400.348] (EE) intel(0): failed to set cursor: Input/output error
[  2400.372] (EE) intel(0): failed to set cursor: Input/output error
[  2400.400] (EE) intel(0): failed to set cursor: Input/output error
[  2400.424] (EE) intel(0): failed to set cursor: Input/output error
[  2400.546] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2401.190] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2406.355] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2406.356] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2406.357] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2406.706] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2406.712] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2406.712] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2406.714] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2407.642] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2407.643] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.907] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.909] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.910] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.910] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.910] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.910] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.910] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.910] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.911] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.911] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2408.918] (EE) intel(0): failed to set cursor: Input/output error
[  2409.899] (EE) intel(0): failed to set cursor: Input/output error
[  2410.666] (EE) intel(0): failed to set cursor: Input/output error
[  2410.698] (EE) intel(0): failed to set cursor: Input/output error
[  2414.273] (EE) intel(0): failed to set cursor: Input/output error
[  2415.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2415.518] (EE) intel(0): failed to set cursor: Input/output error
[  2416.737] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2416.738] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2416.738] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2417.287] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.388] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.400] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.401] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.401] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.401] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.401] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.401] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.402] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.402] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.402] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.402] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.403] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.403] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.403] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.976] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.985] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.985] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.985] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.985] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.985] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.986] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.986] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.986] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.986] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.987] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.987] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.987] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2418.988] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.011] (EE) intel(0): failed to set cursor: Input/output error
[  2419.095] (EE) intel(0): failed to set cursor: Input/output error
[  2419.593] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.600] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.601] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.601] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.601] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.601] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.601] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.602] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.602] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.602] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.602] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.603] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.603] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2419.603] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.157] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.164] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.164] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.165] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.165] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.165] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.165] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.165] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.166] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.166] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.166] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.167] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.791] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.798] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.799] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.799] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.799] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.799] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.799] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.800] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.800] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.800] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.800] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.801] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.801] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2420.801] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.325] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.331] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.332] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.332] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.332] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.332] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.333] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.333] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.333] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.333] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.334] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.334] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.334] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.334] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.617] (EE) intel(0): failed to set cursor: Input/output error
[  2421.650] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.985] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.993] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.993] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.993] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.995] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.995] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.996] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2421.996] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2422.209] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2485.477] (EE) intel(0): failed to set cursor: Input/output error
[  2485.575] (EE) intel(0): failed to set cursor: Input/output error
[  2485.608] (EE) intel(0): failed to set cursor: Input/output error
[  2487.991] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2491.062] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2491.566] (EE) intel(0): failed to set cursor: Input/output error
[  2491.579] (EE) intel(0): failed to set cursor: Input/output error
[  2491.888] (EE) intel(0): failed to set cursor: Input/output error
[  2491.919] (EE) intel(0): failed to set cursor: Input/output error
[  2491.960] (EE) intel(0): failed to set cursor: Input/output error
[  2492.086] (EE) intel(0): failed to set cursor: Input/output error
[  2492.194] (EE) intel(0): failed to set cursor: Input/output error
[  2492.769] (EE) intel(0): failed to set cursor: Input/output error
[  2493.212] (EE) intel(0): failed to set cursor: Input/output error
[  2493.897] (EE) intel(0): failed to set cursor: Input/output error
[  2493.943] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2493.944] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2494.027] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2494.028] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2494.028] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2494.307] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2494.309] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2494.527] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2495.113] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2495.114] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2495.118] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2496.872] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2496.881] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2496.888] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2496.911] (EE) intel(0): failed to set cursor: Input/output error
[  2497.409] (EE) intel(0): failed to set cursor: Input/output error
[  2497.992] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2498.002] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2498.010] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2498.798] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2498.807] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2498.814] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.169] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.228] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.346] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.347] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.403] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.406] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.822] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2499.905] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.026] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.027] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.125] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.127] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.130] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.131] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.237] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.238] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.239] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.244] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.252] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.253] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.254] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.434] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.441] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.980] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2500.981] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.072] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.072] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.084] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.085] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.171] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.172] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.174] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.174] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.175] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.175] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.175] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.175] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.175] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.175] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.176] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.177] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.236] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2501.324] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2502.622] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2502.622] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2502.720] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2502.720] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2502.765] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.787] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.790] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.791] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.792] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.799] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.800] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.800] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2503.880] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.006] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.559] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.733] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.739] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.741] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.745] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.746] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2504.928] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2506.282] (EE) intel(0): failed to set cursor: Input/output error
[  2506.298] (EE) intel(0): failed to set cursor: Input/output error
[  2506.303] (EE) intel(0): failed to set cursor: Input/output error
[  2506.344] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2506.346] (EE) intel(0): failed to set cursor: Input/output error
[  2506.370] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2506.370] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2507.623] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2507.624] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2508.307] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2508.308] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2508.816] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2508.816] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2508.817] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2508.842] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2508.843] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2509.202] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2509.217] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2509.218] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2511.998] (EE) intel(0): failed to set cursor: Input/output error
[  2512.004] (EE) intel(0): failed to set cursor: Input/output error
[  2512.111] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.111] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.112] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.132] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.133] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.485] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.493] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.494] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2512.511] (EE) intel(0): failed to set cursor: Input/output error
[  2513.221] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2513.221] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2513.265] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2513.265] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2513.359] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2513.359] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2513.370] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.514] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.515] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.640] (EE) intel(0): failed to set cursor: Input/output error
[  2514.856] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.856] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.864] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.865] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.916] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.917] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.917] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.963] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.963] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.985] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.993] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2514.994] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.032] (EE) intel(0): failed to set cursor: Input/output error
[  2515.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.083] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.439] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.439] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.547] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.547] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.548] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.581] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2515.582] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2516.155] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2516.178] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2516.190] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2517.204] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2517.204] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2517.204] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.191] (EE) intel(0): failed to set cursor: Input/output error
[  2533.448] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.449] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.450] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.451] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.454] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.455] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.559] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.560] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2533.570] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2534.034] (EE) intel(0): failed to set cursor: Input/output error
[  2534.043] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2534.044] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error
[  2534.044] (WW) intel(0): intel_uxa_prepare_access: bo map failed: Input/output error

```

---

### Post by sweBers on 2011-05-31
Just to clarify, I have not been able to boot into 1024X768.  Using xrandr to try all refresh rates from 65 to 40, I kept getting the following errors:

```

swebers@Gericom-Hummer:~$ cvt 1024 768 65
# 1024x768 64.87 Hz (CVT) hsync: 51.90 kHz; pclk: 69.75 MHz
Modeline "1024x768_65.00"   69.75  1024 1080 1184 1344  768 771 775 800 -hsync +vsync

swebers@Gericom-Hummer:~$ xrandr --newmode "LCD" 69.75  1024 1080 1184 1344  768 771 775 800 -hsync +vsync

swebers@Gericom-Hummer:~$ xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9  
  LCD (0xae)   69.8MHz
        h: width  1024 start 1080 end 1184 total 1344 skew    0 clock   51.9KHz
        v: height  768 start  771 end  775 total  800           clock   64.9Hz
swebers@Gericom-Hummer:~$ xrandr --addmode LVDS1 LCD
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  22
  Current serial number in output stream:  23

```

---

