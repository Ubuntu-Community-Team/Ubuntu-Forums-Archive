---
title: "Returns to Login Screen after correct password"
date: 2012-02-16
forum: Desktop Environments
---

### Post by ivanoats on 2012-02-16
Hi, I have a pretty new fresh install of Ubuntu 11.10 desktop.  I can't log in, it just returns me to the login screen.

I'm sure password is correct because I can log in via terminal mode by pressing ctrl-alt-f2

I've tried dpkg-reconfigure xorg and also gdm and lightdm, still no luck

At this point my machine is unusable (except terminal mode).

Any ideas on how to quickly resolve this?

This started happening after I installed cairo-dock from the software center and logged out. I uninstalled it via aptitude on the command line but I still have the problem. :confused:

---

### Post by ivanoats on 2012-02-21
I'm really stuck here - no access to my desktop. Any ideas, anyone?

---

### Post by roelforg on 2012-02-21
Unity should be on your sys,

try
```

sudo apt-get update
sudo apt-get install xinit
xinit unity

```
from your terminal;

If it works, run:
```

sudo dpkg-reconfigure unity

```

If it doesn't,
We're gonna try a complex procedure:
reboot
try logging in once
when it returns to gdm, switch to a console (CTRL-ALT-F1) and log in on the console
run (replace <username> with your username):
```

mkdir ~/xlogs
sudo bash
cp /var/log/Xorg* /home/<username>/xlogs/
exit

```
Now post the contents of the 2 files in ~/xlogs and PM me (i'm bad in tracking threads so the pm will alert me).

---

### Post by ivanoats on 2012-02-24
Xorg.0.log.old
```
[  5251.332] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  5251.332] X Protocol Version 11, Revision 0
[  5251.332] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  5251.332] Current Operating System: Linux ubuntu 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686
[  5251.332] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=36f2f1d6-9356-4596-a4a8-7b10ed7a7c42 ro quiet splash vt.handoff=7
[  5251.332] Build Date: 19 October 2011  05:09:41AM
[  5251.332] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  5251.332] Current version of pixman: 0.22.2
[  5251.332] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  5251.332] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  5251.332] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 16 10:44:27 2012
[  5251.332] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  5251.332] (==) No Layout section.  Using the first Screen section.
[  5251.333] (==) No screen section available. Using defaults.
[  5251.333] (**) |-->Screen "Default Screen Section" (0)
[  5251.333] (**) |   |-->Monitor "<default monitor>"
[  5251.333] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  5251.333] (==) Automatically adding devices
[  5251.333] (==) Automatically enabling devices
[  5251.333] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  5251.333] 	Entry deleted from font path.
[  5251.333] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  5251.333] 	Entry deleted from font path.
[  5251.333] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  5251.333] 	Entry deleted from font path.
[  5251.333] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  5251.333] 	Entry deleted from font path.
[  5251.333] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  5251.333] 	Entry deleted from font path.
[  5251.333] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  5251.333] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  5251.333] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  5251.333] (II) Loader magic: 0x823ada0
[  5251.333] (II) Module ABI versions:
[  5251.333] 	X.Org ANSI C Emulation: 0.4
[  5251.333] 	X.Org Video Driver: 10.0
[  5251.333] 	X.Org XInput driver : 12.3
[  5251.333] 	X.Org Server Extension : 5.0
[  5251.339] (--) PCI:*(0:0:15:0) 15ad:0405:15ad:0405 rev 0, Mem @ 0xd0000000/134217728, 0xc8800000/8388608, I/O @ 0x000010d0/16, BIOS @ 0x????????/32768
[  5251.339] (II) Open ACPI successful (/var/run/acpid.socket)
[  5251.339] (II) LoadModule: "extmod"
[  5251.339] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  5251.339] (II) Module extmod: vendor="X.Org Foundation"
[  5251.339] 	compiled for 1.10.4, module version = 1.0.0
[  5251.340] 	Module class: X.Org Server Extension
[  5251.340] 	ABI class: X.Org Server Extension, version 5.0
[  5251.340] (II) Loading extension MIT-SCREEN-SAVER
[  5251.340] (II) Loading extension XFree86-VidModeExtension
[  5251.340] (II) Loading extension XFree86-DGA
[  5251.340] (II) Loading extension DPMS
[  5251.340] (II) Loading extension XVideo
[  5251.340] (II) Loading extension XVideo-MotionCompensation
[  5251.340] (II) Loading extension X-Resource
[  5251.340] (II) LoadModule: "dbe"
[  5251.340] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  5251.340] (II) Module dbe: vendor="X.Org Foundation"
[  5251.340] 	compiled for 1.10.4, module version = 1.0.0
[  5251.340] 	Module class: X.Org Server Extension
[  5251.340] 	ABI class: X.Org Server Extension, version 5.0
[  5251.340] (II) Loading extension DOUBLE-BUFFER
[  5251.340] (II) LoadModule: "glx"
[  5251.340] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  5251.340] (II) Module glx: vendor="X.Org Foundation"
[  5251.340] 	compiled for 1.10.4, module version = 1.0.0
[  5251.340] 	ABI class: X.Org Server Extension, version 5.0
[  5251.340] (==) AIGLX enabled
[  5251.340] (II) Loading extension GLX
[  5251.340] (II) LoadModule: "record"
[  5251.340] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  5251.340] (II) Module record: vendor="X.Org Foundation"
[  5251.340] 	compiled for 1.10.4, module version = 1.13.0
[  5251.340] 	Module class: X.Org Server Extension
[  5251.340] 	ABI class: X.Org Server Extension, version 5.0
[  5251.340] (II) Loading extension RECORD
[  5251.340] (II) LoadModule: "dri"
[  5251.340] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  5251.341] (II) Module dri: vendor="X.Org Foundation"
[  5251.341] 	compiled for 1.10.4, module version = 1.0.0
[  5251.341] 	ABI class: X.Org Server Extension, version 5.0
[  5251.341] (II) Loading extension XFree86-DRI
[  5251.341] (II) LoadModule: "dri2"
[  5251.341] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  5251.341] (II) Module dri2: vendor="X.Org Foundation"
[  5251.341] 	compiled for 1.10.4, module version = 1.2.0
[  5251.341] 	ABI class: X.Org Server Extension, version 5.0
[  5251.341] (II) Loading extension DRI2
[  5251.341] (==) Matched vmware as autoconfigured driver 0
[  5251.341] (==) Matched vesa as autoconfigured driver 1
[  5251.341] (==) Matched fbdev as autoconfigured driver 2
[  5251.341] (==) Assigned the driver to the xf86ConfigLayout
[  5251.341] (II) LoadModule: "vmware"
[  5251.341] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[  5251.341] (II) Module vmware: vendor="X.Org Foundation"
[  5251.341] 	compiled for 1.10.1, module version = 11.0.3
[  5251.341] 	Module class: X.Org Video Driver
[  5251.341] 	ABI class: X.Org Video Driver, version 10.0
[  5251.341] (II) LoadModule: "vmwgfx"
[  5251.342] (WW) Warning, couldn't open module vmwgfx
[  5251.342] (II) UnloadModule: "vmwgfx"
[  5251.342] (II) Unloading vmwgfx
[  5251.342] (EE) Failed to load module "vmwgfx" (module does not exist, 0)
[  5251.342] (EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
[  5251.342] (II) vmware: Using vmwlegacy driver everything is fine.
[  5251.342] (II) LoadModule: "vmwlegacy"
[  5251.342] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[  5251.342] (II) Module vmwlegacy: vendor="X.Org Foundation"
[  5251.342] 	compiled for 1.10.1, module version = 11.0.3
[  5251.342] 	Module class: X.Org Video Driver
[  5251.342] 	ABI class: X.Org Video Driver, version 10.0
[  5251.342] (II) LoadModule: "vesa"
[  5251.342] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  5251.342] (II) Module vesa: vendor="X.Org Foundation"
[  5251.342] 	compiled for 1.10.2, module version = 2.3.0
[  5251.342] 	Module class: X.Org Video Driver
[  5251.342] 	ABI class: X.Org Video Driver, version 10.0
[  5251.342] (II) LoadModule: "fbdev"
[  5251.342] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  5251.342] (II) Module fbdev: vendor="X.Org Foundation"
[  5251.342] 	compiled for 1.10.0, module version = 0.4.2
[  5251.342] 	ABI class: X.Org Video Driver, version 10.0
[  5251.342] (II) vmwlegacy: driver for VMware SVGA: vmware0405, vmware0710
[  5251.342] (II) VESA: driver for VESA chipsets: vesa
[  5251.342] (II) FBDEV: driver for framebuffer: fbdev
[  5251.342] (++) using VT number 7

[  5251.343] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[  5251.343] (WW) Falling back to old probe method for vesa
[  5251.343] (WW) Falling back to old probe method for fbdev
[  5251.343] (II) Loading sub module "fbdevhw"
[  5251.343] (II) LoadModule: "fbdevhw"
[  5251.343] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  5251.343] (II) Module fbdevhw: vendor="X.Org Foundation"
[  5251.343] 	compiled for 1.10.4, module version = 0.0.2
[  5251.343] 	ABI class: X.Org Video Driver, version 10.0
[  5251.343] (EE) open /dev/fb0: No such file or directory
[  5251.343] (--) vmwlegacy(0): VMware SVGA regs at (0x10d0, 0x10d1)
[  5251.343] (II) Loading sub module "vgahw"
[  5251.343] (II) LoadModule: "vgahw"
[  5251.343] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[  5251.343] (II) Module vgahw: vendor="X.Org Foundation"
[  5251.343] 	compiled for 1.10.4, module version = 0.1.0
[  5251.343] 	ABI class: X.Org Video Driver, version 10.0
[  5251.383] (--) vmwlegacy(0): caps:  0x00FF83E2
[  5251.383] (--) vmwlegacy(0): depth: 24
[  5251.383] (--) vmwlegacy(0): bpp:   32
[  5251.383] (--) vmwlegacy(0): vram:  67108864
[  5251.383] (--) vmwlegacy(0): pbase: 0xd0000000
[  5251.383] (--) vmwlegacy(0): mwidt: 5120
[  5251.383] (--) vmwlegacy(0): mheig: 3200
[  5251.384] (II) vmwlegacy(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  5251.384] (--) vmwlegacy(0): depth: 24
[  5251.384] (--) vmwlegacy(0): bpp:   32
[  5251.384] (--) vmwlegacy(0): w.red: 8
[  5251.384] (--) vmwlegacy(0): w.grn: 8
[  5251.384] (--) vmwlegacy(0): w.blu: 8
[  5251.384] (--) vmwlegacy(0): vis:   4
[  5251.384] (==) vmwlegacy(0): Depth 24, (==) framebuffer bpp 32
[  5251.384] (==) vmwlegacy(0): RGB weight 888
[  5251.384] (==) vmwlegacy(0): Default visual is TrueColor
[  5251.384] (==) vmwlegacy(0): Using HW cursor
[  5251.384] (==) vmwlegacy(0): Using gamma correction (1.0, 1.0, 1.0)
[  5251.384] (II) vmwlegacy(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[  5251.384] (II) vmwlegacy(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[  5251.384] (II) vmwlegacy(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[  5251.384] (WW) vmwlegacy(0): Unable to estimate virtual size
[  5251.384] (II) vmwlegacy(0): Clock range:   0.00 to 400000.00 MHz
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x350" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x400" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "720x400" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x480" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x480" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x480" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (vrefresh out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1024x768i" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1024x768" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1024x768" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1024x768" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1280x960" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1280x960" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1280x1024" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1280x1024" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1280x1024" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1792x1344" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1792x1344" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1856x1392" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1856x1392" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1920x1440" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1920x1440" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "832x624" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[  5251.384] (II) vmwlegacy(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1360x768" (mode clock too high)
[  5251.384] (II) vmwlegacy(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1440x900" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1600x1024" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1920x1080" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1920x1200" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "1920x1440" (hsync out of range)
[  5251.384] (II) vmwlegacy(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  5251.384] (II) vmwlegacy(0): Not using default mode "2048x1536" (hsync out of range)
[  5251.385] (II) vmwlegacy(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  5251.385] (II) vmwlegacy(0): Not using default mode "2048x1536" (hsync out of range)
[  5251.385] (II) vmwlegacy(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  5251.385] (II) vmwlegacy(0): Not using default mode "2048x1536" (hsync out of range)
[  5251.385] (II) vmwlegacy(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  5251.385] (--) vmwlegacy(0): Virtual size is 1024x768 (pitch 1024)
[  5251.385] (**) vmwlegacy(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[  5251.385] (II) vmwlegacy(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  5251.385] (**) vmwlegacy(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[  5251.385] (II) vmwlegacy(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  5251.385] (**) vmwlegacy(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[  5251.385] (II) vmwlegacy(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  5251.385] (**) vmwlegacy(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[  5251.385] (II) vmwlegacy(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  5251.385] (==) vmwlegacy(0): DPI set to (96, 96)
[  5251.385] (II) Loading sub module "fb"
[  5251.385] (II) LoadModule: "fb"
[  5251.385] (II) Loading /usr/lib/xorg/modules/libfb.so
[  5251.385] (II) Module fb: vendor="X.Org Foundation"
[  5251.385] 	compiled for 1.10.4, module version = 1.0.0
[  5251.385] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  5251.385] (II) Loading sub module "shadowfb"
[  5251.385] (II) LoadModule: "shadowfb"
[  5251.385] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[  5251.385] (II) Module shadowfb: vendor="X.Org Foundation"
[  5251.385] 	compiled for 1.10.4, module version = 1.0.0
[  5251.385] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  5251.385] (II) Loading sub module "ramdac"
[  5251.385] (II) LoadModule: "ramdac"
[  5251.385] (II) Module "ramdac" already built-in
[  5251.385] (II) UnloadModule: "vesa"
[  5251.385] (II) Unloading vesa
[  5251.385] (II) UnloadModule: "fbdev"
[  5251.385] (II) Unloading fbdev
[  5251.385] (II) UnloadModule: "fbdevhw"
[  5251.385] (II) Unloading fbdevhw
[  5251.385] (--) Depth 24 pixmap format is 32 bpp
[  5251.386] (II) vmwlegacy(0): Initialized VMWARE_CTRL extension version 0.2
[  5251.386] (II) vmwlegacy(0): Initialized VMware Xinerama extension.
[  5251.386] (II) vmwlegacy(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[  5251.489] (==) vmwlegacy(0): Backing store disabled
[  5251.489] (==) vmwlegacy(0): Silken mouse enabled
[  5251.490] (II) vmwlegacy(0): Initialized VMware Xv extension successfully.
[  5251.490] (==) RandR enabled
[  5251.490] (II) Initializing built-in extension Generic Event Extension
[  5251.490] (II) Initializing built-in extension SHAPE
[  5251.490] (II) Initializing built-in extension MIT-SHM
[  5251.490] (II) Initializing built-in extension XInputExtension
[  5251.490] (II) Initializing built-in extension XTEST
[  5251.490] (II) Initializing built-in extension BIG-REQUESTS
[  5251.490] (II) Initializing built-in extension SYNC
[  5251.490] (II) Initializing built-in extension XKEYBOARD
[  5251.490] (II) Initializing built-in extension XC-MISC
[  5251.490] (II) Initializing built-in extension SECURITY
[  5251.490] (II) Initializing built-in extension XINERAMA
[  5251.490] (II) Initializing built-in extension XFIXES
[  5251.490] (II) Initializing built-in extension RENDER
[  5251.490] (II) Initializing built-in extension RANDR
[  5251.490] (II) Initializing built-in extension COMPOSITE
[  5251.490] (II) Initializing built-in extension DAMAGE
[  5251.490] (II) Initializing built-in extension GESTURE
[  5251.496] (II) AIGLX: Screen 0 is not DRI2 capable
[  5251.496] (II) AIGLX: Screen 0 is not DRI capable
[  5251.496] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[  5251.498] (II) AIGLX: Loaded and initialized swrast
[  5251.498] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  5251.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  5251.511] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  5251.511] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  5251.511] (II) LoadModule: "evdev"
[  5251.511] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5251.512] (II) Module evdev: vendor="X.Org Foundation"
[  5251.512] 	compiled for 1.10.2, module version = 2.6.0
[  5251.512] 	Module class: X.Org XInput Driver
[  5251.512] 	ABI class: X.Org XInput driver, version 12.3
[  5251.512] (II) Using input driver 'evdev' for 'Power Button'
[  5251.512] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5251.512] (**) Power Button: always reports core events
[  5251.512] (**) Power Button: Device: "/dev/input/event0"
[  5251.512] (--) Power Button: Found keys
[  5251.512] (II) Power Button: Configuring as keyboard
[  5251.512] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[  5251.512] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  5251.512] (**) Option "xkb_rules" "evdev"
[  5251.512] (**) Option "xkb_model" "SKIP"
[  5251.512] (**) Option "xkb_layout" "us"
[  5251.514] (II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[  5251.518] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/event2)
[  5251.518] (**) VMware VMware Virtual USB Mouse: Applying InputClass "evdev pointer catchall"
[  5251.518] (II) Using input driver 'evdev' for 'VMware VMware Virtual USB Mouse'
[  5251.518] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5251.518] (**) VMware VMware Virtual USB Mouse: always reports core events
[  5251.518] (**) VMware VMware Virtual USB Mouse: Device: "/dev/input/event2"
[  5251.518] (--) VMware VMware Virtual USB Mouse: Found 20 mouse buttons
[  5251.518] (--) VMware VMware Virtual USB Mouse: Found scroll wheel(s)
[  5251.518] (--) VMware VMware Virtual USB Mouse: Found relative axes
[  5251.518] (--) VMware VMware Virtual USB Mouse: Found absolute axes
[  5251.518] (II) evdev-grail: failed to open grail, no gesture support
[  5251.518] (--) VMware VMware Virtual USB Mouse: Found x and y absolute axes
[  5251.519] (II) VMware VMware Virtual USB Mouse: Configuring as mouse
[  5251.519] (II) VMware VMware Virtual USB Mouse: Adding scrollwheel support
[  5251.519] (**) VMware VMware Virtual USB Mouse: YAxisMapping: buttons 4 and 5
[  5251.519] (**) VMware VMware Virtual USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  5251.519] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/input/input2/event2"
[  5251.519] (II) XINPUT: Adding extended input device "VMware VMware Virtual USB Mouse" (type: MOUSE)
[  5251.519] (EE) VMware VMware Virtual USB Mouse: failed to initialize for relative axes.
[  5251.519] (II) VMware VMware Virtual USB Mouse: initialized for absolute axes.
[  5251.519] (**) VMware VMware Virtual USB Mouse: (accel) keeping acceleration scheme 1
[  5251.519] (**) VMware VMware Virtual USB Mouse: (accel) acceleration profile 0
[  5251.519] (**) VMware VMware Virtual USB Mouse: (accel) acceleration factor: 2.000
[  5251.519] (**) VMware VMware Virtual USB Mouse: (accel) acceleration threshold: 4
[  5251.519] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/js0)
[  5251.519] (II) No input driver/identifier specified (ignoring)
[  5251.519] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/mouse0)
[  5251.519] (II) No input driver/identifier specified (ignoring)
[  5251.520] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/event3)
[  5251.520] (**) VMware VMware Virtual USB Mouse: Applying InputClass "evdev pointer catchall"
[  5251.520] (II) Using input driver 'evdev' for 'VMware VMware Virtual USB Mouse'
[  5251.520] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5251.520] (**) VMware VMware Virtual USB Mouse: always reports core events
[  5251.520] (**) VMware VMware Virtual USB Mouse: Device: "/dev/input/event3"
[  5251.520] (--) VMware VMware Virtual USB Mouse: Found 20 mouse buttons
[  5251.520] (--) VMware VMware Virtual USB Mouse: Found scroll wheel(s)
[  5251.520] (--) VMware VMware Virtual USB Mouse: Found relative axes
[  5251.520] (--) VMware VMware Virtual USB Mouse: Found x and y relative axes
[  5251.520] (II) VMware VMware Virtual USB Mouse: Configuring as mouse
[  5251.520] (II) VMware VMware Virtual USB Mouse: Adding scrollwheel support
[  5251.520] (**) VMware VMware Virtual USB Mouse: YAxisMapping: buttons 4 and 5
[  5251.520] (**) VMware VMware Virtual USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  5251.520] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.1/input/input3/event3"
[  5251.520] (II) XINPUT: Adding extended input device "VMware VMware Virtual USB Mouse" (type: MOUSE)
[  5251.520] (II) VMware VMware Virtual USB Mouse: initialized for relative axes.
[  5251.520] (**) VMware VMware Virtual USB Mouse: (accel) keeping acceleration scheme 1
[  5251.520] (**) VMware VMware Virtual USB Mouse: (accel) acceleration profile 0
[  5251.520] (**) VMware VMware Virtual USB Mouse: (accel) acceleration factor: 2.000
[  5251.520] (**) VMware VMware Virtual USB Mouse: (accel) acceleration threshold: 4
[  5251.520] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/mouse1)
[  5251.520] (II) No input driver/identifier specified (ignoring)
[  5251.525] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[  5251.525] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  5251.525] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  5251.525] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5251.525] (**) AT Translated Set 2 keyboard: always reports core events
[  5251.525] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[  5251.525] (--) AT Translated Set 2 keyboard: Found keys
[  5251.525] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  5251.525] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input1/event1"
[  5251.525] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  5251.525] (**) Option "xkb_rules" "evdev"
[  5251.525] (**) Option "xkb_model" "SKIP"
[  5251.525] (**) Option "xkb_layout" "us"
[  5251.526] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[  5251.526] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[  5251.526] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "vmmouse"
[  5251.526] (II) LoadModule: "vmmouse"
[  5251.526] (II) Loading /usr/lib/xorg/modules/input/vmmouse_drv.so
[  5251.526] (II) Module vmmouse: vendor="X.Org Foundation"
[  5251.526] 	compiled for 1.10.1, module version = 12.7.0
[  5251.526] 	Module class: X.Org XInput Driver
[  5251.526] 	ABI class: X.Org XInput driver, version 12.3
[  5251.526] (II) VMWARE(0): VMMOUSE module was loaded
[  5251.526] (II) Using input driver 'vmmouse' for 'ImPS/2 Generic Wheel Mouse'
[  5251.526] (II) Loading /usr/lib/xorg/modules/input/vmmouse_drv.so
[  5251.526] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[  5251.526] (II) VMWARE(0): vmmouse is available
[  5251.526] (**) Option "Device" "/dev/input/event4"
[  5251.528] (**) ImPS/2 Generic Wheel Mouse: ZAxisMapping: buttons 4 and 5
[  5251.528] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[  5251.528] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[  5251.528] (II) VMWARE(0): VMMOUSE DEVICE_INIT
[  5251.528] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[  5251.528] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[  5251.528] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[  5251.528] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[  5251.528] (II) VMWARE(0): VMMOUSE DEVICE_ON
[  5251.528] (II) VMWARE(0): vmmouse enabled
[  5251.528] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse2)
[  5251.528] (II) No input driver/identifier specified (ignoring)
[  5255.730] (II) VMWARE(0): vmmouse enable absolute mode
[  5263.308] (II) Power Button: Close
[  5263.308] (II) UnloadModule: "evdev"
[  5263.308] (II) Unloading evdev
[  5263.635] (II) VMware VMware Virtual USB Mouse: Close
[  5263.635] (II) UnloadModule: "evdev"
[  5263.635] (II) Unloading evdev
[  5264.640] (II) VMware VMware Virtual USB Mouse: Close
[  5264.640] (II) UnloadModule: "evdev"
[  5264.640] (II) Unloading evdev
[  5264.648] (II) AT Translated Set 2 keyboard: Close
[  5264.648] (II) UnloadModule: "evdev"
[  5264.648] (II) Unloading evdev
[  5264.648] (II) VMWARE(0): VMMOUSE DEVICE_OFF/CLOSE
[  5264.957] (II) VMWARE(0): VMMOUSE DEVICE_OFF/CLOSE
[  5265.258] (II) VMWARE(0): VMMouseUnInit
[  5265.258] (II) vmwlegacy(0): Terminating Xv video-stream id:0
[  5265.336]  ddxSigGiveUp: Closing log

```

Xorg.0.log
```


[  5265.340] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  5265.340] X Protocol Version 11, Revision 0
[  5265.340] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  5265.340] Current Operating System: Linux ubuntu 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686
[  5265.340] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=36f2f1d6-9356-4596-a4a8-7b10ed7a7c42 ro quiet splash vt.handoff=7
[  5265.341] Build Date: 19 October 2011  05:09:41AM
[  5265.341] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  5265.341] Current version of pixman: 0.22.2
[  5265.341] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  5265.341] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  5265.341] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 16 10:44:41 2012
[  5265.341] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  5265.341] (==) No Layout section.  Using the first Screen section.
[  5265.341] (==) No screen section available. Using defaults.
[  5265.341] (**) |-->Screen "Default Screen Section" (0)
[  5265.341] (**) |   |-->Monitor "<default monitor>"
[  5265.341] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  5265.341] (==) Automatically adding devices
[  5265.341] (==) Automatically enabling devices
[  5265.341] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  5265.341] 	Entry deleted from font path.
[  5265.341] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  5265.341] 	Entry deleted from font path.
[  5265.341] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  5265.341] 	Entry deleted from font path.
[  5265.341] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  5265.341] 	Entry deleted from font path.
[  5265.341] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  5265.341] 	Entry deleted from font path.
[  5265.341] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  5265.341] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  5265.341] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  5265.341] (II) Loader magic: 0x823ada0
[  5265.341] (II) Module ABI versions:
[  5265.341] 	X.Org ANSI C Emulation: 0.4
[  5265.341] 	X.Org Video Driver: 10.0
[  5265.341] 	X.Org XInput driver : 12.3
[  5265.341] 	X.Org Server Extension : 5.0
[  5265.347] (--) PCI:*(0:0:15:0) 15ad:0405:15ad:0405 rev 0, Mem @ 0xd0000000/134217728, 0xc8800000/8388608, I/O @ 0x000010d0/16, BIOS @ 0x????????/32768
[  5265.347] (II) Open ACPI successful (/var/run/acpid.socket)
[  5265.347] (II) LoadModule: "extmod"
[  5265.347] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  5265.347] (II) Module extmod: vendor="X.Org Foundation"
[  5265.347] 	compiled for 1.10.4, module version = 1.0.0
[  5265.347] 	Module class: X.Org Server Extension
[  5265.347] 	ABI class: X.Org Server Extension, version 5.0
[  5265.347] (II) Loading extension MIT-SCREEN-SAVER
[  5265.347] (II) Loading extension XFree86-VidModeExtension
[  5265.347] (II) Loading extension XFree86-DGA
[  5265.347] (II) Loading extension DPMS
[  5265.347] (II) Loading extension XVideo
[  5265.347] (II) Loading extension XVideo-MotionCompensation
[  5265.347] (II) Loading extension X-Resource
[  5265.347] (II) LoadModule: "dbe"
[  5265.347] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  5265.347] (II) Module dbe: vendor="X.Org Foundation"
[  5265.347] 	compiled for 1.10.4, module version = 1.0.0
[  5265.347] 	Module class: X.Org Server Extension
[  5265.347] 	ABI class: X.Org Server Extension, version 5.0
[  5265.347] (II) Loading extension DOUBLE-BUFFER
[  5265.347] (II) LoadModule: "glx"
[  5265.348] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  5265.348] (II) Module glx: vendor="X.Org Foundation"
[  5265.348] 	compiled for 1.10.4, module version = 1.0.0
[  5265.348] 	ABI class: X.Org Server Extension, version 5.0
[  5265.348] (==) AIGLX enabled
[  5265.348] (II) Loading extension GLX
[  5265.348] (II) LoadModule: "record"
[  5265.348] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  5265.348] (II) Module record: vendor="X.Org Foundation"
[  5265.348] 	compiled for 1.10.4, module version = 1.13.0
[  5265.348] 	Module class: X.Org Server Extension
[  5265.348] 	ABI class: X.Org Server Extension, version 5.0
[  5265.348] (II) Loading extension RECORD
[  5265.348] (II) LoadModule: "dri"
[  5265.348] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  5265.348] (II) Module dri: vendor="X.Org Foundation"
[  5265.348] 	compiled for 1.10.4, module version = 1.0.0
[  5265.348] 	ABI class: X.Org Server Extension, version 5.0
[  5265.348] (II) Loading extension XFree86-DRI
[  5265.348] (II) LoadModule: "dri2"
[  5265.348] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  5265.348] (II) Module dri2: vendor="X.Org Foundation"
[  5265.348] 	compiled for 1.10.4, module version = 1.2.0
[  5265.348] 	ABI class: X.Org Server Extension, version 5.0
[  5265.348] (II) Loading extension DRI2
[  5265.348] (==) Matched vmware as autoconfigured driver 0
[  5265.348] (==) Matched vesa as autoconfigured driver 1
[  5265.348] (==) Matched fbdev as autoconfigured driver 2
[  5265.348] (==) Assigned the driver to the xf86ConfigLayout
[  5265.348] (II) LoadModule: "vmware"
[  5265.349] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[  5265.349] (II) Module vmware: vendor="X.Org Foundation"
[  5265.349] 	compiled for 1.10.1, module version = 11.0.3
[  5265.349] 	Module class: X.Org Video Driver
[  5265.349] 	ABI class: X.Org Video Driver, version 10.0
[  5265.349] (II) LoadModule: "vmwgfx"
[  5265.349] (WW) Warning, couldn't open module vmwgfx
[  5265.349] (II) UnloadModule: "vmwgfx"
[  5265.349] (II) Unloading vmwgfx
[  5265.349] (EE) Failed to load module "vmwgfx" (module does not exist, 0)
[  5265.349] (EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
[  5265.349] (II) vmware: Using vmwlegacy driver everything is fine.
[  5265.349] (II) LoadModule: "vmwlegacy"
[  5265.349] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[  5265.349] (II) Module vmwlegacy: vendor="X.Org Foundation"
[  5265.349] 	compiled for 1.10.1, module version = 11.0.3
[  5265.349] 	Module class: X.Org Video Driver
[  5265.349] 	ABI class: X.Org Video Driver, version 10.0
[  5265.349] (II) LoadModule: "vesa"
[  5265.349] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  5265.349] (II) Module vesa: vendor="X.Org Foundation"
[  5265.349] 	compiled for 1.10.2, module version = 2.3.0
[  5265.349] 	Module class: X.Org Video Driver
[  5265.349] 	ABI class: X.Org Video Driver, version 10.0
[  5265.349] (II) LoadModule: "fbdev"
[  5265.350] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  5265.350] (II) Module fbdev: vendor="X.Org Foundation"
[  5265.350] 	compiled for 1.10.0, module version = 0.4.2
[  5265.350] 	ABI class: X.Org Video Driver, version 10.0
[  5265.350] (II) vmwlegacy: driver for VMware SVGA: vmware0405, vmware0710
[  5265.350] (II) VESA: driver for VESA chipsets: vesa
[  5265.350] (II) FBDEV: driver for framebuffer: fbdev
[  5265.350] (++) using VT number 7

[  5265.350] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[  5265.350] (WW) Falling back to old probe method for vesa
[  5265.350] (WW) Falling back to old probe method for fbdev
[  5265.350] (II) Loading sub module "fbdevhw"
[  5265.350] (II) LoadModule: "fbdevhw"
[  5265.350] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  5265.350] (II) Module fbdevhw: vendor="X.Org Foundation"
[  5265.350] 	compiled for 1.10.4, module version = 0.0.2
[  5265.350] 	ABI class: X.Org Video Driver, version 10.0
[  5265.350] (EE) open /dev/fb0: No such file or directory
[  5265.350] (--) vmwlegacy(0): VMware SVGA regs at (0x10d0, 0x10d1)
[  5265.350] (II) Loading sub module "vgahw"
[  5265.350] (II) LoadModule: "vgahw"
[  5265.351] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[  5265.351] (II) Module vgahw: vendor="X.Org Foundation"
[  5265.351] 	compiled for 1.10.4, module version = 0.1.0
[  5265.351] 	ABI class: X.Org Video Driver, version 10.0
[  5265.391] (--) vmwlegacy(0): caps:  0x00FF83E2
[  5265.391] (--) vmwlegacy(0): depth: 24
[  5265.391] (--) vmwlegacy(0): bpp:   32
[  5265.391] (--) vmwlegacy(0): vram:  67108864
[  5265.391] (--) vmwlegacy(0): pbase: 0xd0000000
[  5265.391] (--) vmwlegacy(0): mwidt: 5120
[  5265.391] (--) vmwlegacy(0): mheig: 3200
[  5265.391] (II) vmwlegacy(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  5265.391] (--) vmwlegacy(0): depth: 24
[  5265.391] (--) vmwlegacy(0): bpp:   32
[  5265.391] (--) vmwlegacy(0): w.red: 8
[  5265.391] (--) vmwlegacy(0): w.grn: 8
[  5265.391] (--) vmwlegacy(0): w.blu: 8
[  5265.391] (--) vmwlegacy(0): vis:   4
[  5265.391] (==) vmwlegacy(0): Depth 24, (==) framebuffer bpp 32
[  5265.391] (==) vmwlegacy(0): RGB weight 888
[  5265.391] (==) vmwlegacy(0): Default visual is TrueColor
[  5265.391] (==) vmwlegacy(0): Using HW cursor
[  5265.391] (==) vmwlegacy(0): Using gamma correction (1.0, 1.0, 1.0)
[  5265.391] (II) vmwlegacy(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[  5265.391] (II) vmwlegacy(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[  5265.391] (II) vmwlegacy(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[  5265.391] (WW) vmwlegacy(0): Unable to estimate virtual size
[  5265.391] (II) vmwlegacy(0): Clock range:   0.00 to 400000.00 MHz
[  5265.391] (II) vmwlegacy(0): Not using default mode "640x350" (vrefresh out of range)
[  5265.391] (II) vmwlegacy(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[  5265.391] (II) vmwlegacy(0): Not using default mode "640x400" (vrefresh out of range)
[  5265.391] (II) vmwlegacy(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[  5265.391] (II) vmwlegacy(0): Not using default mode "720x400" (vrefresh out of range)
[  5265.391] (II) vmwlegacy(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[  5265.391] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5265.391] (II) vmwlegacy(0): Not using default mode "640x480" (vrefresh out of range)
[  5265.391] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "640x480" (vrefresh out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "640x480" (vrefresh out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (vrefresh out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (vrefresh out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1024x768i" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1024x768" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1024x768" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1024x768" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1280x960" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1280x960" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1280x1024" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1280x1024" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1280x1024" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1600x1200" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1792x1344" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1792x1344" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1856x1392" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1856x1392" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1920x1440" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1920x1440" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "832x624" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1152x864" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[  5265.392] (II) vmwlegacy(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1360x768" (mode clock too high)
[  5265.392] (II) vmwlegacy(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1400x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1440x900" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1600x1024" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1680x1050" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1920x1080" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1920x1200" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1920x1440" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "2048x1536" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "2048x1536" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  5265.392] (II) vmwlegacy(0): Not using default mode "2048x1536" (hsync out of range)
[  5265.392] (II) vmwlegacy(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[  5265.392] (--) vmwlegacy(0): Virtual size is 1024x768 (pitch 1024)
[  5265.392] (**) vmwlegacy(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[  5265.392] (II) vmwlegacy(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  5265.392] (**) vmwlegacy(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[  5265.392] (II) vmwlegacy(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  5265.392] (**) vmwlegacy(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[  5265.392] (II) vmwlegacy(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  5265.392] (**) vmwlegacy(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[  5265.392] (II) vmwlegacy(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  5265.392] (==) vmwlegacy(0): DPI set to (96, 96)
[  5265.392] (II) Loading sub module "fb"
[  5265.392] (II) LoadModule: "fb"
[  5265.393] (II) Loading /usr/lib/xorg/modules/libfb.so
[  5265.393] (II) Module fb: vendor="X.Org Foundation"
[  5265.393] 	compiled for 1.10.4, module version = 1.0.0
[  5265.393] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  5265.393] (II) Loading sub module "shadowfb"
[  5265.393] (II) LoadModule: "shadowfb"
[  5265.393] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[  5265.393] (II) Module shadowfb: vendor="X.Org Foundation"
[  5265.393] 	compiled for 1.10.4, module version = 1.0.0
[  5265.393] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  5265.393] (II) Loading sub module "ramdac"
[  5265.393] (II) LoadModule: "ramdac"
[  5265.393] (II) Module "ramdac" already built-in
[  5265.393] (II) UnloadModule: "vesa"
[  5265.393] (II) Unloading vesa
[  5265.393] (II) UnloadModule: "fbdev"
[  5265.393] (II) Unloading fbdev
[  5265.393] (II) UnloadModule: "fbdevhw"
[  5265.393] (II) Unloading fbdevhw
[  5265.393] (--) Depth 24 pixmap format is 32 bpp
[  5265.393] (II) vmwlegacy(0): Initialized VMWARE_CTRL extension version 0.2
[  5265.394] (II) vmwlegacy(0): Initialized VMware Xinerama extension.
[  5265.394] (II) vmwlegacy(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[  5265.495] (==) vmwlegacy(0): Backing store disabled
[  5265.496] (==) vmwlegacy(0): Silken mouse enabled
[  5265.497] (II) vmwlegacy(0): Initialized VMware Xv extension successfully.
[  5265.497] (==) RandR enabled
[  5265.497] (II) Initializing built-in extension Generic Event Extension
[  5265.497] (II) Initializing built-in extension SHAPE
[  5265.497] (II) Initializing built-in extension MIT-SHM
[  5265.497] (II) Initializing built-in extension XInputExtension
[  5265.497] (II) Initializing built-in extension XTEST
[  5265.497] (II) Initializing built-in extension BIG-REQUESTS
[  5265.497] (II) Initializing built-in extension SYNC
[  5265.497] (II) Initializing built-in extension XKEYBOARD
[  5265.497] (II) Initializing built-in extension XC-MISC
[  5265.497] (II) Initializing built-in extension SECURITY
[  5265.497] (II) Initializing built-in extension XINERAMA
[  5265.497] (II) Initializing built-in extension XFIXES
[  5265.497] (II) Initializing built-in extension RENDER
[  5265.497] (II) Initializing built-in extension RANDR
[  5265.497] (II) Initializing built-in extension COMPOSITE
[  5265.497] (II) Initializing built-in extension DAMAGE
[  5265.497] (II) Initializing built-in extension GESTURE
[  5265.502] (II) AIGLX: Screen 0 is not DRI2 capable
[  5265.502] (II) AIGLX: Screen 0 is not DRI capable
[  5265.502] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[  5265.504] (II) AIGLX: Loaded and initialized swrast
[  5265.504] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  5265.511] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  5265.517] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  5265.517] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  5265.517] (II) LoadModule: "evdev"
[  5265.517] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5265.517] (II) Module evdev: vendor="X.Org Foundation"
[  5265.518] 	compiled for 1.10.2, module version = 2.6.0
[  5265.518] 	Module class: X.Org XInput Driver
[  5265.518] 	ABI class: X.Org XInput driver, version 12.3
[  5265.518] (II) Using input driver 'evdev' for 'Power Button'
[  5265.518] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5265.518] (**) Power Button: always reports core events
[  5265.518] (**) Power Button: Device: "/dev/input/event0"
[  5265.518] (--) Power Button: Found keys
[  5265.518] (II) Power Button: Configuring as keyboard
[  5265.518] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[  5265.518] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  5265.518] (**) Option "xkb_rules" "evdev"
[  5265.518] (**) Option "xkb_model" "SKIP"
[  5265.518] (**) Option "xkb_layout" "us"
[  5265.519] (II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
[  5265.524] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/event2)
[  5265.524] (**) VMware VMware Virtual USB Mouse: Applying InputClass "evdev pointer catchall"
[  5265.524] (II) Using input driver 'evdev' for 'VMware VMware Virtual USB Mouse'
[  5265.524] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5265.524] (**) VMware VMware Virtual USB Mouse: always reports core events
[  5265.524] (**) VMware VMware Virtual USB Mouse: Device: "/dev/input/event2"
[  5265.524] (--) VMware VMware Virtual USB Mouse: Found 20 mouse buttons
[  5265.524] (--) VMware VMware Virtual USB Mouse: Found scroll wheel(s)
[  5265.524] (--) VMware VMware Virtual USB Mouse: Found relative axes
[  5265.524] (--) VMware VMware Virtual USB Mouse: Found absolute axes
[  5265.524] (II) evdev-grail: failed to open grail, no gesture support
[  5265.524] (--) VMware VMware Virtual USB Mouse: Found x and y absolute axes
[  5265.524] (II) VMware VMware Virtual USB Mouse: Configuring as mouse
[  5265.524] (II) VMware VMware Virtual USB Mouse: Adding scrollwheel support
[  5265.524] (**) VMware VMware Virtual USB Mouse: YAxisMapping: buttons 4 and 5
[  5265.524] (**) VMware VMware Virtual USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  5265.524] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.0/input/input2/event2"
[  5265.524] (II) XINPUT: Adding extended input device "VMware VMware Virtual USB Mouse" (type: MOUSE)
[  5265.524] (EE) VMware VMware Virtual USB Mouse: failed to initialize for relative axes.
[  5265.524] (II) VMware VMware Virtual USB Mouse: initialized for absolute axes.
[  5265.524] (**) VMware VMware Virtual USB Mouse: (accel) keeping acceleration scheme 1
[  5265.524] (**) VMware VMware Virtual USB Mouse: (accel) acceleration profile 0
[  5265.524] (**) VMware VMware Virtual USB Mouse: (accel) acceleration factor: 2.000
[  5265.524] (**) VMware VMware Virtual USB Mouse: (accel) acceleration threshold: 4
[  5265.524] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/js0)
[  5265.524] (II) No input driver/identifier specified (ignoring)
[  5265.524] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/mouse0)
[  5265.524] (II) No input driver/identifier specified (ignoring)
[  5265.525] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/event3)
[  5265.525] (**) VMware VMware Virtual USB Mouse: Applying InputClass "evdev pointer catchall"
[  5265.525] (II) Using input driver 'evdev' for 'VMware VMware Virtual USB Mouse'
[  5265.525] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5265.525] (**) VMware VMware Virtual USB Mouse: always reports core events
[  5265.525] (**) VMware VMware Virtual USB Mouse: Device: "/dev/input/event3"
[  5265.525] (--) VMware VMware Virtual USB Mouse: Found 20 mouse buttons
[  5265.525] (--) VMware VMware Virtual USB Mouse: Found scroll wheel(s)
[  5265.525] (--) VMware VMware Virtual USB Mouse: Found relative axes
[  5265.525] (--) VMware VMware Virtual USB Mouse: Found x and y relative axes
[  5265.525] (II) VMware VMware Virtual USB Mouse: Configuring as mouse
[  5265.525] (II) VMware VMware Virtual USB Mouse: Adding scrollwheel support
[  5265.525] (**) VMware VMware Virtual USB Mouse: YAxisMapping: buttons 4 and 5
[  5265.525] (**) VMware VMware Virtual USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  5265.525] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:11.0/0000:02:00.0/usb2/2-1/2-1:1.1/input/input3/event3"
[  5265.525] (II) XINPUT: Adding extended input device "VMware VMware Virtual USB Mouse" (type: MOUSE)
[  5265.525] (II) VMware VMware Virtual USB Mouse: initialized for relative axes.
[  5265.525] (**) VMware VMware Virtual USB Mouse: (accel) keeping acceleration scheme 1
[  5265.525] (**) VMware VMware Virtual USB Mouse: (accel) acceleration profile 0
[  5265.525] (**) VMware VMware Virtual USB Mouse: (accel) acceleration factor: 2.000
[  5265.525] (**) VMware VMware Virtual USB Mouse: (accel) acceleration threshold: 4
[  5265.525] (II) config/udev: Adding input device VMware VMware Virtual USB Mouse (/dev/input/mouse1)
[  5265.525] (II) No input driver/identifier specified (ignoring)
[  5265.531] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[  5265.531] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  5265.531] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  5265.531] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5265.531] (**) AT Translated Set 2 keyboard: always reports core events
[  5265.531] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[  5265.531] (--) AT Translated Set 2 keyboard: Found keys
[  5265.531] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  5265.531] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input1/event1"
[  5265.531] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  5265.531] (**) Option "xkb_rules" "evdev"
[  5265.531] (**) Option "xkb_model" "SKIP"
[  5265.531] (**) Option "xkb_layout" "us"
[  5265.531] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[  5265.531] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[  5265.531] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "vmmouse"
[  5265.531] (II) LoadModule: "vmmouse"
[  5265.531] (II) Loading /usr/lib/xorg/modules/input/vmmouse_drv.so
[  5265.531] (II) Module vmmouse: vendor="X.Org Foundation"
[  5265.531] 	compiled for 1.10.1, module version = 12.7.0
[  5265.531] 	Module class: X.Org XInput Driver
[  5265.531] 	ABI class: X.Org XInput driver, version 12.3
[  5265.532] (II) VMWARE(0): VMMOUSE module was loaded
[  5265.532] (II) Using input driver 'vmmouse' for 'ImPS/2 Generic Wheel Mouse'
[  5265.532] (II) Loading /usr/lib/xorg/modules/input/vmmouse_drv.so
[  5265.532] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[  5265.532] (II) VMWARE(0): vmmouse is available
[  5265.532] (**) Option "Device" "/dev/input/event4"
[  5265.536] (**) ImPS/2 Generic Wheel Mouse: ZAxisMapping: buttons 4 and 5
[  5265.536] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[  5265.536] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[  5265.536] (II) VMWARE(0): VMMOUSE DEVICE_INIT
[  5265.536] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[  5265.536] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[  5265.536] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[  5265.536] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[  5265.536] (II) VMWARE(0): VMMOUSE DEVICE_ON
[  5265.536] (II) VMWARE(0): vmmouse enabled
[  5265.536] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse2)
[  5265.536] (II) No input driver/identifier specified (ignoring)
[  5267.512] (II) VMWARE(0): vmmouse enable absolute mode
[  5348.672] (II) VMWARE(0): VMMOUSE DEVICE_OFF/CLOSE

```

---

### Post by roelforg on 2012-02-24
Give us the content of /etc/X11/default-display-manager

Try:
```

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure gnome
sudo dpkg-reconfigure xorg-xserver

```

---

### Post by ivanoats on 2012-02-24
cat /etc/X11/default-display-manager
/usr/sbin/gdm

tried all of the above, but got error with reconfiguring xorg-xserver:

package `xorg-xserver' is not installed and no info is available

I tried to aptitude search xorg-xserver and there is no package with that name

---

### Post by roelforg on 2012-02-24
> **ivanoats said:**
> cat /etc/X11/default-display-manager
/usr/sbin/gdm

tried all of the above, but got error with reconfiguring xorg-xserver:

package `xorg-xserver' is not installed and no info is available

I tried to aptitude search xorg-xserver and there is no package with that name
Yeah... It's xserver-xorg  i always reverse the order (some habit i can't shake off).

---

### Post by ivanoats on 2012-02-24
thanks - did a dpkg-reconfigure on that and still no lock, still returning to login screen after correct password

---

### Post by roelforg on 2012-02-24
> **ivanoats said:**
> thanks - did a dpkg-reconfigure on that and still no lock, still returning to login screen after correct password
The logs tell me that gdm isn't loading gnome for some reason, it's just ending; Xserver reboots and gdm appears again.
Reinstalling gdm and xserver-xorg might work. the wiki has instructions.

---

### Post by ivanoats on 2012-02-24
I had an error in my .profile  - found out from checking .xsession-errors  

that was it!

---

