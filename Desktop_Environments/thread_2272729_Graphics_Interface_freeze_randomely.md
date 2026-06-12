---
title: "Graphics Interface freeze randomely"
date: 2015-04-08
forum: Desktop Environments
---

### Post by damjuve on 2015-04-08
Hi,

I have some probleme with the graphic interface of ubuntu.

Randomely (sometimes every 5 minutes, sometimes once a day), my graphic interface freeze. The computer is still running and nothing goes wrong, just i can't see anything moving anymore. I have to switch to tty1 (ctrl + alt + f1) then go back to tty7 and then the screen is unfreeze.

This is a minor problème but very anoying when its happen every 5 minutes, this is why i am looking for any solution.

I use Ubuntu 14.04 LTS on an Acer Aspire V3 771G with an NVIDIA GeForce GT 740M.

And this post is a copy of [a post on a french forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=1749371") where nobody could help me.

I give you some information :
file /etc/X11/xorg.conf :
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection
```

file /var/log/Xorg.0.log :
```
[    20.138] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    20.139] X Protocol Version 11, Revision 0
[    20.139] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    20.139] Current Operating System: Linux dewey-linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64
[    20.139] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=995b2cd0-0f16-4353-8a9d-d1f22d817419 ro quiet splash
[    20.139] Build Date: 30 July 2014  12:21:54AM
[    20.139] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    20.139] Current version of pixman: 0.30.2
[    20.139]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.139] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.139] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 20 14:21:56 2014
[    20.174] (==) Using config file: "/etc/X11/xorg.conf"
[    20.175] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.202] (==) ServerLayout "layout"
[    20.202] (**) |-->Screen "nvidia" (0)
[    20.202] (**) |   |-->Monitor "<default monitor>"
[    20.202] (**) |   |-->Device "nvidia"
[    20.202] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[    20.202] (**) |-->Inactive Device "intel"
[    20.202] (==) Automatically adding devices
[    20.202] (==) Automatically enabling devices
[    20.202] (==) Automatically adding GPU devices
[    20.202] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.202]     Entry deleted from font path.
[    20.202] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.202]     Entry deleted from font path.
[    20.202] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.202]     Entry deleted from font path.
[    20.202] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.202]     Entry deleted from font path.
[    20.202] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.202]     Entry deleted from font path.
[    20.202] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.202] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.202] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.203] (II) Loader magic: 0x7f5880d40d40
[    20.203] (II) Module ABI versions:
[    20.203]     X.Org ANSI C Emulation: 0.4
[    20.203]     X.Org Video Driver: 15.0
[    20.203]     X.Org XInput driver : 20.0
[    20.203]     X.Org Server Extension : 8.0
[    20.203] (II) xfree86: Adding drm device (/dev/dri/card1)
[    20.203] (II) xfree86: Adding drm device (/dev/dri/card0)
[    20.204] (--) PCI:*(0:0:2:0) 8086:0166:1025:0686 rev 9, Mem @ 0xd4000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    20.204] (--) PCI: (0:1:0:0) 10de:0fdf:1025:0686 rev 161, Mem @ 0xd2000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    20.204] Initializing built-in extension Generic Event Extension
[    20.204] Initializing built-in extension SHAPE
[    20.204] Initializing built-in extension MIT-SHM
[    20.204] Initializing built-in extension XInputExtension
[    20.204] Initializing built-in extension XTEST
[    20.204] Initializing built-in extension BIG-REQUESTS
[    20.204] Initializing built-in extension SYNC
[    20.204] Initializing built-in extension XKEYBOARD
[    20.204] Initializing built-in extension XC-MISC
[    20.204] Initializing built-in extension SECURITY
[    20.204] Initializing built-in extension XINERAMA
[    20.204] Initializing built-in extension XFIXES
[    20.204] Initializing built-in extension RENDER
[    20.204] Initializing built-in extension RANDR
[    20.204] Initializing built-in extension COMPOSITE
[    20.204] Initializing built-in extension DAMAGE
[    20.204] Initializing built-in extension MIT-SCREEN-SAVER
[    20.204] Initializing built-in extension DOUBLE-BUFFER
[    20.204] Initializing built-in extension RECORD
[    20.204] Initializing built-in extension DPMS
[    20.204] Initializing built-in extension Present
[    20.204] Initializing built-in extension DRI3
[    20.204] Initializing built-in extension X-Resource
[    20.204] Initializing built-in extension XVideo
[    20.204] Initializing built-in extension XVideo-MotionCompensation
[    20.204] Initializing built-in extension SELinux
[    20.204] Initializing built-in extension XFree86-VidModeExtension
[    20.204] Initializing built-in extension XFree86-DGA
[    20.204] Initializing built-in extension XFree86-DRI
[    20.204] Initializing built-in extension DRI2
[    20.204] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    20.204] (II) "glx" will be loaded by default.
[    20.204] (WW) "xmir" is not to be loaded by default. Skipping.
[    20.204] (II) LoadModule: "glx"
[    20.204] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    20.674] (II) Module glx: vendor="NVIDIA Corporation"
[    20.674]     compiled for 4.0.2, module version = 1.0.0
[    20.675]     Module class: X.Org Server Extension
[    20.675] (II) NVIDIA GLX Module  331.38  Wed Jan  8 19:10:17 PST 2014
[    20.675] Loading extension GLX
[    20.675] (II) LoadModule: "nvidia"
[    20.675] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    20.675] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.675]     compiled for 4.0.2, module version = 1.0.0
[    20.675]     Module class: X.Org Video Driver
[    20.675] (II) LoadModule: "intel"
[    20.687] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.707] (II) Module intel: vendor="X.Org Foundation"
[    20.707]     compiled for 1.15.1, module version = 2.99.910
[    20.707]     Module class: X.Org Video Driver
[    20.707]     ABI class: X.Org Video Driver, version 15.0
[    20.707] (II) NVIDIA dlloader X Driver  331.38  Wed Jan  8 18:51:00 PST 2014
[    20.707] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.707] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    20.707] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    20.707] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    20.707] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    20.707] (++) using VT number 7

