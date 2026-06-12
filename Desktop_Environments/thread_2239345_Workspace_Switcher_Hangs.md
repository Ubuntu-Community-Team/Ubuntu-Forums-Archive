---
title: "Workspace Switcher Hangs"
date: 2014-08-13
forum: Desktop Environments
---

### Post by jwh2505 on 2014-08-13
I recently did a fresh install of 14.04 LTS.  When I zoom out the workspace switcher to see all four workspaces and try to move a program window to a different workspace the display freezes before the move is completed and the only way to get out is to use the power button to force a reboot.  Otherwise, everything works normally.  I used 12.04 LTS for quite some time on the same computer and never had this issue.  Computer info below.

Asus A43E-VX277d
Intel Core i3-2330 M
Mobile Intel HM65 Express Chipset
Intel HD Graphics 3000
2 GB RAM 

All current updates to 14.04 LTS installed.

Any help will be greatly appreciated.

Jerry

---

### Post by tgalati4 on 2014-08-13
Check your Video RAM settings in BIOS--perhaps you need more RAM allocated for video in 14.04.  Also check your log files:

```
more /var/log/Xorg.0.log
```

---

### Post by jwh2505 on 2014-08-13
> **tgalati4 said:**
> Check your Video RAM settings in BIOS--perhaps you need more RAM allocated for video in 14.04.  Also check your log files:

```
more /var/log/Xorg.0.log
```

Thanks for your reply.  There doesn't seem to be a setting for Video RAM in the BIOS, been through all the menus, don't see one.   I'm not sure what to look for in the log file.  Here's a copy:

