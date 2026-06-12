---
title: "XPS17 monitor problem GT555M"
date: 2012-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by giodum on 2012-02-09
Hi everybody!

I have a Dell XPS 17 64-bit with a nVidia GT555M. I installed Ubuntu 11.10 64-bit but I had to do it setting before installation NOMODESET.

At that point, if I tried to run the system in normal mode, it just appeared a black screen. On the contrary, running it by recovery mode (resume normal) it runned fine. So I installed Bumblebee (i though it was a graphic card issue) following the procedure explained in [http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936 ]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work/36936#36936")Then I blacklisted the nouveau driver.

So, this is the problem: running the system I have the monitor unknown and the resolution is set to 640x480 and I cannot change it. How can I solve the problem?

Here there is the result of the "xrandr"command:

```
giorgio@giorgio-dell:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        73.0* 
giorgio@giorgio-dell:~$ 

```Moreover I do not have the Xorg.conf file.

Thank you very much in advance,

giodum

---

### Post by giodum on 2012-02-09
Here there are more useful information.

If I boot the system in recovery mode (resume normal) the system does not start and I get two failure:

```
* Starting Bumblebee supporting nVidia Optimus Card    [fail]

initctl: Event failed
   * Starting load fallback graphics devices   [fail]
```This is the content of /var/log/Xorg.0.log