[    20.707] (II) Loading sub module "fb"
[    20.707] (II) LoadModule: "fb"
[    20.707] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.707] (II) Module fb: vendor="X.Org Foundation"
[    20.707]     compiled for 1.15.1, module version = 1.0.0
[    20.707]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.707] (WW) Unresolved symbol: fbGetGCPrivateKey
[    20.707] (II) Loading sub module "wfb"
[    20.707] (II) LoadModule: "wfb"
[    20.707] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    20.707] (II) Module wfb: vendor="X.Org Foundation"
[    20.707]     compiled for 1.15.1, module version = 1.0.0
[    20.707]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.708] (II) Loading sub module "ramdac"
[    20.708] (II) LoadModule: "ramdac"
[    20.708] (II) Module "ramdac" already built-in
[    20.708] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.1 (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[    20.708] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[    20.708] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    20.708] (==) NVIDIA(0): RGB weight 888
[    20.708] (==) NVIDIA(0): Default visual is TrueColor
[    20.708] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.708] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    20.708] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    20.708] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    20.708] (**) NVIDIA(0): Enabling 2D acceleration
[    21.586] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[    21.586] (II) NVIDIA(0): NVIDIA GPU GeForce GT 740M (GK107) at PCI:1:0:0 (GPU-0)
[    21.586] (--) NVIDIA(0): Memory: 4194304 kBytes
[    21.586] (--) NVIDIA(0): VideoBIOS: 80.07.9a.00.43
[    21.586] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    21.586] (--) NVIDIA(0): Valid display device(s) on GeForce GT 740M at PCI:1:0:0
[    21.586] (--) NVIDIA(0):     none
[    21.586] (II) NVIDIA(0): Validated MetaModes:
[    21.587] (II) NVIDIA(0):     "NULL"
[    21.587] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    21.587] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    21.587] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    21.587] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    21.587] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    21.587] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    21.587] (==) intel(G0): RGB weight 888
[    21.587] (==) intel(G0): Default visual is TrueColor
[    21.587] (**) intel(G0): Option "AccelMethod" "SNA"
[    21.587] (**) intel(G0): Framebuffer tiled
[    21.587] (**) intel(G0): Pixmaps tiled
[    21.587] (**) intel(G0): "Tear free" disabled
[    21.587] (**) intel(G0): Forcing per-crtc-pixmaps? no
[    21.587] (II) intel(G0): Output LVDS1 has no monitor section
[    21.587] (--) intel(G0): found backlight control interface acpi_video1 (type 'firmware')
[    21.587] (II) intel(G0): Output VGA1 has no monitor section
[    21.587] (II) intel(G0): Output HDMI1 has no monitor section
[    21.587] (II) intel(G0): Output DP1 has no monitor section
[    21.587] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    21.587] (--) intel(G0): Output LVDS1 using initial mode 1920x1080 on pipe 0
[    21.587] (==) intel(G0): DPI set to (96, 96)
[    21.587] (II) Loading sub module "dri2"
[    21.587] (II) LoadModule: "dri2"
[    21.587] (II) Module "dri2" already built-in
[    21.587] (--) Depth 24 pixmap format is 32 bpp
[    21.587] (II) intel(G0): SNA initialized with Ivybridge (gen7, gt2) backend
[    21.587] (==) intel(G0): Backing store enabled
[    21.587] (==) intel(G0): Silken mouse enabled
[    21.587] (II) intel(G0): HW Cursor enabled
[    21.587] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.588] (==) intel(G0): DPMS enabled
[    21.588] (II) intel(G0): [DRI2] Setup complete
[    21.588] (II) intel(G0): [DRI2]   DRI driver: i965
[    21.588] (II) intel(G0): [DRI2]   VDPAU driver: i965
[    21.588] (II) intel(G0): direct rendering: DRI2 Enabled
[    21.588] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[    21.588] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[    21.588] (==) intel(G0): hotplug detection: "enabled"
[    21.588] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    21.588] (II) NVIDIA:     access.
[    21.590] (II) NVIDIA(0): Setting mode "NULL"
[    21.590] (EE) NVIDIA(0): Failed to initiate mode change.
[    21.590] (EE) NVIDIA(0): Failed to complete mode change
[    21.598] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    21.598] Loading extension NV-GLX
[    21.601] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.601] (==) NVIDIA(0): Backing store enabled
[    21.601] (==) NVIDIA(0): Silken mouse enabled
[    21.601] (==) NVIDIA(0): DPMS enabled
[    21.601] Loading extension NV-CONTROL
[    21.601] (II) Loading sub module "dri2"
[    21.601] (II) LoadModule: "dri2"
[    21.601] (II) Module "dri2" already built-in
[    21.601] (II) NVIDIA(0): [DRI2] Setup complete
[    21.601] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    21.601] (--) RandR disabled
[    21.605] (II) SELinux: Disabled on system
[    21.605] (II) Initializing extension GLX
[    21.607] (II) intel(G0): switch to mode 1920x1080@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    21.620] (II) intel(G0): Setting screen physical size to 508 x 285
[    21.629] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.631] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    21.631] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.631] (II) LoadModule: "evdev"
[    21.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.678] (II) Module evdev: vendor="X.Org Foundation"
[    21.678]     compiled for 1.15.0, module version = 2.8.2
[    21.678]     Module class: X.Org XInput Driver
[    21.678]     ABI class: X.Org XInput driver, version 20.0
[    21.678] (II) Using input driver 'evdev' for 'Power Button'
[    21.678] (**) Power Button: always reports core events
[    21.678] (**) evdev: Power Button: Device: "/dev/input/event3"
[    21.678] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.678] (--) evdev: Power Button: Found keys
[    21.678] (II) evdev: Power Button: Configuring as keyboard
[    21.678] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    21.678] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.678] (**) Option "xkb_rules" "evdev"
[    21.678] (**) Option "xkb_model" "pc105"
[    21.678] (**) Option "xkb_layout" "fr"
[    21.679] (**) Option "xkb_variant" "oss"
[    21.680] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[    21.681] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    21.681] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.681] (II) Using input driver 'evdev' for 'Video Bus'
[    21.681] (**) Video Bus: always reports core events
[    21.681] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    21.681] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.681] (--) evdev: Video Bus: Found keys
[    21.681] (II) evdev: Video Bus: Configuring as keyboard
[    21.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input11/event10"
[    21.681] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    21.681] (**) Option "xkb_rules" "evdev"
[    21.681] (**) Option "xkb_model" "pc105"
[    21.681] (**) Option "xkb_layout" "fr"
[    21.681] (**) Option "xkb_variant" "oss"
[    21.681] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.681] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.681] (II) Using input driver 'evdev' for 'Power Button'
[    21.681] (**) Power Button: always reports core events
[    21.681] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.681] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.681] (--) evdev: Power Button: Found keys
[    21.681] (II) evdev: Power Button: Configuring as keyboard
[    21.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0C:00/input/input0/event0"
[    21.682] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    21.682] (**) Option "xkb_rules" "evdev"
[    21.682] (**) Option "xkb_model" "pc105"
[    21.682] (**) Option "xkb_layout" "fr"
[    21.682] (**) Option "xkb_variant" "oss"
[    21.682] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    21.682] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.682] (II) Using input driver 'evdev' for 'Sleep Button'
[    21.682] (**) Sleep Button: always reports core events
[    21.682] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    21.682] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    21.682] (--) evdev: Sleep Button: Found keys
[    21.682] (II) evdev: Sleep Button: Configuring as keyboard
[    21.682] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0E:00/input/input1/event1"
[    21.682] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    21.682] (**) Option "xkb_rules" "evdev"
[    21.682] (**) Option "xkb_model" "pc105"
[    21.682] (**) Option "xkb_layout" "fr"
[    21.682] (**) Option "xkb_variant" "oss"
[    21.682] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    21.682] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.682] (II) Using input driver 'evdev' for 'Video Bus'
[    21.682] (**) Video Bus: always reports core events
[    21.682] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    21.682] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.682] (--) evdev: Video Bus: Found keys
[    21.682] (II) evdev: Video Bus: Configuring as keyboard
[    21.682] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:37/LNXVIDEO:00/input/input10/event9"
[    21.682] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    21.682] (**) Option "xkb_rules" "evdev"
[    21.682] (**) Option "xkb_model" "pc105"
[    21.682] (**) Option "xkb_layout" "fr"
[    21.682] (**) Option "xkb_variant" "oss"
[    21.683] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    21.683] (II) No input driver specified, ignoring this device.
[    21.683] (II) This device may have been added with another device file.
[    21.683] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card1
[    21.683] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    21.683] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    21.683] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    21.683] (II) config/udev: Adding input device HD WebCam (/dev/input/event6)
[    21.683] (**) HD WebCam: Applying InputClass "evdev keyboard catchall"
[    21.683] (II) Using input driver 'evdev' for 'HD WebCam'
[    21.683] (**) HD WebCam: always reports core events
[    21.683] (**) evdev: HD WebCam: Device: "/dev/input/event6"
[    21.683] (--) evdev: HD WebCam: Vendor 0x1bcf Product 0x2c18
[    21.683] (--) evdev: HD WebCam: Found keys
[    21.683] (II) evdev: HD WebCam: Configuring as keyboard
[    21.683] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7/event6"
[    21.683] (II) XINPUT: Adding extended input device "HD WebCam" (type: KEYBOARD, id 11)
[    21.683] (**) Option "xkb_rules" "evdev"
[    21.683] (**) Option "xkb_model" "pc105"
[    21.683] (**) Option "xkb_layout" "fr"
[    21.683] (**) Option "xkb_variant" "oss"
[    21.683] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[    21.683] (II) No input driver specified, ignoring this device.
[    21.683] (II) This device may have been added with another device file.
[    21.683] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    21.683] (II) No input driver specified, ignoring this device.
[    21.683] (II) This device may have been added with another device file.
[    21.684] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[    21.684] (II) No input driver specified, ignoring this device.
[    21.684] (II) This device may have been added with another device file.
[    21.684] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    21.684] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.684] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.684] (**) AT Translated Set 2 keyboard: always reports core events
[    21.684] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    21.684] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    21.684] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    21.684] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    21.684] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    21.684] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    21.684] (**) Option "xkb_rules" "evdev"
[    21.684] (**) Option "xkb_model" "pc105"
[    21.684] (**) Option "xkb_layout" "fr"
[    21.684] (**) Option "xkb_variant" "oss"
[    21.684] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event5)
[    21.684] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    21.684] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    21.684] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    21.684] (II) LoadModule: "synaptics"
[    21.684] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.684] (II) Module synaptics: vendor="X.Org Foundation"
[    21.684]     compiled for 1.15.0, module version = 1.7.4
[    21.684]     Module class: X.Org XInput Driver
[    21.684]     ABI class: X.Org XInput driver, version 20.0
[    21.684] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    21.684] (**) ETPS/2 Elantech Touchpad: always reports core events
[    21.684] (**) Option "Device" "/dev/input/event5"
[    21.704] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2964 (res 0)
[    21.704] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1560 (res 0)
[    21.704] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    21.704] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    21.704] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    21.704] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    21.704] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    21.704] (**) ETPS/2 Elantech Touchpad: always reports core events
[    21.720] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
[    21.720] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[    21.720] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    21.720] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    21.720] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.060
[    21.720] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    21.720] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    21.720] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    21.720] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    21.720] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    21.720] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    21.720] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    21.721] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event7)
[    21.721] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    21.722] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    21.722] (**) Acer WMI hotkeys: always reports core events
[    21.722] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event7"
[    21.722] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    21.722] (--) evdev: Acer WMI hotkeys: Found keys
[    21.722] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    21.722] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[    21.722] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 14)
[    21.722] (**) Option "xkb_rules" "evdev"
[    21.722] (**) Option "xkb_model" "pc105"
[    21.722] (**) Option "xkb_layout" "fr"
[    21.722] (**) Option "xkb_variant" "oss"
[    21.722] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event8)
[    21.722] (II) No input driver specified, ignoring this device.
[    21.722] (II) This device may have been added with another device file.
[    21.722] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    21.722] (II) No input driver specified, ignoring this device.
[    21.722] (II) This device may have been added with another device file.
[    21.761] (II) intel(G0): EDID vendor "CMO", prod id 5920
[    21.761] (II) intel(G0): Printing DDC gathered Modelines:
[    21.761] (II) intel(G0): Modeline "1920x1080"x0.0  140.49  1920 1972 2007 2094  1080 1083 1089 1118 +hsync -vsync (67.1 kHz eP)
[    21.761] (II) intel(G0): Modeline "1920x1080"x0.0   92.45  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (44.4 kHz e)
[    21.762] reporting 4 5 17 141
[    21.779] reporting 4 5 17 141
[    21.782] reporting 4 5 17 141
[    21.782] have a master to look out for
[    21.782] need to create shared pixmap 1reporting 4 5 17 141
[    22.106] have a master to look out for
[    22.106] adjust shatters 0 1920
[    22.109] need to create shared pixmap 1(II) intel(G0): switch to mode 1920x1080@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    23.048] reporting 4 5 17 141
[    23.976] reporting 4 5 17 141
[    24.178] reporting 4 5 17 141
[    24.614] reporting 4 5 17 141
[    25.126] reporting 4 5 17 141
[    25.129] reporting 4 5 17 141
[    25.195] reporting 4 5 17 141
[    25.195] reporting 4 5 17 141
[    25.280] reporting 4 5 17 141
[    25.318] reporting 4 5 17 141
[    25.319] reporting 4 5 17 141
[    25.621] reporting 4 5 17 141
[    27.083] reporting 4 5 17 141
[    50.297] reporting 4 5 17 141
[    50.297] reporting 4 5 17 141
[    50.313] reporting 4 5 17 141
[    50.314] reporting 4 5 17 141
[    50.320] reporting 4 5 17 141
[    50.340] reporting 4 5 17 141
[    50.342] reporting 4 5 17 141
[    50.356] reporting 4 5 17 141
[    50.426] reporting 4 5 17 141
[    50.454] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[    50.484] reporting 4 5 17 141
[    50.506] reporting 4 5 17 141
[    50.521] reporting 4 5 17 141
[    50.534] reporting 4 5 17 141
[    50.932] reporting 4 5 17 141
[    50.972] reporting 4 5 17 141
[    51.076] reporting 4 5 17 141
[    51.078] reporting 4 5 17 141
[    51.096] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[    51.104] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[    51.135] reporting 4 5 17 141
[    51.200] reporting 4 5 17 141
[    52.147] reporting 4 5 17 141
[    53.164] reporting 4 5 17 141
[    57.868] reporting 4 5 17 141
[    57.879] reporting 4 5 17 141
[    58.843] (II) XKB: reuse xkmfile /var/lib/xkb/server-1580E94F9C282AE2A0B7C28D11147BD2670E600F.xkm
[    64.322] reporting 4 5 17 141
[    66.649] reporting 4 5 17 141
[    66.828] reporting 4 5 17 141
[    67.767] reporting 4 5 17 141
[    67.783] reporting 4 5 17 141
[    73.697] reporting 4 5 17 141
[   105.469] (II) NVIDIA(0): Setting mode "NULL"
[   105.470] (EE) NVIDIA(0): Failed to initiate mode change.
[   105.470] (EE) NVIDIA(0): Failed to complete mode change
[   105.487] (II) intel(G0): switch to mode 1920x1080@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   105.514] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   105.546] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   105.558] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   105.567] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   105.584] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   105.599] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   105.610] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   105.624] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   105.648] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   111.619] reporting 4 5 17 141
[   116.185] reporting 4 5 17 141
[   671.600] (II) NVIDIA(0): Setting mode "NULL"
[   671.601] (EE) NVIDIA(0): Failed to initiate mode change.
[   671.601] (EE) NVIDIA(0): Failed to complete mode change
[   671.622] (II) intel(G0): switch to mode 1920x1080@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   671.661] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   671.750] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   671.765] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   671.785] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   671.801] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   671.818] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   671.833] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   671.852] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   671.878] (II) XKB: reuse xkmfile /var/lib/xkb/server-79DA8A0BAEB4CF1B2497C5C301111BA2CA0B8D85.xkm
[   897.121] reporting 4 5 17 141
```

If you need any other command i will get you.


Ps : Sorry if my post isn't in the right place but this is my first post in this forum.

---

### Post by dino99 on 2015-04-08
you should no more use an xorg.conf as now the kernel deals directly with X. Rename or delete it, your issue looks to be related with that xorg.conf. Then log out/in or better reboot

---

### Post by bernhard-kettner on 2015-07-20
I HAVE INSTALLED UBUNTU 14.04 ON acer aspire x3900 8 gb ram and graphic nvidia gt-215 on AN EMPTY HDD COMPLETELY NEW.
The installation completes fine , but I got freeze situation app. 30 - 45 min. Of operation, mouse jumps one time and freeze completly. As I investigated in der Internet I found some reports with Graphic card Nvidia trouble with new nouveau driver, so I decided to install Nvidia 305 proprietary driver from ubuntu repository and the trouble was gone. NOW THE SYSTEM RUNS WITHOUT ANY FREEZE SITUATION. But I am now thinking to exchange graphics card to Ati one to get rid of all the trouble. HOPEFULLY THAT WILL SOLVE THE ISSUE FOR EVER.

---