[    18.861] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    18.861] X Protocol Version 11, Revision 0
[    18.861] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    18.861] Current Operating System: Linux laptop 3.13.0-33-generic #58-Ubuntu SMP Tue Jul 29 16:47:17 UTC 2014 i686
[    18.861] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-33-generic root=UUID=49e8688e-73e9-42c1-8a2f-0e26b1cb8f23 ro quiet splash
[    18.861] Build Date: 16 April 2014  01:40:08PM
[    18.861] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.861] Current version of pixman: 0.30.2
[    18.861] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    18.861] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.861] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 13 21:38:06 2014
[    18.893] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.894] (==) No Layout section.  Using the first Screen section.
[    18.894] (==) No screen section available. Using defaults.
[    18.894] (**) |-->Screen "Default Screen Section" (0)
[    18.894] (**) |   |-->Monitor "<default monitor>"
[    18.895] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.895] (==) Automatically adding devices
[    18.895] (==) Automatically enabling devices
[    18.895] (==) Automatically adding GPU devices
[    18.895] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.895] 	Entry deleted from font path.
[    18.895] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.895] 	Entry deleted from font path.
[    18.895] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.895] 	Entry deleted from font path.
[    18.895] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.895] 	Entry deleted from font path.
[    18.895] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.895] 	Entry deleted from font path.
[    18.895] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.895] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.895] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.895] (II) Loader magic: 0xb77196c0
[    18.895] (II) Module ABI versions:
[    18.895] 	X.Org ANSI C Emulation: 0.4
[    18.895] 	X.Org Video Driver: 15.0
[    18.895] 	X.Org XInput driver : 20.0
[    18.895] 	X.Org Server Extension : 8.0
[    18.896] (II) xfree86: Adding drm device (/dev/dri/card0)
[    18.899] (--) PCI:*(0:0:2:0) 8086:0116:1043:1652 rev 9, Mem @ 0xddc00000/4194304, 0xc0000000/268435456, I/O @ 0x0000e000/64
[    18.899] Initializing built-in extension Generic Event Extension
[    18.899] Initializing built-in extension SHAPE
[    18.899] Initializing built-in extension MIT-SHM
[    18.899] Initializing built-in extension XInputExtension
[    18.899] Initializing built-in extension XTEST
[    18.899] Initializing built-in extension BIG-REQUESTS
[    18.899] Initializing built-in extension SYNC
[    18.899] Initializing built-in extension XKEYBOARD
[    18.899] Initializing built-in extension XC-MISC
[    18.899] Initializing built-in extension SECURITY
[    18.899] Initializing built-in extension XINERAMA
[    18.899] Initializing built-in extension XFIXES
[    18.899] Initializing built-in extension RENDER
[    18.900] Initializing built-in extension RANDR
[    18.900] Initializing built-in extension COMPOSITE
[    18.900] Initializing built-in extension DAMAGE
[    18.900] Initializing built-in extension MIT-SCREEN-SAVER
[    18.900] Initializing built-in extension DOUBLE-BUFFER
[    18.900] Initializing built-in extension RECORD
[    18.900] Initializing built-in extension DPMS
[    18.900] Initializing built-in extension Present
[    18.900] Initializing built-in extension DRI3
[    18.900] Initializing built-in extension X-Resource
[    18.900] Initializing built-in extension XVideo
[    18.900] Initializing built-in extension XVideo-MotionCompensation
[    18.900] Initializing built-in extension SELinux
[    18.900] Initializing built-in extension XFree86-VidModeExtension
[    18.900] Initializing built-in extension XFree86-DGA
[    18.900] Initializing built-in extension XFree86-DRI
[    18.900] Initializing built-in extension DRI2
[    18.900] (II) LoadModule: "glx"
[    18.929] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.327] (II) Module glx: vendor="X.Org Foundation"
[    19.327] 	compiled for 1.15.1, module version = 1.0.0
[    19.327] 	ABI class: X.Org Server Extension, version 8.0
[    19.327] (==) AIGLX enabled
[    19.327] Loading extension GLX
[    19.327] (==) Matched intel as autoconfigured driver 0
[    19.327] (==) Matched intel as autoconfigured driver 1
[    19.327] (==) Matched modesetting as autoconfigured driver 2
[    19.327] (==) Matched fbdev as autoconfigured driver 3
[    19.327] (==) Matched vesa as autoconfigured driver 4
[    19.327] (==) Assigned the driver to the xf86ConfigLayout
[    19.327] (II) LoadModule: "intel"
[    19.354] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.392] (II) Module intel: vendor="X.Org Foundation"
[    19.392] 	compiled for 1.15.1, module version = 2.99.914
[    19.392] 	Module class: X.Org Video Driver
[    19.392] 	ABI class: X.Org Video Driver, version 15.0
[    19.392] (II) LoadModule: "modesetting"
[    19.392] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    19.393] (II) Module modesetting: vendor="X.Org Foundation"
[    19.393] 	compiled for 1.15.0, module version = 0.8.1
[    19.393] 	Module class: X.Org Video Driver
[    19.393] 	ABI class: X.Org Video Driver, version 15.0
[    19.393] (II) LoadModule: "fbdev"
[    19.393] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.393] (II) Module fbdev: vendor="X.Org Foundation"
[    19.393] 	compiled for 1.15.0, module version = 0.4.4
[    19.393] 	Module class: X.Org Video Driver
[    19.393] 	ABI class: X.Org Video Driver, version 15.0
[    19.393] (II) LoadModule: "vesa"
[    19.393] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.393] (II) Module vesa: vendor="X.Org Foundation"
[    19.393] 	compiled for 1.15.0, module version = 2.3.3
[    19.393] 	Module class: X.Org Video Driver
[    19.393] 	ABI class: X.Org Video Driver, version 15.0
[    19.393] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    19.394] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    19.394] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    19.394] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    19.394] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    19.394] (II) FBDEV: driver for framebuffer: fbdev
[    19.394] (II) VESA: driver for VESA chipsets: vesa
[    19.394] (++) using VT number 7

