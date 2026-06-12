---
title: "Any required tweaks specific to WINE when switching from Ubuntu to Xubuntu?"
date: 2011-05-07
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-05-07
On my initial move from Ubuntu to Xubuntu my FPS dropped from around 36 to 4.

Recommendations from WINE were to make sure I was using proprietary drivers, and that any desktop affects like compiz fusion were disabled.

Opening *Menu > System > Additional Drivers* revealed the following:

[IMG]http://oi56.tinypic.com/345hh91.jpg[/IMG]

Querying this in #xubuntu on Freenode I learned that there is a known bug that drivers will be in use although this applet may report otherwise.

On activating the other driver, reactivating the original 'current version', and rebooting, lspci -k outputs:

```
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Dell Device 01dd
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
    Subsystem: Dell Device 0405
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidia-173, nouveau, nvidiafb
```FPS is now up around 28/29 but does still seem a bit slower than normal when using Ubuntu/Ubuntu-classic, is there anything else I can do, and can anyone confirm that there are in fact no desktop affects or anything like compiz fusion one should disable in Xubuntu to improve performance when using the WINE layer?

Wine support have told me I am using proprietary and FOSS drivers, namely I need to stop using and remove nouveau.

Used synaptic to uninstall  xserver-xorg-video-nouveau, should I also remove libdrm-nouveau1a?  Synaptic is tell me doing so will affect hundreds of other packages.  There is no single 'nouveau' package, sudo apt-get remove nouveau does  nothing. 
 
lspci -k still showing nouveau 
 
The contents of my xorg.conf: 

```
Section "Screen" 
   Identifier   "Default Screen" 
   DefaultDepth   24 
EndSection 
 
Section "Module" 
   Load   "glx" 
EndSection 
 
Section "Device" 
   Identifier   "Default Device" 
   Driver   "nvidia" 
   Option   "NoLogo"   "True" 
EndSection 
```

/var/log/Xorg.0.log: 

