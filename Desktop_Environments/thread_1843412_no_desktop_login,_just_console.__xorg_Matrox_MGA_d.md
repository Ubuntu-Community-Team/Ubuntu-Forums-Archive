---
title: "no desktop login, just console.  xorg Matrox MGA driver fails to initialize"
date: 2011-09-13
forum: Desktop Environments
---

### Post by bcavagnolo on 2011-09-13
Hey guys,

I've got some fancy new servers, and they came with 10.04.  I upgraded to 10.10 and everything still worked.  Then I upgraded to 11.04 and I only get the terminal, no GUI login screen.  I googled around, and it looks like lots of nvidia users had this same problem.  I tried some of the proposed solutions (e.g., pass nomodeset to the kernel), but nothing works.

I dug a bit deeper, and it seems that X is not launching.  I've pasted the log below.  The (EE) lines seem to indicate a problem loading the matrox mga driver, but I'm not sure what to try next.  Please advise.

Thanks,
Brian
```

[    13.293] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.293] X Protocol Version 11, Revision 0
[    13.293] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    13.293] Current Operating System: Linux london 2.6.38-11-server #48-Ubuntu SMP Fri Jul 29 19:20:32 UTC 2011 x86_64
[    13.293] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-11-server root=UUID=968aa190-60b4-4529-a05b-8a8d6563ba73 ro quiet nomodeset
[    13.293] Build Date: 11 August 2011  03:43:05PM
[    13.293] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.293] Current version of pixman: 0.20.2
[    13.293] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    13.293] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.293] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 12 15:30:30 2011
[    13.298] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.298] (==) No Layout section.  Using the first Screen section.
[    13.298] (==) No screen section available. Using defaults.
[    13.298] (**) |-->Screen "Default Screen Section" (0)
[    13.298] (**) |   |-->Monitor "<default monitor>"
[    13.298] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    13.298] (==) Automatically adding devices
[    13.298] (==) Automatically enabling devices
[    13.321] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.321] 	Entry deleted from font path.
[    13.321] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.321] 	Entry deleted from font path.
[    13.321] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.321] 	Entry deleted from font path.
[    13.321] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.321] 	Entry deleted from font path.
[    13.321] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.321] 	Entry deleted from font path.
[    13.331] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    13.331] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.331] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.331] (II) Loader magic: 0x7e17e0
[    13.331] (II) Module ABI versions:
[    13.331] 	X.Org ANSI C Emulation: 0.4
[    13.331] 	X.Org Video Driver: 10.0
[    13.331] 	X.Org XInput driver : 12.3
[    13.331] 	X.Org Server Extension : 5.0
[    13.332] (--) PCI:*(0:7:4:0) 102b:0532:15d9:0100 rev 10, Mem @ 0xf9000000/16777216, 0xfa200000/16384
[    13.332] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.332] (II) LoadModule: "extmod"
[    13.338] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.339] (II) Module extmod: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.10.1, module version = 1.0.0
[    13.339] 	Module class: X.Org Server Extension
[    13.339] 	ABI class: X.Org Server Extension, version 5.0
[    13.339] (II) Loading extension MIT-SCREEN-SAVER
[    13.339] (II) Loading extension XFree86-VidModeExtension
[    13.339] (II) Loading extension XFree86-DGA
[    13.339] (II) Loading extension DPMS
[    13.339] (II) Loading extension XVideo
[    13.339] (II) Loading extension XVideo-MotionCompensation
[    13.339] (II) Loading extension X-Resource
[    13.339] (II) LoadModule: "dbe"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.339] (II) Module dbe: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.10.1, module version = 1.0.0
[    13.339] 	Module class: X.Org Server Extension
[    13.339] 	ABI class: X.Org Server Extension, version 5.0
[    13.339] (II) Loading extension DOUBLE-BUFFER
[    13.339] (II) LoadModule: "glx"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.339] (II) Module glx: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.10.1, module version = 1.0.0
[    13.339] 	ABI class: X.Org Server Extension, version 5.0
[    13.339] (==) AIGLX enabled
[    13.339] (II) Loading extension GLX
[    13.339] (II) LoadModule: "record"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.339] (II) Module record: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.10.1, module version = 1.13.0
[    13.339] 	Module class: X.Org Server Extension
[    13.339] 	ABI class: X.Org Server Extension, version 5.0
[    13.339] (II) Loading extension RECORD
[    13.339] (II) LoadModule: "dri"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.339] (II) Module dri: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.10.1, module version = 1.0.0
[    13.339] 	ABI class: X.Org Server Extension, version 5.0
[    13.339] (II) Loading extension XFree86-DRI
[    13.339] (II) LoadModule: "dri2"
[    13.339] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.339] (II) Module dri2: vendor="X.Org Foundation"
[    13.339] 	compiled for 1.10.1, module version = 1.2.0
[    13.339] 	ABI class: X.Org Server Extension, version 5.0
[    13.339] (II) Loading extension DRI2
[    13.339] (==) Matched mga as autoconfigured driver 0
[    13.339] (==) Matched vesa as autoconfigured driver 1
[    13.339] (==) Matched fbdev as autoconfigured driver 2
[    13.339] (==) Assigned the driver to the xf86ConfigLayout
[    13.339] (II) LoadModule: "mga"
[    13.340] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[    13.340] (II) Module mga: vendor="X.Org Foundation"
[    13.340] 	compiled for 1.10.0, module version = 1.4.13
[    13.340] 	Module class: X.Org Video Driver
[    13.340] 	ABI class: X.Org Video Driver, version 10.0
[    13.340] (II) LoadModule: "vesa"
[    13.340] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.340] (II) Module vesa: vendor="X.Org Foundation"
[    13.340] 	compiled for 1.10.0, module version = 2.3.0
[    13.340] 	Module class: X.Org Video Driver
[    13.340] 	ABI class: X.Org Video Driver, version 10.0
[    13.340] (II) LoadModule: "fbdev"
[    13.340] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.340] (II) Module fbdev: vendor="X.Org Foundation"
[    13.340] 	compiled for 1.10.0, module version = 0.4.2
[    13.340] 	ABI class: X.Org Video Driver, version 10.0
[    13.340] (II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag200 EV Maxim,
	mgag200 ER SH7757, mgag200 eW Nuvoton, mgag200eH, mgag400, mgag550
[    13.340] (II) VESA: driver for VESA chipsets: vesa
[    13.340] (II) FBDEV: driver for framebuffer: fbdev
[    13.340] (++) using VT number 7

[    13.340] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[    13.340] (WW) Falling back to old probe method for vesa
[    13.340] (WW) Falling back to old probe method for fbdev
[    13.340] (II) Loading sub module "fbdevhw"
[    13.340] (II) LoadModule: "fbdevhw"
[    13.341] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.341] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.341] 	compiled for 1.10.1, module version = 0.0.2
[    13.341] 	ABI class: X.Org Video Driver, version 10.0
[    13.341] (II) Loading sub module "vgahw"
[    13.341] (II) LoadModule: "vgahw"
[    13.341] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    13.341] (II) Module vgahw: vendor="X.Org Foundation"
[    13.341] 	compiled for 1.10.1, module version = 0.1.0
[    13.341] 	ABI class: X.Org Video Driver, version 10.0
[    13.341] (--) MGA(0): Chipset: "mgag200 eW Nuvoton"
[    13.341] (--) MGA(0): Linear framebuffer at 0xF9000000
[    13.341] (--) MGA(0): MMIO registers at 0xFA200000
[    13.341] (--) MGA(0): Pseudo-DMA transfer window at 0x0
[    13.343] (II) MGA(0): MAPPED Framebuffer F9000000 800000 to 7FBA6C14F000.
[    13.343] (EE) MGA(0): Unable to map BAR 2 (ILOAD region).  No such file or directory (2)
[    13.343] (II) MGA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    13.343] (==) MGA(0): Depth 24, (--) framebuffer bpp 32
[    13.343] (==) MGA(0): RGB weight 888
[    13.343] (**) MGA(0): Enabling KVM
[    13.343] (==) MGA(0): Using AGP 1x mode
[    13.343] (==) MGA(0): Using HW cursor
[    13.343] (==) MGA(0): Using XAA acceleration
[    13.343] (--) MGA(0): Video BIOS info block at offset 0x07D60
[    13.343] (EE) MGA(0): Unable to detect video RAM.
[    13.343] (II) UnloadModule: "mga"
[    13.343] (II) Unloading mga
[    13.343] (II) UnloadModule: "vgahw"
[    13.343] (II) Unloading vgahw
[    13.343] (EE) Screen(s) found, but none have a usable configuration.
[    13.343] 
Fatal server error:
[    13.343] no screens found
[    13.343] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    13.343] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    13.343] 
[    13.549]  ddxSigGiveUp: Closing log

```