[    19.394] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    19.394] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.914+git20140811.6554cf0a-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    19.394] (II) intel(0): SNA compiled for use with valgrind
[    19.394] (WW) Falling back to old probe method for modesetting
[    19.394] (WW) Falling back to old probe method for fbdev
[    19.394] (II) Loading sub module "fbdevhw"
[    19.394] (II) LoadModule: "fbdevhw"
[    19.394] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.394] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.394] 	compiled for 1.15.1, module version = 0.0.2
[    19.395] 	ABI class: X.Org Video Driver, version 15.0
[    19.395] (WW) Falling back to old probe method for vesa
[    19.395] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 3000
[    19.395] (--) intel(0): CPU: x86, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    19.395] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    19.396] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    19.396] (==) intel(0): RGB weight 888
[    19.396] (==) intel(0): Default visual is TrueColor
[    19.396] (II) intel(0): Output LVDS1 has no monitor section
[    19.397] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output LVDS1
[    19.397] (II) intel(0): Enabled output LVDS1
[    19.397] (II) intel(0): Output VGA1 has no monitor section
[    19.397] (II) intel(0): Enabled output VGA1
[    19.397] (II) intel(0): Output HDMI1 has no monitor section
[    19.397] (II) intel(0): Enabled output HDMI1
[    19.397] (II) intel(0): Output DP1 has no monitor section
[    19.397] (II) intel(0): Enabled output DP1
[    19.397] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    19.397] (II) intel(0): Output VIRTUAL1 has no monitor section
[    19.397] (II) intel(0): Enabled output VIRTUAL1
[    19.397] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    19.397] (==) intel(0): TearFree disabled
[    19.397] (==) intel(0): DPI set to (96, 96)
[    19.397] (II) Loading sub module "dri3"
[    19.397] (II) LoadModule: "dri3"
[    19.398] (WW) Warning, couldn't open module dri3
[    19.398] (II) UnloadModule: "dri3"
[    19.398] (II) Unloading dri3
[    19.398] (EE) intel: Failed to load module "dri3" (module does not exist, 0)
[    19.398] (II) Loading sub module "dri2"
[    19.398] (II) LoadModule: "dri2"
[    19.398] (II) Module "dri2" already built-in
[    19.398] (II) Loading sub module "present"
[    19.398] (II) LoadModule: "present"
[    19.398] (WW) Warning, couldn't open module present
[    19.398] (II) UnloadModule: "present"
[    19.398] (II) Unloading present
[    19.398] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    19.398] (II) UnloadModule: "modesetting"
[    19.398] (II) Unloading modesetting
[    19.398] (II) UnloadModule: "fbdev"
[    19.398] (II) Unloading fbdev
[    19.398] (II) UnloadSubModule: "fbdevhw"
[    19.398] (II) Unloading fbdevhw
[    19.399] (II) UnloadModule: "vesa"
[    19.399] (II) Unloading vesa
[    19.399] (==) Depth 24 pixmap format is 32 bpp
[    19.399] (II) intel(0): SNA initialized with Sandybridge (gen6, gt2) backend
[    19.399] (==) intel(0): Backing store enabled
[    19.399] (==) intel(0): Silken mouse enabled
[    19.399] (II) intel(0): HW Cursor enabled
[    19.399] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.399] (==) intel(0): DPMS enabled
[    19.399] (II) intel(0): [DRI2] Setup complete
[    19.399] (II) intel(0): [DRI2]   DRI driver: i965
[    19.399] (II) intel(0): [DRI2]   VDPAU driver: i965
[    19.399] (II) intel(0): direct rendering: DRI2 enabled
[    19.399] (==) intel(0): display hotplug detection enabled
[    19.399] (--) RandR disabled
[    19.407] (II) SELinux: Disabled on system
[    19.489] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.489] (II) AIGLX: enabled GLX_ARB_create_context
[    19.489] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    19.489] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    19.489] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.489] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.489] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    19.489] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    19.489] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.489] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    19.489] (II) AIGLX: Loaded and initialized i965
[    19.489] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.493] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.512] (II) intel(0): Setting screen physical size to 361 x 203
[    19.523] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.526] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    19.526] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.526] (II) LoadModule: "evdev"
[    19.527] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.552] (II) Module evdev: vendor="X.Org Foundation"
[    19.552] 	compiled for 1.15.0, module version = 2.8.2
[    19.552] 	Module class: X.Org XInput Driver
[    19.552] 	ABI class: X.Org XInput driver, version 20.0
[    19.552] (II) Using input driver 'evdev' for 'Power Button'
[    19.552] (**) Power Button: always reports core events
[    19.552] (**) evdev: Power Button: Device: "/dev/input/event2"
[    19.552] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.552] (--) evdev: Power Button: Found keys
[    19.553] (II) evdev: Power Button: Configuring as keyboard
[    19.553] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    19.553] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.553] (**) Option "xkb_rules" "evdev"
[    19.553] (**) Option "xkb_model" "pc105"
[    19.553] (**) Option "xkb_layout" "us"
[    19.553] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    19.553] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.553] (II) Using input driver 'evdev' for 'Video Bus'
[    19.553] (**) Video Bus: always reports core events
[    19.553] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    19.553] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.553] (--) evdev: Video Bus: Found keys
[    19.553] (II) evdev: Video Bus: Configuring as keyboard
[    19.553] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input15/event8"
[    19.553] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    19.553] (**) Option "xkb_rules" "evdev"
[    19.553] (**) Option "xkb_model" "pc105"
[    19.553] (**) Option "xkb_layout" "us"
[    19.554] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    19.554] (II) No input driver specified, ignoring this device.
[    19.554] (II) This device may have been added with another device file.
[    19.554] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    19.554] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.554] (II) Using input driver 'evdev' for 'Sleep Button'
[    19.554] (**) Sleep Button: always reports core events
[    19.554] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    19.554] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    19.554] (--) evdev: Sleep Button: Found keys
[    19.554] (II) evdev: Sleep Button: Configuring as keyboard
[    19.554] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    19.554] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    19.554] (**) Option "xkb_rules" "evdev"
[    19.554] (**) Option "xkb_model" "pc105"
[    19.554] (**) Option "xkb_layout" "us"
[    19.554] (II) config/udev: Adding drm device (/dev/dri/card0)
[    19.554] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    19.555] (II) config/udev: Adding input device ASUS USB2.0 WebCam (/dev/input/event6)
[    19.555] (**) ASUS USB2.0 WebCam: Applying InputClass "evdev keyboard catchall"
[    19.555] (II) Using input driver 'evdev' for 'ASUS USB2.0 WebCam'
[    19.555] (**) ASUS USB2.0 WebCam: always reports core events
[    19.555] (**) evdev: ASUS USB2.0 WebCam: Device: "/dev/input/event6"
[    19.555] (--) evdev: ASUS USB2.0 WebCam: Vendor 0x58f Product 0xa014
[    19.555] (--) evdev: ASUS USB2.0 WebCam: Found keys
[    19.555] (II) evdev: ASUS USB2.0 WebCam: Configuring as keyboard
[    19.555] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input13/event6"
[    19.555] (II) XINPUT: Adding extended input device "ASUS USB2.0 WebCam" (type: KEYBOARD, id 9)
[    19.555] (**) Option "xkb_rules" "evdev"
[    19.555] (**) Option "xkb_model" "pc105"
[    19.555] (**) Option "xkb_layout" "us"
[    19.555] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[    19.555] (II) No input driver specified, ignoring this device.
[    19.555] (II) This device may have been added with another device file.
[    19.556] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.556] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.556] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[    19.556] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    19.556] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    19.556] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    19.556] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[    19.556] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc03d
[    19.556] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[    19.556] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    19.556] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    19.556] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    19.556] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    19.556] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    19.556] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    19.556] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.556] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12/event4"
[    19.556] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 10)
[    19.556] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    19.557] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    19.557] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    19.557] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    19.557] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    19.557] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    19.557] (II) No input driver specified, ignoring this device.
[    19.557] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event7)
[    19.557] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    19.557] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    19.557] (**) Asus WMI hotkeys: always reports core events
[    19.557] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event7"
[    19.557] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    19.557] (--) evdev: Asus WMI hotkeys: Found keys
[    19.557] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    19.557] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input14/event7"
[    19.557] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    19.557] (**) Option "xkb_rules" "evdev"
[    19.557] (**) Option "xkb_model" "pc105"
[    19.557] (**) Option "xkb_layout" "us"
[    19.558] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    19.558] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.558] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.558] (**) AT Translated Set 2 keyboard: always reports core events
[    19.558] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    19.558] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    19.558] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    19.558] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    19.558] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    19.558] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    19.558] (**) Option "xkb_rules" "evdev"
[    19.558] (**) Option "xkb_model" "pc105"
[    19.558] (**) Option "xkb_layout" "us"
[    19.558] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event5)
[    19.558] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    19.558] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    19.558] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    19.558] (II) LoadModule: "synaptics"
[    19.559] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.559] (II) Module synaptics: vendor="X.Org Foundation"
[    19.559] 	compiled for 1.15.0, module version = 1.7.4
[    19.559] 	Module class: X.Org XInput Driver
[    19.559] 	ABI class: X.Org XInput driver, version 20.0
[    19.559] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    19.559] (**) ETPS/2 Elantech Touchpad: always reports core events
[    19.559] (**) Option "Device" "/dev/input/event5"
[    19.676] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508 (res 0)
[    19.676] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320 (res 0)
[    19.676] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    19.676] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    19.676] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    19.676] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    19.676] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    19.676] (**) ETPS/2 Elantech Touchpad: always reports core events
[    19.724] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event5"
[    19.724] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    19.724] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    19.724] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    19.724] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.071
[    19.724] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    19.724] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    19.724] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    19.724] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    19.724] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    19.724] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    19.724] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    22.904] (II) intel(0): EDID vendor "SEC", prod id 17730
[    22.904] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    22.904] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    22.904] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    22.904] (II) intel(0): Printing DDC gathered Modelines:
[    22.904] (II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 773 778 790 -hsync -vsync (47.4 kHz eP)
[    37.542] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    49.932] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm

---

