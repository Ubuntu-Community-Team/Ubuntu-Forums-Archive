---
title: "unity 3d will not load"
date: 2011-05-03
forum: Desktop Environments
---

### Post by Mia1990 on 2011-05-03
unity 3d never loaded from the first time i installed ubuntu 11.04.When i run /usr/lib/nux/unity_support_test -p this is what i get

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

I don't understand why i can't run unity i have a nvidia 256 mb card but in additional drivers is says this driver is active but not currently in use this error is a bug in additional drivers but the bug report says that nvidia is running and it's just a false report.I don't know if this is true or not.Could anyone help?

---

### Post by Elfy on 2011-05-03
You could check in the xorg log in sys-admin-log viewer and see whether nvidia or nouveau is being used.

You could also try disabling the driver, rebooting and reinstalling the driver.

---

### Post by Mia1990 on 2011-05-03
I reinstalled the nvidia driver it didn't help.From what i can tell it looks like the nvidia is loading and i can run compiz just not unity.Here is my log file 

> [    22.961] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    22.961] X Protocol Version 11, Revision 0
[    22.961] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    22.961] Current Operating System: Linux mia-Dimension-4600i 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    22.961] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=2db580b4-8c97-4055-a3be-eec372ec118e ro nopat quiet splash vt.handoff=7
[    22.961] Build Date: 19 April 2011  03:33:17PM
[    22.961] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.961] Current version of pixman: 0.20.2
[    22.961]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    22.961] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.962] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May  3 09:03:48 2011
[    22.962] (==) Using config file: "/etc/X11/xorg.conf"
[    22.962] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.136] (==) No Layout section.  Using the first Screen section.
[    23.136] (==) No screen section available. Using defaults.
[    23.136] (**) |-->Screen "Default Screen Section" (0)
[    23.136] (**) |   |-->Monitor "<default monitor>"
[    23.136] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    23.136] (**) |   |-->Device "Default Device"
[    23.136] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    23.136] (==) Automatically adding devices
[    23.136] (==) Automatically enabling devices
[    23.136] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.137]     Entry deleted from font path.
[    23.137] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.137]     Entry deleted from font path.
[    23.137] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.137]     Entry deleted from font path.
[    23.137] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.137]     Entry deleted from font path.
[    23.137] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.137]     Entry deleted from font path.
[    23.137] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    23.137] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.137] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.137] (II) Loader magic: 0x81ffde0
[    23.137] (II) Module ABI versions:
[    23.137]     X.Org ANSI C Emulation: 0.4
[    23.137]     X.Org Video Driver: 10.0
[    23.137]     X.Org XInput driver : 12.3
[    23.137]     X.Org Server Extension : 5.0
[    23.138] (--) PCI: (0:0:2:0) 8086:2572:1028:0174 rev 2, Mem @ 0xd0000000/134217728, 0xfeb80000/524288, I/O @ 0x0000ed98/8
[    23.138] (--) PCI:*(0:1:1:0) 10de:0326:270f:196c rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
[    23.139] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.139] (II) LoadModule: "extmod"
[    23.179] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.179] (II) Module extmod: vendor="X.Org Foundation"
[    23.179]     compiled for 1.10.1, module version = 1.0.0
[    23.179]     Module class: X.Org Server Extension
[    23.179]     ABI class: X.Org Server Extension, version 5.0
[    23.179] (II) Loading extension MIT-SCREEN-SAVER
[    23.179] (II) Loading extension XFree86-VidModeExtension
[    23.179] (II) Loading extension XFree86-DGA
[    23.179] (II) Loading extension DPMS
[    23.179] (II) Loading extension XVideo
[    23.179] (II) Loading extension XVideo-MotionCompensation
[    23.179] (II) Loading extension X-Resource
[    23.179] (II) LoadModule: "dbe"
[    23.180] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.180] (II) Module dbe: vendor="X.Org Foundation"
[    23.180]     compiled for 1.10.1, module version = 1.0.0
[    23.180]     Module class: X.Org Server Extension
[    23.180]     ABI class: X.Org Server Extension, version 5.0
[    23.180] (II) Loading extension DOUBLE-BUFFER
[    23.180] (II) LoadModule: "glx"
[    23.180] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    24.240] (II) Module glx: vendor="NVIDIA Corporation"
[    24.240]     compiled for 4.0.2, module version = 1.0.0
[    24.240]     Module class: X.Org Server Extension
[    24.240] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[    24.240] (II) Loading extension GLX
[    24.240] (II) LoadModule: "record"
[    24.241] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.241] (II) Module record: vendor="X.Org Foundation"
[    24.241]     compiled for 1.10.1, module version = 1.13.0
[    24.241]     Module class: X.Org Server Extension
[    24.241]     ABI class: X.Org Server Extension, version 5.0
[    24.241] (II) Loading extension RECORD
[    24.241] (II) LoadModule: "dri"
[    24.241] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.242] (II) Module dri: vendor="X.Org Foundation"
[    24.242]     compiled for 1.10.1, module version = 1.0.0
[    24.242]     ABI class: X.Org Server Extension, version 5.0
[    24.242] (II) Loading extension XFree86-DRI
[    24.242] (II) LoadModule: "dri2"
[    24.242] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.243] (II) Module dri2: vendor="X.Org Foundation"
[    24.243]     compiled for 1.10.1, module version = 1.2.0
[    24.243]     ABI class: X.Org Server Extension, version 5.0
[    24.243] (II) Loading extension DRI2
[    24.243] (==) Matched nvidia as autoconfigured driver 0
[    24.243] (==) Matched nouveau as autoconfigured driver 1
[    24.243] (==) Matched nv as autoconfigured driver 2
[    24.243] (==) Matched vesa as autoconfigured driver 3
[    24.243] (==) Matched fbdev as autoconfigured driver 4
[    24.243] (==) Assigned the driver to the xf86ConfigLayout
[    24.243] (II) LoadModule: "nvidia"
[    24.243] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    24.310] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.310]     compiled for 4.0.2, module version = 1.0.0
[    24.310]     Module class: X.Org Video Driver
[    24.324] (II) LoadModule: "nouveau"
[    24.324] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    24.325] (II) Module nouveau: vendor="X.Org Foundation"
[    24.325]     compiled for 1.10.0, module version = 0.0.16
[    24.325]     Module class: X.Org Video Driver
[    24.325]     ABI class: X.Org Video Driver, version 10.0
[    24.325] (II) LoadModule: "nv"
[    24.326] (WW) Warning, couldn't open module nv
[    24.326] (II) UnloadModule: "nv"
[    24.326] (II) Unloading nv
[    24.326] (EE) Failed to load module "nv" (module does not exist, 0)
[    24.326] (II) LoadModule: "vesa"
[    24.326] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.326] (II) Module vesa: vendor="X.Org Foundation"
[    24.326]     compiled for 1.10.0, module version = 2.3.0
[    24.326]     Module class: X.Org Video Driver
[    24.326]     ABI class: X.Org Video Driver, version 10.0
[    24.327] (II) LoadModule: "fbdev"
[    24.327] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.327] (II) Module fbdev: vendor="X.Org Foundation"
[    24.327]     compiled for 1.10.0, module version = 0.4.2
[    24.327]     ABI class: X.Org Video Driver, version 10.0
[    24.332] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[    24.340] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    24.340] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    24.340] (II) NOUVEAU driver for NVIDIA chipset families :
[    24.340]     RIVA TNT    (NV04)
[    24.340]     RIVA TNT2   (NV05)
[    24.340]     GeForce 256 (NV10)
[    24.340]     GeForce 2   (NV11, NV15)
[    24.340]     GeForce 4MX (NV17, NV18)
[    24.340]     GeForce 3   (NV20)
[    24.340]     GeForce 4Ti (NV25, NV28)
[    24.340]     GeForce FX  (NV3x)
[    24.340]     GeForce 6   (NV4x)
[    24.340]     GeForce 7   (G7x)
[    24.340]     GeForce 8   (G8x)
[    24.340] (II) VESA: driver for VESA chipsets: vesa
[    24.340] (II) FBDEV: driver for framebuffer: fbdev
[    24.340] (++) using VT number 7

