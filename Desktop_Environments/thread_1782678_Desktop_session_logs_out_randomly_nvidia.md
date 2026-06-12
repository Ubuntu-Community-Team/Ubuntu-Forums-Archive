---
title: "Desktop session logs out randomly? nvidia"
date: 2011-06-14
forum: Desktop Environments
---

### Post by talkfig on 2011-06-14
My desktop session logs out (or crashes) seemingly randomly,

maybe every other day, or sometimes 5 days between crashes.

when "it" happens, everything closes and I am presented
with greeter.


root@moto:/var/log/gdm# uname -a
Linux moto 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
root@moto:/var/log/gdm# cat /etc/issue
Ubuntu 10.04.2 LTS \n \l


[ /var/log/gdm/:1.log.1]

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux moto 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-28-generic root=/dev/sda6 ro pci=nomsi quiet splash
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Jun 14 17:02:12 2011
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices

(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(--) using VT number 1

(--) PCI:*(0:5:0:0) 10de:00ce:10de:0243 nVidia Corporation NV41GL [Quadro FX 1400] rev 162, Mem @ 0xf8000000/16777216, 0xd8000000/134217728, 0xf9000000/16777216, BIOS @ 0x????????/131072
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
(==) AIGLX enabled
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
(II) FBDEV: driver for framebuffer: fbdev
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
(**) FBDEV(0): claimed PCI slot 5@0:0:0
(II) FBDEV(0): using default device
(II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: nouveaufb (video memory: 8100kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
(**) FBDEV(0):  Built-in mode "current"
(==) FBDEV(0): DPI set to (96, 96)
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
(**) FBDEV(0): using shadow framebuffer
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
(==) Depth 24 pixmap format is 32 bpp
(==) FBDEV(0): Backing store disabled
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

... (last line repeats, lots of pages...)

(==) FBDEV(0): DPMS enabled
(==) RandR enabled
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device HP HP USB Laser Mouse (/dev/input/event3)
(**) HP HP USB Laser Mouse: Applying InputClass "evdev pointer catchall"
(**) HP HP USB Laser Mouse: always reports core events
(**) HP HP USB Laser Mouse: Device: "/dev/input/event3"
(II) HP HP USB Laser Mouse: Found 3 mouse buttons
(II) HP HP USB Laser Mouse: Found scroll wheel(s)
(II) HP HP USB Laser Mouse: Found relative axes
(II) HP HP USB Laser Mouse: Found x and y relative axes
(II) HP HP USB Laser Mouse: Configuring as mouse
(**) HP HP USB Laser Mouse: YAxisMapping: buttons 4 and 5
(**) HP HP USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HP HP USB Laser Mouse" (type: MOUSE)
(II) HP HP USB Laser Mouse: initialized for relative axes.
(II) config/udev: Adding input device HP HP USB Laser Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device C-Media Electronics Inc.       USB PnP Sound Device (/dev/input/event4)
(**) C-Media Electronics Inc.       USB PnP Sound Device: Applying InputClass "evdev keyboard catchall"
(**) C-Media Electronics Inc.       USB PnP Sound Device: always reports core events
(**) C-Media Electronics Inc.       USB PnP Sound Device: Device: "/dev/input/event4"
(II) C-Media Electronics Inc.       USB PnP Sound Device: Found 1 mouse buttons
(II) C-Media Electronics Inc.       USB PnP Sound Device: Found keys
(II) C-Media Electronics Inc.       USB PnP Sound Device: Configuring as mouse
(II) C-Media Electronics Inc.       USB PnP Sound Device: Configuring as keyboard
(**) C-Media Electronics Inc.       USB PnP Sound Device: YAxisMapping: buttons 4 and 5
(**) C-Media Electronics Inc.       USB PnP Sound Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "C-Media Electronics Inc.       USB PnP Sound Device" (type: KEYBOARD)
(II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event5)
(**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event5"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event6)
(**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
(**) Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event6"
(II) Mitsumi Electric Apple Extended USB Keyboard: Found keys
(II) Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

... ( last line repeats, a whole lot of pages! )


(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(II) Power Button: Close
(II) Power Button: Close
(II) HP HP USB Laser Mouse: Close
(II) C-Media Electronics Inc.       USB PnP Sound Device: Close
(II) Mitsumi Electric Apple Extended USB Keyboard: Close
(II) Mitsumi Electric Apple Extended USB Keyboard: Close
(II) Macintosh mouse button emulation: Close
 ddxSigGiveUp: Closing log

---

### Post by l0co on 2011-11-22
Did you solve the problem? I have the same, started to be annoying...

BTW. For me this is frequently related to some action, the most often on "ENTER" hit, sometimes on left mouse button click. Very frequenty when I'm in chrome browser

---

### Post by talkfig on 2011-11-22
Switch to "nvidia" driver,  problem gone.

---

### Post by LinuxFan999 on 2011-11-22
Are you using Ubuntu on a Mac? I see Apple mentioned in the log.

---

### Post by talkfig on 2011-11-22
Just a MAC keyboard...

---

### Post by l0co on 2011-11-23
It looks that for me this is related to **[this]("http://www.google.com/support/forum/p/Chrome/thread?tid=0e5cf9dcd69aa363&hl=en")** google chrome problem. I currently have nvidia drivers installed.

---