---

### Post by Toz on 2011-09-15
Not exactly a solution, but try passing **xforcevesa** to the kernel. This should start X using the vesa driver and get you access to the gui. 

Just googled a bit and not much there of recent. Also read that the MGA drivers are no longer being maintained.

---

### Post by bcavagnolo on 2011-09-17
Hmm.  I'm a bit worried about the xforcevesa because we do have some graphics intensive apps.  Even the console right now, which I presume is using VESA, is terribly slow.

Anyway, what do you mean the MGA drivers are not supported anymore?  By xorg?  By Ubuntu?  I googled around and didn't find anything particularly disconcerting.

Thanks,
Brian

---

### Post by Toz on 2011-09-18
See as examples:
- [http://forums.freebsd.org/showpost.php?p=142724&postcount=3]("http://forums.freebsd.org/showpost.php?p=142724&postcount=3")
- [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+question/141544]("https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+question/141544")

From your Xorg.0.log file:
> [    13.343] (EE) MGA(0): Unable to map BAR 2 (ILOAD region).  No such file or directory (2
...
[    13.343] (EE) MGA(0): Unable to detect video RAM.


It might be best to create a bug report in launchpad.

---

### Post by bcavagnolo on 2011-09-19
Okay.  I filed a bug.  Thanks for your support.

For the record, neither nomodeset nor xforcevesa had any effect.

I considered trying gnome-classic.  After all, 10.04 and 10.10 worked fine.  But I don't even see a splash screen or login screen, so I'm not sure this strategy would even work.  Any thoughts on this?

Thanks,
Brian

---

### Post by Toz on 2011-09-19
Perhaps you're best bet is to run 10.04 - the LTS version and keep an eye on the bug report for changes/fixes.

I also did some more research and came across this link: [https://bbs.archlinux.org/viewtopic.php?id=93629]("https://bbs.archlinux.org/viewtopic.php?id=93629") (see post #3). Is there maybe something in your bios that you can set for the later versions of ubuntu?

EDIT: Just came across this link: [http://ubuntuforums.org/showpost.php?p=10302673&postcount=9]("http://ubuntuforums.org/showpost.php?p=10302673&postcount=9"). It talks about a **mga-vid-common** package. Do you have this installed? Here is the info about it:
> This package contains the program 'mga_vid_test', which has one mission
 in life: to verify that the mga_vid driver works correctly.
 .
 It also contains some configuration files for udev so that
 the module gets loaded automatically on demand and so that the device
 node will be created with proper permissions.


Maybe worth a try to install if not installed?

---