[    24.343] (II) Loading sub module "fb"
[    24.343] (II) LoadModule: "fb"
[    24.343] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.344] (II) Module fb: vendor="X.Org Foundation"
[    24.344]     compiled for 1.10.1, module version = 1.0.0
[    24.344]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.344] (II) Loading sub module "wfb"
[    24.344] (II) LoadModule: "wfb"
[    24.344] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    24.365] (II) Module wfb: vendor="X.Org Foundation"
[    24.365]     compiled for 1.10.1, module version = 1.0.0
[    24.365]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.365] (II) Loading sub module "ramdac"
[    24.365] (II) LoadModule: "ramdac"
[    24.365] (II) Module "ramdac" already built-in
[    24.365] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    24.365] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    24.365] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.365] (WW) Falling back to old probe method for vesa
[    24.365] (WW) Falling back to old probe method for fbdev
[    24.365] (II) Loading sub module "fbdevhw"
[    24.365] (II) LoadModule: "fbdevhw"
[    24.365] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.366] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.366]     compiled for 1.10.1, module version = 0.0.2
[    24.366]     ABI class: X.Org Video Driver, version 10.0
[    24.384] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    24.384] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    24.384] (==) NVIDIA(0): RGB weight 888
[    24.384] (==) NVIDIA(0): Default visual is TrueColor
[    24.384] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    24.384] (**) NVIDIA(0): Option "NoLogo" "True"
[    24.387] (**) NVIDIA(0): Enabling RENDER acceleration
[    24.387] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    24.387] (II) NVIDIA(0):     enabled.
[    26.155] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 (NV34) at PCI:1:1:0 (GPU-0)
[    26.155] (--) NVIDIA(0): Memory: 262144 kBytes
[    26.155] (--) NVIDIA(0): VideoBIOS: 04.34.20.69.65
[    26.155] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    26.155] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:1:0:
[    26.155] (--) NVIDIA(0):     Acer P191W (CRT-0)
[    26.155] (--) NVIDIA(0): Acer P191W (CRT-0): 350.0 MHz maximum pixel clock
[    26.156] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    26.156] (==) NVIDIA(0): 
[    26.156] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    26.156] (==) NVIDIA(0):     will be used as the requested mode.
[    26.156] (==) NVIDIA(0): 
[    26.156] (II) NVIDIA(0): Validated modes:
[    26.156] (II) NVIDIA(0):     "nvidia-auto-select"
[    26.156] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    26.157] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    26.157] (--) NVIDIA(0):     option
[    26.157] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    26.158] (II) UnloadModule: "nouveau"
[    26.158] (II) Unloading nouveau
[    26.159] (II) UnloadModule: "vesa"
[    26.159] (II) Unloading vesa
[    26.159] (II) UnloadModule: "fbdev"
[    26.159] (II) Unloading fbdev
[    26.159] (II) UnloadModule: "fbdevhw"
[    26.159] (II) Unloading fbdevhw
[    26.159] (--) Depth 24 pixmap format is 32 bpp
[    26.160] (II) NVIDIA(0): Initialized GPU GART.
[    26.164] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    26.272] (II) Loading extension NV-GLX
[    26.311] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    26.316] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    26.316] (==) NVIDIA(0): Backing store disabled
[    26.316] (==) NVIDIA(0): Silken mouse enabled
[    26.317] (==) NVIDIA(0): DPMS enabled
[    26.317] (II) Loading extension NV-CONTROL
[    26.318] (==) RandR enabled
[    26.318] (II) Initializing built-in extension Generic Event Extension
[    26.318] (II) Initializing built-in extension SHAPE
[    26.318] (II) Initializing built-in extension MIT-SHM
[    26.318] (II) Initializing built-in extension XInputExtension
[    26.318] (II) Initializing built-in extension XTEST
[    26.318] (II) Initializing built-in extension BIG-REQUESTS
[    26.318] (II) Initializing built-in extension SYNC
[    26.318] (II) Initializing built-in extension XKEYBOARD
[    26.318] (II) Initializing built-in extension XC-MISC
[    26.318] (II) Initializing built-in extension SECURITY
[    26.318] (II) Initializing built-in extension XINERAMA
[    26.318] (II) Initializing built-in extension XFIXES
[    26.318] (II) Initializing built-in extension RENDER
[    26.318] (II) Initializing built-in extension RANDR
[    26.318] (II) Initializing built-in extension COMPOSITE
[    26.318] (II) Initializing built-in extension DAMAGE
[    26.318] (II) Initializing built-in extension GESTURE
[    26.322] (II) Initializing extension GLX
[    26.353] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.367] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.367] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.367] (II) LoadModule: "evdev"
[    26.368] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.368] (II) Module evdev: vendor="X.Org Foundation"
[    26.368]     compiled for 1.10.0.902, module version = 2.6.0
[    26.368]     Module class: X.Org XInput Driver
[    26.368]     ABI class: X.Org XInput driver, version 12.3
[    26.368] (II) Using input driver 'evdev' for 'Power Button'
[    26.368] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.368] (**) Power Button: always reports core events
[    26.368] (**) Power Button: Device: "/dev/input/event1"
[    26.369] (--) Power Button: Found keys
[    26.369] (II) Power Button: Configuring as keyboard
[    26.369] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    26.369] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.369] (**) Option "xkb_rules" "evdev"
[    26.369] (**) Option "xkb_model" "pc105"
[    26.369] (**) Option "xkb_layout" "us"
[    26.371] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.371] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.371] (II) Using input driver 'evdev' for 'Power Button'
[    26.371] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.371] (**) Power Button: always reports core events
[    26.371] (**) Power Button: Device: "/dev/input/event0"
[    26.371] (--) Power Button: Found keys
[    26.372] (II) Power Button: Configuring as keyboard
[    26.372] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    26.372] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.372] (**) Option "xkb_rules" "evdev"
[    26.372] (**) Option "xkb_model" "pc105"
[    26.372] (**) Option "xkb_layout" "us"
[    26.384] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    26.384] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.384] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.384] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.384] (**) AT Translated Set 2 keyboard: always reports core events
[    26.384] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    26.384] (--) AT Translated Set 2 keyboard: Found keys
[    26.384] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.384] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    26.384] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.384] (**) Option "xkb_rules" "evdev"
[    26.384] (**) Option "xkb_model" "pc105"
[    26.384] (**) Option "xkb_layout" "us"
[    26.385] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event3)
[    26.385] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    26.385] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[    26.385] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.385] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[    26.385] (**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
[    26.386] (--) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[    26.386] (--) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[    26.386] (--) ImExPS/2 Generic Explorer Mouse: Found relative axes
[    26.386] (--) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[    26.386] (II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[    26.386] (II) ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[    26.386] (**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[    26.386] (**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.386] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    26.386] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
[    26.386] (II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[    26.386] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[    26.386] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[    26.386] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[    26.386] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[    26.387] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[    26.387] (II) No input driver/identifier specified (ignoring)


---

### Post by mc4man on 2011-05-03
Mia - unfortunately  your video card and driver -
> Driver 173.14.30
NVIDIA GPU GeForce FX 5500 (NV34)

probalby are inc. in ones that atm can't properly run unity, either w/ nvidia or nouveau 3d drivers
This post has some links to current bugs - the first 2 most likely relate to you
[http://ubuntuforums.org/showthread.php?p=10761117#post10761117](http://ubuntuforums.org/showthread.php?p=10761117#post10761117)

---

### Post by zizban on 2011-05-03
I have a laptop with one of these and it didn't run. I decided to try out Unity 2D and I must say, it's not bad. Compared to Unity it's a little flat but still pretty nice.

---

### Post by Mia1990 on 2011-05-03
Thank you mc4man i was kind of thinking that way too after a lot of google searches i just can't  see how  /usr/lib/nux/unity_support_test -p said it supported unity.The odd thing was that my nvidia driver in additional drivers said this driver is activated  but not currently in use i was thinking the two problems were the same and they may be i don't know how to get around that.Compiz still works i just have to start compiz from the terminal each time i boot and again i don't know how to get around that.

---

### Post by Mia1990 on 2011-05-03
> **zizban said:**
> I have a laptop with one of these and it didn't run. I decided to try out Unity 2D and I must say, it's not bad. Compared to Unity it's a little flat but still pretty nice.
  Could you explain what your talking about when you say compared to Unity it's a little flatt

---