```
   	 	 	 	 	 	   [    14.984] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    14.984] X Protocol Version 11, Revision 0
[    14.984] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.984] Current Operating System: Linux giorgio-dell 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64
[    14.984] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=c798fc87-7d15-44e9-b735-2fc1594d4e96 ro quiet splash vt.handoff=7
[    14.984] Build Date: 19 October 2011  05:21:26AM
[    14.984] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    14.984] Current version of pixman: 0.22.2
[    14.984] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.984] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.984] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb  9 17:24:40 2012
[    15.027] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.027] (==) No Layout section.  Using the first Screen section.
[    15.027] (==) No screen section available. Using defaults.
[    15.027] (**) |-->Screen "Default Screen Section" (0)
[    15.027] (**) |   |-->Monitor "<default monitor>"
[    15.027] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    15.027] (==) Automatically adding devices
[    15.027] (==) Automatically enabling devices
[    15.027] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.027] 	Entry deleted from font path.
[    15.027] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.027] 	Entry deleted from font path.
[    15.027] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.027] 	Entry deleted from font path.
[    15.027] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.027] 	Entry deleted from font path.
[    15.027] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.027] 	Entry deleted from font path.
[    15.027] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.027] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.027] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.027] (II) Loader magic: 0x7e0220
[    15.027] (II) Module ABI versions:
[    15.027] 	X.Org ANSI C Emulation: 0.4
[    15.027] 	X.Org Video Driver: 10.0
[    15.027] 	X.Org XInput driver : 12.3
[    15.027] 	X.Org Server Extension : 5.0
[    15.028] (--) PCI:*(0:1:0:0) 10de:124d:1028:0570 rev 161, Mem @ 0xd4000000/33554432, 0xc0000000/268435456, 0xd0000000/67108864, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    15.028] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.028] (II) LoadModule: "extmod"
[    15.085] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.085] (II) Module extmod: vendor="X.Org Foundation"
[    15.085] 	compiled for 1.10.4, module version = 1.0.0
[    15.085] 	Module class: X.Org Server Extension
[    15.085] 	ABI class: X.Org Server Extension, version 5.0
[    15.085] (II) Loading extension MIT-SCREEN-SAVER
[    15.085] (II) Loading extension XFree86-VidModeExtension
[    15.085] (II) Loading extension XFree86-DGA
[    15.085] (II) Loading extension DPMS
[    15.085] (II) Loading extension XVideo
[    15.085] (II) Loading extension XVideo-MotionCompensation
[    15.085] (II) Loading extension X-Resource
[    15.085] (II) LoadModule: "dbe"
[    15.085] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.085] (II) Module dbe: vendor="X.Org Foundation"
[    15.085] 	compiled for 1.10.4, module version = 1.0.0
[    15.085] 	Module class: X.Org Server Extension
[    15.085] 	ABI class: X.Org Server Extension, version 5.0
[    15.085] (II) Loading extension DOUBLE-BUFFER
[    15.085] (II) LoadModule: "glx"
[    15.085] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.085] (II) Module glx: vendor="X.Org Foundation"
[    15.085] 	compiled for 1.10.4, module version = 1.0.0
[    15.085] 	ABI class: X.Org Server Extension, version 5.0
[    15.085] (==) AIGLX enabled
[    15.085] (II) Loading extension GLX
[    15.085] (II) LoadModule: "record"
[    15.085] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.086] (II) Module record: vendor="X.Org Foundation"
[    15.086] 	compiled for 1.10.4, module version = 1.13.0
[    15.086] 	Module class: X.Org Server Extension
[    15.086] 	ABI class: X.Org Server Extension, version 5.0
[    15.086] (II) Loading extension RECORD
[    15.086] (II) LoadModule: "dri"
[    15.086] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.086] (II) Module dri: vendor="X.Org Foundation"
[    15.086] 	compiled for 1.10.4, module version = 1.0.0
[    15.086] 	ABI class: X.Org Server Extension, version 5.0
[    15.086] (II) Loading extension XFree86-DRI
[    15.086] (II) LoadModule: "dri2"
[    15.086] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.086] (II) Module dri2: vendor="X.Org Foundation"
[    15.086] 	compiled for 1.10.4, module version = 1.2.0
[    15.086] 	ABI class: X.Org Server Extension, version 5.0
[    15.086] (II) Loading extension DRI2
[    15.086] (==) Matched nvidia as autoconfigured driver 0
[    15.086] (==) Matched nouveau as autoconfigured driver 1
[    15.086] (==) Matched nv as autoconfigured driver 2
[    15.086] (==) Matched vesa as autoconfigured driver 3
[    15.086] (==) Matched fbdev as autoconfigured driver 4
[    15.086] (==) Assigned the driver to the xf86ConfigLayout
[    15.086] (II) LoadModule: "nvidia"
[    15.102] (WW) Warning, couldn't open module nvidia
[    15.102] (II) UnloadModule: "nvidia"
[    15.102] (II) Unloading nvidia
[    15.102] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    15.102] (II) LoadModule: "nouveau"
[    15.102] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    15.102] (II) Module nouveau: vendor="X.Org Foundation"
[    15.102] 	compiled for 1.10.1, module version = 0.0.16
[    15.102] 	Module class: X.Org Video Driver
[    15.102] 	ABI class: X.Org Video Driver, version 10.0
[    15.102] (II) LoadModule: "nv"
[    15.102] (WW) Warning, couldn't open module nv
[    15.102] (II) UnloadModule: "nv"
[    15.102] (II) Unloading nv
[    15.102] (EE) Failed to load module "nv" (module does not exist, 0)
[    15.102] (II) LoadModule: "vesa"
[    15.102] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.102] (II) Module vesa: vendor="X.Org Foundation"
[    15.102] 	compiled for 1.10.2, module version = 2.3.0
[    15.102] 	Module class: X.Org Video Driver
[    15.102] 	ABI class: X.Org Video Driver, version 10.0
[    15.102] (II) LoadModule: "fbdev"
[    15.103] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.103] (II) Module fbdev: vendor="X.Org Foundation"
[    15.103] 	compiled for 1.10.0, module version = 0.4.2
[    15.103] 	ABI class: X.Org Video Driver, version 10.0
[    15.103] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    15.103] (II) NOUVEAU driver for NVIDIA chipset families :
[    15.103] 	RIVA TNT        (NV04)
[    15.103] 	RIVA TNT2       (NV05)
[    15.103] 	GeForce 256     (NV10)
[    15.103] 	GeForce 2       (NV11, NV15)
[    15.103] 	GeForce 4MX     (NV17, NV18)
[    15.103] 	GeForce 3       (NV20)
[    15.103] 	GeForce 4Ti     (NV25, NV28)
[    15.103] 	GeForce FX      (NV3x)
[    15.103] 	GeForce 6       (NV4x)
[    15.103] 	GeForce 7       (G7x)
[    15.103] 	GeForce 8       (G8x)
[    15.103] 	GeForce GTX 200 (NVA0)
[    15.103] 	GeForce GTX 400 (NVC0)
[    15.103] (II) VESA: driver for VESA chipsets: vesa
[    15.103] (II) FBDEV: driver for framebuffer: fbdev
[    15.103] (++) using VT number 7

[    15.103] drmOpenDevice: node name is /dev/dri/card0
[    15.114] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    15.114] drmOpenDevice: node name is /dev/dri/card0
[    15.120] drmOpenByBusid: drmOpenMinor returns -1
[    15.121] drmOpenDevice: node name is /dev/dri/card1
[    15.124] drmOpenByBusid: drmOpenMinor returns -1
[    15.124] drmOpenDevice: node name is /dev/dri/card2
[    15.128] drmOpenByBusid: drmOpenMinor returns -1
[    15.128] drmOpenDevice: node name is /dev/dri/card3
[    15.132] drmOpenByBusid: drmOpenMinor returns -1
[    15.132] drmOpenDevice: node name is /dev/dri/card4
[    15.136] drmOpenByBusid: drmOpenMinor returns -1
[    15.136] drmOpenDevice: node name is /dev/dri/card5
[    15.140] drmOpenByBusid: drmOpenMinor returns -1
[    15.140] drmOpenDevice: node name is /dev/dri/card6
[    15.144] drmOpenByBusid: drmOpenMinor returns -1
[    15.144] drmOpenDevice: node name is /dev/dri/card7
[    15.148] drmOpenByBusid: drmOpenMinor returns -1
[    15.148] drmOpenDevice: node name is /dev/dri/card8
[    15.152] drmOpenByBusid: drmOpenMinor returns -1
[    15.152] drmOpenDevice: node name is /dev/dri/card9
[    15.156] drmOpenByBusid: drmOpenMinor returns -1
[    15.156] drmOpenDevice: node name is /dev/dri/card10
[    15.160] drmOpenByBusid: drmOpenMinor returns -1
[    15.160] drmOpenDevice: node name is /dev/dri/card11
[    15.164] drmOpenByBusid: drmOpenMinor returns -1
[    15.164] drmOpenDevice: node name is /dev/dri/card12
[    15.168] drmOpenByBusid: drmOpenMinor returns -1
[    15.168] drmOpenDevice: node name is /dev/dri/card13
[    15.172] drmOpenByBusid: drmOpenMinor returns -1
[    15.172] drmOpenDevice: node name is /dev/dri/card14
[    15.176] drmOpenByBusid: drmOpenMinor  returns -1
[    15.176] drmOpenDevice: node name is /dev/dri/card15
[    15.179] drmOpenByBusid: drmOpenMinor returns -1
[    15.179] drmOpenDevice: node name is /dev/dri/card0
[    15.185] drmOpenDevice: node name is /dev/dri/card0
[    15.189] drmOpenDevice: node name is /dev/dri/card1
[    15.193] drmOpenDevice: node name is /dev/dri/card2
[    15.197] drmOpenDevice: node name is /dev/dri/card3
[    15.201] drmOpenDevice: node name is /dev/dri/card4
[    15.205] drmOpenDevice: node name is /dev/dri/card5
[    15.208] drmOpenDevice: node name is /dev/dri/card6
[    15.212] drmOpenDevice: node name is /dev/dri/card7
[    15.216] drmOpenDevice: node name is /dev/dri/card8
[    15.219] drmOpenDevice: node name is /dev/dri/card9
[    15.223] drmOpenDevice: node name is /dev/dri/card10
[    15.227] drmOpenDevice: node name is /dev/dri/card11
[    15.230] drmOpenDevice: node name is /dev/dri/card12
[    15.234] drmOpenDevice: node name is /dev/dri/card13
[    15.238] drmOpenDevice: node name is /dev/dri/card14
[    15.242] drmOpenDevice: node name is /dev/dri/card15
[    15.247] (EE) [drm] failed to open device
[    15.247] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.247] vesa: Ignoring device with a bound kernel driver
[    15.247] (WW) Falling back to old probe method for vesa
[    15.247] (II) Loading sub module "fbdevhw"
[    15.247] (II) LoadModule: "fbdevhw"
[    15.247] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.247] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.247] 	compiled for 1.10.4, module version = 0.0.2
[    15.247] 	ABI class: X.Org Video Driver, version 10.0
[    15.247] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.247] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.247] (**) FBDEV(1): claimed PCI slot 1@0:0:0
[    15.247] (II) FBDEV(1): using default device
[    15.247] (II) FBDEV(1): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.247] (==) FBDEV(1): Depth 24, (==) framebuffer bpp 32
[    15.247] (==) FBDEV(1): RGB weight 888
[    15.247] (==) FBDEV(1): Default visual is TrueColor
[    15.247] (==) FBDEV(1): Using gamma correction (1.0, 1.0, 1.0)
[    15.247] (II) FBDEV(1): hardware: VESA VGA (video memory: 1216kB)
[    15.247] (II) FBDEV(1): checking modes against framebuffer device...
[    15.247] (II) FBDEV(1): checking modes against monitor...
[    15.247] (--) FBDEV(1): Virtual size is 640x480 (pitch 640)
[    15.247] (**) FBDEV(1):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[    15.247] (II) FBDEV(1): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz)
[    15.247] (==) FBDEV(1): DPI set to (96, 96)
[    15.247] (II) Loading sub module "fb"
[    15.247] (II) LoadModule: "fb"
[    15.247] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.247] (II) Module fb: vendor="X.Org Foundation"
[    15.247] 	compiled for 1.10.4, module version = 1.0.0
[    15.247] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.247] (**) FBDEV(1): using shadow framebuffer
[    15.247] (II) Loading sub module "shadow"
[    15.247] (II) LoadModule: "shadow"
[    15.247] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.247] (II) Module shadow: vendor="X.Org Foundation"
[    15.247] 	compiled for 1.10.4, module version = 1.1.0
[    15.247] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.248] (II) UnloadModule: "vesa"
[    15.248] (II) Unloading vesa
[    15.248] (==) Depth 24 pixmap format is 32 bpp
[    15.248] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    15.248] (==) FBDEV(0): Backing store disabled
[    15.248] (==) FBDEV(0): DPMS enabled
[    15.248] (==) RandR enabled
[    15.248] (II) Initializing built-in extension Generic Event Extension
[    15.248] (II) Initializing built-in extension SHAPE
[    15.248] (II) Initializing built-in extension MIT-SHM
[    15.248] (II) Initializing built-in extension XInputExtension
[    15.248] (II) Initializing built-in extension XTEST
[    15.248] (II) Initializing built-in extension BIG-REQUESTS
[    15.248] (II) Initializing built-in extension SYNC
[    15.248] (II) Initializing built-in extension XKEYBOARD
[    15.248] (II) Initializing built-in extension XC-MISC
[    15.248] (II) Initializing built-in extension SECURITY
[    15.248] (II) Initializing built-in extension XINERAMA
[    15.248] (II) Initializing built-in extension XFIXES
[    15.248] (II) Initializing built-in extension RENDER
[    15.248] (II) Initializing built-in extension RANDR
[    15.248] (II) Initializing built-in extension COMPOSITE
[    15.248] (II) Initializing built-in extension DAMAGE
[    15.248] (II) Initializing built-in extension GESTURE
[    15.252] (II) AIGLX: Screen 0 is not DRI2 capable
[    15.252] (II) AIGLX: Screen 0 is not DRI capable
[    15.252] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[    15.253] (II) AIGLX: Loaded and initialized swrast
[    15.253] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    15.258] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.263] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    15.264] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.264] (II) LoadModule: "evdev"
[    15.264] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.264] (II) Module evdev: vendor="X.Org Foundation"
[    15.264] 	compiled for 1.10.2, module version = 2.6.0
[    15.264] 	Module class: X.Org XInput Driver
[    15.264] 	ABI class: X.Org XInput driver, version 12.3
[    15.264] (II) Using input driver 'evdev' for 'Power Button'
[    15.264] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.264] (**) Power Button: always reports core events
[    15.264] (**) Power Button: Device: "/dev/input/event3"
[    15.264] (--) Power Button: Found keys
[    15.264] (II) Power Button: Configuring as keyboard
[    15.264] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    15.264] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.264] (**) Option "xkb_rules" "evdev"
[    15.264] (**) Option "xkb_model" "pc105"
[    15.264] (**) Option "xkb_layout" "it"
[    15.266] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    15.366] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    15.366] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.366] (II) Using input driver 'evdev' for 'Video Bus'
[    15.366] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.366] (**) Video Bus: always reports core events
[    15.366] (**) Video Bus: Device: "/dev/input/event10"
[    15.366] (--) Video Bus: Found keys
[    15.366] (II) Video Bus: Configuring as keyboard
[    15.366] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2c/LNXVIDEO:00/input/input10/event10"
[    15.366] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    15.366] (**) Option "xkb_rules" "evdev"
[    15.366] (**) Option "xkb_model" "pc105"
[    15.366] (**) Option "xkb_layout" "it"
[    15.372] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.372] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.372] (II) Using input driver 'evdev' for 'Power Button'
[    15.372] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.372] (**) Power Button: always reports core events
[    15.372] (**) Power Button: Device: "/dev/input/event0"
[    15.372] (--) Power Button: Found keys
[    15.372] (II) Power Button: Configuring as keyboard
[    15.372] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    15.372] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.372] (**) Option "xkb_rules" "evdev"
[    15.372] (**) Option "xkb_model" "pc105"
[    15.372] (**) Option "xkb_layout" "it"
[    15.373] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    15.373] (II) No input driver/identifier specified (ignoring)
[    15.373] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    15.373] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    15.373] (II) Using input driver 'evdev' for 'Sleep Button'
[    15.373] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.373] (**) Sleep Button: always reports core events
[    15.373] (**) Sleep Button: Device: "/dev/input/event1"
[    15.373] (--) Sleep Button: Found keys
[    15.373] (II) Sleep Button: Configuring as keyboard
[    15.373] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    15.373] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    15.373] (**) Option "xkb_rules" "evdev"
[    15.373] (**) Option "xkb_model" "pc105"
[    15.373] (**) Option "xkb_layout" "it"
[    15.374] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event12)
[    15.374] (II) No input driver/identifier specified (ignoring)
[    15.374] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event13)
[    15.374] (II) No input driver/identifier specified (ignoring)
[    15.374] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[    15.374] (II) No input driver/identifier specified (ignoring)
[    15.375] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event15)
[    15.375] (II) No input driver/identifier specified (ignoring)
[    15.375] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2HDM (/dev/input/event9)
[    15.375] (**) Laptop_Integrated_Webcam_2HDM:  Applying InputClass "evdev keyboard catchall"
[    15.375] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_2HDM'
[    15.375] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.375] (**) Laptop_Integrated_Webcam_2HDM: always reports core events
[    15.375] (**) Laptop_Integrated_Webcam_2HDM: Device: "/dev/input/event9"
[    15.375] (--) Laptop_Integrated_Webcam_2HDM: Found keys
[    15.375] (II) Laptop_Integrated_Webcam_2HDM: Configuring as keyboard
[    15.375] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input9/event9"
[    15.375] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2HDM" (type: KEYBOARD)
[    15.375] (**) Option "xkb_rules" "evdev"
[    15.375] (**) Option "xkb_model" "pc105"
[    15.375] (**) Option "xkb_layout" "it"
[    15.376] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event6)
[    15.376] (II) No input driver/identifier specified (ignoring)
[    15.376] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event7)
[    15.376] (II) No input driver/identifier specified (ignoring)
[    15.377] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/event5)
[    15.377] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Applying InputClass "evdev pointer catchall"
[    15.377] (II) Using input driver 'evdev' for 'Microsoft Microsoft Optical Mouse with Tilt Wheel'
[    15.377] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.377] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
[    15.377] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event5"
[    15.377] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
[    15.378] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
[    15.378] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found relative axes
[    15.378] (--) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
[    15.378] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
[    15.378] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Adding scrollwheel support
[    15.378] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
[    15.378] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.378] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5/event5"
[    15.378] (II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
[    15.378] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
[    15.378] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) keeping acceleration scheme 1
[    15.378] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration profile 0
[    15.378] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration factor: 2.000
[    15.378] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: (accel) acceleration threshold: 4
[    15.378] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/mouse0)
[    15.378] (II) No input driver/identifier specified (ignoring)
[    15.380] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    15.380] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.380] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.380] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.380] (**) AT Translated Set 2 keyboard: always reports core events
[    15.380] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    15.380] (--) AT Translated Set 2 keyboard: Found keys
[    15.380] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    15.380] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    15.380] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    15.380] (**) Option "xkb_rules" "evdev"
[    15.380] (**) Option "xkb_model" "pc105"
[    15.380] (**) Option "xkb_layout" "it"
[    15.380] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[    15.380] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.380] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    15.380] (II) LoadModule: "synaptics"
[    15.380] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.381] (II) Module synaptics: vendor="X.Org Foundation"
[    15.381] 	compiled for 1.10.4, module version = 1.4.1
[    15.381] 	Module class: X.Org XInput Driver
[    15.381] 	ABI class: X.Org XInput driver, version 12.3
[    15.381] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    15.381] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.381] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.381] (**) Option "Device" "/dev/input/event11"
[    15.528] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5398
[    15.528] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4728
[    15.528] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    15.528] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    15.528] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    15.656] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    15.656] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.768] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    15.769] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    15.769] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    15.769] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    15.769] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.039
[    15.769] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    15.769] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    15.769] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    15.769] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    15.770] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    15.770] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    15.770] (II) No input driver/identifier specified (ignoring)
[    15.773] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    15.773] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.773] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    15.773] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.773] (**) Dell WMI hotkeys: always reports core events
[    15.773] (**) Dell WMI hotkeys: Device: "/dev/input/event8"
[    15.773] (--) Dell WMI hotkeys: Found keys
[    15.773] (II) Dell WMI hotkeys: Configuring as keyboard
[    15.773] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[    15.773] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    15.773] (**) Option "xkb_rules" "evdev"
[    15.773] (**) Option "xkb_model" "pc105"
[    15.773] (**) Option "xkb_layout" "it"
[    15.777] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    26.699] (II) XKB: reuse xkmfile /var/lib/xkb/server-F852E81D2903E78D24267D023F61A4200171B031.xkm
```

---

### Post by blumagic on 2012-02-25
I am having similar problem. I would like to get a better screen resolution than 1024x768. Any assistance would be appreciated.

thanks
blu.....

---

### Post by anushcbe on 2012-02-27
Ubuntu 11.10; mini DV port connected projector is not working with twin view & hdmi port is not working with the Samsung inch-TV actually with none of the display device which has HDMI port, i have an nvidia graphics card. installed the update for nvidia driver.

help me pls with getting a twin view.

.

Thank you

---