```
[    22.519]  
X.Org X Server 1.10.1 
Release Date: 2011-04-15 
[    22.519] X Protocol Version 11, Revision 0 
[    22.519] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu 
[    22.519] Current Operating System: Linux skyrocket 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 
[    22.519] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic  root=UUID=ef405805-13f0-47e9-b625-ce8155ea3e4d ro quiet splash  vt.handoff=7 
[    22.519] Build Date: 19 April 2011  03:33:17PM 
[    22.519] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support)  
[    22.519] Current version of pixman: 0.20.2 
[    22.519]    Before reporting problems, check http://wiki.x.org 
   to make sure that you have the latest version. 
[    22.519] Markers: (--) probed, (**) from config file, (==) default setting, 
   (++) from command line, (!!) notice, (II) informational, 
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
[    22.519] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May  8 02:51:41 2011 
[    22.519] (==) Using config file: "/etc/X11/xorg.conf" 
[    22.519] (==) Using system config directory "/usr/share/X11/xorg.conf.d" 
[    22.520] (==) No Layout section.  Using the first Screen section. 
[    22.520] (**) |-->Screen "Default Screen" (0) 
[    22.520] (**) |   |-->Monitor "<default monitor>" 
[    22.520] (==) No device specified for screen "Default Screen". 
   Using the first device section listed. 
[    22.520] (**) |   |-->Device "Default Device" 
[    22.520] (==) No monitor specified for screen "Default Screen". 
   Using a default monitor configuration. 
[    22.520] (==) Automatically adding devices 
[    22.520] (==) Automatically enabling devices 
[    22.520] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. 
[    22.520]    Entry deleted from font path. 
[    22.520] (==) FontPath set to: 
   /usr/share/fonts/X11/misc, 
   /usr/share/fonts/X11/100dpi/:unscaled, 
   /usr/share/fonts/X11/75dpi/:unscaled, 
   /usr/share/fonts/X11/Type1, 
   /usr/share/fonts/X11/100dpi, 
   /usr/share/fonts/X11/75dpi, 
   /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, 
   built-ins 
[    22.520] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules" 
[    22.520] (II) The server relies on udev to provide the list of input devices. 
   If no devices become available, reconfigure udev or disable AutoAddDevices. 
[    22.520] (II) Loader magic: 0x81ffde0 
[    22.520] (II) Module ABI versions: 
[    22.520]    X.Org ANSI C Emulation: 0.4 
[    22.520]    X.Org Video Driver: 10.0 
[    22.520]    X.Org XInput driver : 12.3 
[    22.520]    X.Org Server Extension : 5.0 
[    22.521] (--) PCI:*(0:1:0:0) 10de:01d1:1028:0405 rev 161, Mem @  0xdd000000/16777216, 0xc0000000/268435456, 0xde000000/16777216, BIOS @  0x????????/131072 
[    22.521] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory) 
[    22.521] (II) "extmod" will be loaded by default. 
[    22.521] (II) "dbe" will be loaded by default. 
[    22.521] (II) "glx" will be loaded. This was enabled by default and also specified in the config file. 
[    22.521] (II) "record" will be loaded by default. 
[    22.521] (II) "dri" will be loaded by default. 
[    22.521] (II) "dri2" will be loaded by default. 
[    22.521] (II) LoadModule: "glx" 
[    22.522] (II) Loading /usr/lib/xorg/extra-modules/libglx.so 
[    22.555] (II) Module glx: vendor="NVIDIA Corporation" 
[    22.555]    compiled for 4.0.2, module version = 1.0.0 
[    22.555]    Module class: X.Org Server Extension 
[    22.555] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011 
[    22.555] (II) Loading extension GLX 
[    22.555] (II) LoadModule: "extmod" 
[    22.555] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so 
[    22.555] (II) Module extmod: vendor="X.Org Foundation" 
[    22.555]    compiled for 1.10.1, module version = 1.0.0 
[    22.555]    Module class: X.Org Server Extension 
[    22.555]    ABI class: X.Org Server Extension, version 5.0 
[    22.555] (II) Loading extension MIT-SCREEN-SAVER 
[    22.556] (II) Loading extension XFree86-VidModeExtension 
[    22.556] (II) Loading extension XFree86-DGA 
[    22.556] (II) Loading extension DPMS 
[    22.556] (II) Loading extension XVideo 
[    22.556] (II) Loading extension XVideo-MotionCompensation 
[    22.556] (II) Loading extension X-Resource 
[    22.556] (II) LoadModule: "dbe" 
[    22.556] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so 
[    22.556] (II) Module dbe: vendor="X.Org Foundation" 
[    22.556]    compiled for 1.10.1, module version = 1.0.0 
[    22.556]    Module class: X.Org Server Extension 
[    22.556]    ABI class: X.Org Server Extension, version 5.0 
[    22.556] (II) Loading extension DOUBLE-BUFFER 
[    22.556] (II) LoadModule: "record" 
[    22.556] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so 
[    22.556] (II) Module record: vendor="X.Org Foundation" 
[    22.556]    compiled for 1.10.1, module version = 1.13.0 
[    22.556]    Module class: X.Org Server Extension 
[    22.556]    ABI class: X.Org Server Extension, version 5.0 
[    22.556] (II) Loading extension RECORD 
[    22.556] (II) LoadModule: "dri" 
[    22.557] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so 
[    22.557] (II) Module dri: vendor="X.Org Foundation" 
[    22.557]    compiled for 1.10.1, module version = 1.0.0 
[    22.557]    ABI class: X.Org Server Extension, version 5.0 
[    22.557] (II) Loading extension XFree86-DRI 
[    22.557] (II) LoadModule: "dri2" 
[    22.557] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so 
[    22.557] (II) Module dri2: vendor="X.Org Foundation" 
[    22.557]    compiled for 1.10.1, module version = 1.2.0 
[    22.557]    ABI class: X.Org Server Extension, version 5.0 
[    22.557] (II) Loading extension DRI2 
[    22.557] (II) LoadModule: "nvidia" 
[    22.557] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so 
[    22.558] (II) Module nvidia: vendor="NVIDIA Corporation" 
[    22.558]    compiled for 4.0.2, module version = 1.0.0 
[    22.558]    Module class: X.Org Video Driver 
[    22.558] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:51 PDT 2011 
[    22.558] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs 
[    22.558] (++) using VT number 7 
 
[    22.558] (II) Loading sub module "fb" 
[    22.558] (II) LoadModule: "fb" 
[    22.568] (II) Loading /usr/lib/xorg/modules/libfb.so 
[    22.568] (II) Module fb: vendor="X.Org Foundation" 
[    22.568]    compiled for 1.10.1, module version = 1.0.0 
[    22.568]    ABI class: X.Org ANSI C Emulation, version 0.4 
[    22.568] (II) Loading sub module "wfb" 
[    22.568] (II) LoadModule: "wfb" 
[    22.569] (II) Loading /usr/lib/xorg/modules/libwfb.so 
[    22.569] (II) Module wfb: vendor="X.Org Foundation" 
[    22.569]    compiled for 1.10.1, module version = 1.0.0 
[    22.569]    ABI class: X.Org ANSI C Emulation, version 0.4 
[    22.569] (II) Loading sub module "ramdac" 
[    22.569] (II) LoadModule: "ramdac" 
[    22.569] (II) Module "ramdac" already built-in 
[    22.569] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so 
[    22.569] (II) Loading /usr/lib/xorg/modules/libwfb.so 
[    22.569] (II) Loading /usr/lib/xorg/modules/libfb.so 
[    22.569] (II) NVIDIA(0): Creating default Display subsection in Screen section 
   "Default Screen" for depth/fbbpp 24/32 
[    22.569] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32 
[    22.569] (==) NVIDIA(0): RGB weight 888 
[    22.569] (==) NVIDIA(0): Default visual is TrueColor 
[    22.569] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0) 
[    22.569] (**) NVIDIA(0): Option "NoLogo" "True" 
[    23.682] (II) NVIDIA(GPU-0): Display (DELL SE197FP (CRT-0)) does not support NVIDIA 3D 
[    23.682] (II) NVIDIA(GPU-0):     Vision stereo. 
[    23.684] (II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE (G72) at PCI:1:0:0 (GPU-0) 
[    23.684] (--) NVIDIA(0): Memory: 524288 kBytes 
[    23.684] (--) NVIDIA(0): VideoBIOS: 05.72.22.49.09 
[    23.684] (II) NVIDIA(0): Detected PCI Express Link width: 16X 
[    23.684] (--) NVIDIA(0): Interlaced video modes are supported on this GPU 
[    23.684] (--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0 
[    23.684] (--) NVIDIA(0):     DELL SE197FP (CRT-0) 
[    23.684] (--) NVIDIA(0): DELL SE197FP (CRT-0): 400.0 MHz maximum pixel clock 
[    23.684] (II) NVIDIA(0): Assigned Display Device: CRT-0 
[    23.684] (==) NVIDIA(0):  
[    23.684] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select" 
[    23.685] (==) NVIDIA(0):     will be used as the requested mode. 
[    23.685] (==) NVIDIA(0):  
[    23.685] (II) NVIDIA(0): Validated modes: 
[    23.685] (II) NVIDIA(0):     "nvidia-auto-select" 
[    23.685] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024 
[    23.686] (--) NVIDIA(0): DPI set to (85, 83); computed from "UseEdidDpi" X config 
[    23.686] (--) NVIDIA(0):     option 
[    23.686] (--) Depth 24 pixmap format is 32 bpp 
[    23.691] (II) NVIDIA(0): Setting mode "nvidia-auto-select" 
[    23.757] (II) Loading extension NV-GLX 
[    23.792] (==) NVIDIA(0): Disabling shared memory pixmaps 
[    23.792] (==) NVIDIA(0): Backing store disabled 
[    23.792] (==) NVIDIA(0): Silken mouse enabled 
[    23.792] (==) NVIDIA(0): DPMS enabled 
[    23.793] (II) Loading extension NV-CONTROL 
[    23.793] (II) Loading extension XINERAMA 
[    23.793] (II) Loading sub module "dri2" 
[    23.793] (II) LoadModule: "dri2" 
[    23.793] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so 
[    23.793] (II) Module dri2: vendor="X.Org Foundation" 
[    23.793]    compiled for 1.10.1, module version = 1.2.0 
[    23.793]    ABI class: X.Org Server Extension, version 5.0 
[    23.793] (II) NVIDIA(0): [DRI2] Setup complete 
[    23.793] (==) RandR enabled 
[    23.793] (II) Initializing built-in extension Generic Event Extension 
[    23.793] (II) Initializing built-in extension SHAPE 
[    23.794] (II) Initializing built-in extension MIT-SHM 
[    23.794] (II) Initializing built-in extension XInputExtension 
[    23.794] (II) Initializing built-in extension XTEST 
[    23.794] (II) Initializing built-in extension BIG-REQUESTS 
[    23.794] (II) Initializing built-in extension SYNC 
[    23.794] (II) Initializing built-in extension XKEYBOARD 
[    23.794] (II) Initializing built-in extension XC-MISC 
[    23.794] (II) Initializing built-in extension SECURITY 
[    23.794] (II) Initializing built-in extension XINERAMA 
[    23.794] (II) Initializing built-in extension XFIXES 
[    23.794] (II) Initializing built-in extension RENDER 
[    23.794] (II) Initializing built-in extension RANDR 
[    23.794] (II) Initializing built-in extension COMPOSITE 
[    23.794] (II) Initializing built-in extension DAMAGE 
[    23.794] (II) Initializing built-in extension GESTURE 
[    23.794] (II) Initializing extension GLX 
[    23.840] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm 
[    23.854] (II) config/udev: Adding input device Power Button (/dev/input/event1) 
[    23.854] (**) Power Button: Applying InputClass "evdev keyboard catchall" 
[    23.854] (II) LoadModule: "evdev" 
[    23.855] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[    23.855] (II) Module evdev: vendor="X.Org Foundation" 
[    23.855]    compiled for 1.10.0.902, module version = 2.6.0 
[    23.855]    Module class: X.Org XInput Driver 
[    23.855]    ABI class: X.Org XInput driver, version 12.3 
[    23.855] (II) Using input driver 'evdev' for 'Power Button' 
[    23.855] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[    23.855] (**) Power Button: always reports core events 
[    23.856] (**) Power Button: Device: "/dev/input/event1" 
[    23.856] (--) Power Button: Found keys 
[    23.856] (II) Power Button: Configuring as keyboard 
[    23.856] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1" 
[    23.856] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD) 
[    23.856] (**) Option "xkb_rules" "evdev" 
[    23.856] (**) Option "xkb_model" "pc105" 
[    23.856] (**) Option "xkb_layout" "ie" 
[    23.859] (II) XKB: reuse xkmfile /var/lib/xkb/server-D63B65A598D87ADD63BB2A7251A4C90D6C2F46D8.xkm 
[    23.862] (II) config/udev: Adding input device Power Button (/dev/input/event0) 
[    23.862] (**) Power Button: Applying InputClass "evdev keyboard catchall" 
[    23.862] (II) Using input driver 'evdev' for 'Power Button' 
[    23.862] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[    23.862] (**) Power Button: always reports core events 
[    23.862] (**) Power Button: Device: "/dev/input/event0" 
[    23.862] (--) Power Button: Found keys 
[    23.862] (II) Power Button: Configuring as keyboard 
[    23.862] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0" 
[    23.862] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD) 
[    23.862] (**) Option "xkb_rules" "evdev" 
[    23.862] (**) Option "xkb_model" "pc105" 
[    23.862] (**) Option "xkb_layout" "ie" 
[    23.866] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event10) 
[    23.866] (II) No input driver/identifier specified (ignoring) 
[    23.867] (II) config/udev: Adding input device HDA Intel Line In at Ext Rear Jack (/dev/input/event3) 
[    23.867] (II) No input driver/identifier specified (ignoring) 
[    23.867] (II) config/udev: Adding input device HDA Intel Mic at Ext Rear Jack (/dev/input/event4) 
[    23.867] (II) No input driver/identifier specified (ignoring) 
[    23.868] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event5) 
[    23.868] (II) No input driver/identifier specified (ignoring) 
[    23.868] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event6) 
[    23.868] (II) No input driver/identifier specified (ignoring) 
[    23.868] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event7) 
[    23.868] (II) No input driver/identifier specified (ignoring) 
[    23.869] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event8) 
[    23.869] (II) No input driver/identifier specified (ignoring) 
[    23.869] (II) config/udev: Adding input device HDA Intel Speaker at Ext Rear Jack (/dev/input/event9) 
[    23.869] (II) No input driver/identifier specified (ignoring) 
[    23.871] (II) config/udev: Adding input device USB Optical Mouse USB Optical Mouse (/dev/input/event13) 
[    23.871] (**) USB Optical Mouse USB Optical Mouse: Applying InputClass "evdev pointer catchall" 
[    23.871] (II) Using input driver 'evdev' for 'USB Optical Mouse USB Optical Mouse' 
[    23.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[    23.871] (**) USB Optical Mouse USB Optical Mouse: always reports core events 
[    23.871] (**) USB Optical Mouse USB Optical Mouse: Device: "/dev/input/event13" 
[    23.871] (--) USB Optical Mouse USB Optical Mouse: Found 10 mouse buttons 
[    23.871] (--) USB Optical Mouse USB Optical Mouse: Found scroll wheel(s) 
[    23.871] (--) USB Optical Mouse USB Optical Mouse: Found relative axes 
[    23.871] (--) USB Optical Mouse USB Optical Mouse: Found x and y relative axes 
[    23.871] (II) USB Optical Mouse USB Optical Mouse: Configuring as mouse 
[    23.871] (II) USB Optical Mouse USB Optical Mouse: Adding scrollwheel support 
[    23.871] (**) USB Optical Mouse USB Optical Mouse: YAxisMapping: buttons 4 and 5 
[    23.871] (**) USB Optical Mouse USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200 
[    23.871] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input13/event13" 
[    23.871] (II) XINPUT: Adding extended input device "USB Optical Mouse USB Optical Mouse" (type: MOUSE) 
[    23.871] (II) USB Optical Mouse USB Optical Mouse: initialized for relative axes. 
[    23.872] (**) USB Optical Mouse USB Optical Mouse: (accel) keeping acceleration scheme 1 
[    23.872] (**) USB Optical Mouse USB Optical Mouse: (accel) acceleration profile 0 
[    23.872] (**) USB Optical Mouse USB Optical Mouse: (accel) acceleration factor: 2.000 
[    23.872] (**) USB Optical Mouse USB Optical Mouse: (accel) acceleration threshold: 4 
[    23.872] (II) config/udev: Adding input device USB Optical Mouse USB Optical Mouse (/dev/input/mouse0) 
[    23.872] (II) No input driver/identifier specified (ignoring) 
[    23.873] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event11) 
[    23.873] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall" 
[    23.873] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard' 
[    23.873] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[    23.874] (**) Dell Dell USB Keyboard: always reports core events 
[    23.874] (**) Dell Dell USB Keyboard: Device: "/dev/input/event11" 
[    23.874] (--) Dell Dell USB Keyboard: Found keys 
[    23.874] (II) Dell Dell USB Keyboard: Configuring as keyboard 
[    23.874] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.1/7-1.1:1.0/input/input11/event11" 
[    23.874] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD) 
[    23.874] (**) Option "xkb_rules" "evdev" 
[    23.874] (**) Option "xkb_model" "pc105" 
[    23.874] (**) Option "xkb_layout" "ie" 
[    23.875] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event12) 
[    23.875] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall" 
[    23.875] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard' 
[    23.875] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[    23.875] (**) Dell Dell USB Keyboard: always reports core events 
[    23.875] (**) Dell Dell USB Keyboard: Device: "/dev/input/event12" 
[    23.875] (--) Dell Dell USB Keyboard: Found absolute axes 
[    23.875] (II) evdev-grail: failed to open grail, no gesture support 
[    23.875] (--) Dell Dell USB Keyboard: Found keys 
[    23.875] (II) Dell Dell USB Keyboard: Configuring as mouse 
[    23.875] (II) Dell Dell USB Keyboard: Configuring as keyboard 
[    23.875] (**) Option "config_info"  "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.1/7-1.1:1.1/input/input12/event12" 
[    23.875] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD) 
[    23.875] (**) Option "xkb_rules" "evdev" 
[    23.875] (**) Option "xkb_model" "pc105" 
[    23.875] (**) Option "xkb_layout" "ie" 
[    23.876] (II) Dell Dell USB Keyboard: initialized for absolute axes. 
[    23.876] (**) Dell Dell USB Keyboard: (accel) keeping acceleration scheme 1 
[    23.876] (**) Dell Dell USB Keyboard: (accel) acceleration profile 0 
[    23.876] (**) Dell Dell USB Keyboard: (accel) acceleration factor: 2.000 
[    23.876] (**) Dell Dell USB Keyboard: (accel) acceleration threshold: 4 
[    23.879] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event2) 
[    23.879] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall" 
[    23.879] (II) Using input driver 'evdev' for 'USB 2.0 Camera' 
[    23.879] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[    23.880] (**) USB 2.0 Camera: always reports core events 
[    23.880] (**) USB 2.0 Camera: Device: "/dev/input/event2" 
[    23.880] (--) USB 2.0 Camera: Found keys 
[    23.880] (II) USB 2.0 Camera: Configuring as keyboard 
[    23.880] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input2/event2" 
[    23.880] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD) 
[    23.880] (**) Option "xkb_rules" "evdev" 
[    23.880] (**) Option "xkb_model" "pc105" 
[    23.880] (**) Option "xkb_layout" "ie" 
[   176.210] (II) NVIDIA(0): Setting mode "1280x1024_75"
```

Menu >> System >> NVidia Server Settings brings up the options menu. 

So am I really using NVidia, and lspci -k showing  nouveau is just a symptom of the bug that shows that nvidia-current  is active but not in use in Menu >> System >> Additional Drivers? 

If not, please tell me how to remove nouveau?

---

### Post by peyre on 2011-05-07
I'm a Xubuntu user myself.  Unfortunately I don't have a solution for you, but I wanted to chime in and say that what you're experiencing isn't representative of how Xubuntu has worked for me.  I have various mounting issues in Xubuntu, but videos play fine.  -FWIW-

---

### Post by Dáire Fagan on 2011-05-08
> **peyre said:**
> I'm a Xubuntu user myself.  Unfortunately I don't have a solution for you, but I wanted to chime in and say that what you're experiencing isn't representative of how Xubuntu has worked for me.  I have various mounting issues in Xubuntu, but videos play fine.  -FWIW-

Thanks, maybe there's a bug switching from Ubuntu to Xubuntu.

Anybody else?

WINE support telling me now I need to blacklist noveau in the boot options, but I thought that was already the case.

---

