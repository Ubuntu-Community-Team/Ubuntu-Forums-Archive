---
title: "Problem with display (DVI)"
date: 2011-08-31
forum: Desktop Environments
---

### Post by bobl61 on 2011-08-31
I am running a dual boot system with Kubuntu 11.04 and Windows XP  Professional. I had been using the setup in VGA mode, but just purchased  a DVI cable. Windows had no problem recognizing the Digital Display,  but now when I try and boot Kubuntu, I am presented with a command  prompt environment. I've searched for a resolution to the problem, but  have not been able to obtain a solution. Any help appreciated  [IMG]http://kubuntuforums.net/forums/Smileys/classic/wink.gif[/IMG]

---

### Post by papibe on 2011-08-31
Welcome!

Try first deleting (actually renaming) your Xorg config file.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then reboot.

If that doesn't work, post here your Xorg log file right after a bad boot. It's this file:
```
/var/log/Xorg.0.log
```
When pasting it, please use # tags (CODE).

Regards.

---

### Post by bobl61 on 2011-08-31
Thanks for the quick reply. When I execute I got this error:
```
mv: cannot stat '/etc/x11/xorg.conf': No such file or directory
```

---

### Post by papibe on 2011-09-01
Posting your log may provide more information about the problem.

Regards.

---

### Post by bobl61 on 2011-09-02
Okay... found out that the folder is X11 (capital X) and I was able to rename the file to xorg.conf.old. However, that did not help. Here is the log file:

```
[    22.599] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    22.599] X Protocol Version 11, Revision 0
[    22.599] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    22.599] Current Operating System: Linux Biostar 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    22.599] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=bf4c8c86-7a51-461a-8347-a191737da4c2 ro vga=792 splash quiet splash vt.handoff=7
[    22.599] Build Date: 21 May 2011  11:38:35AM
[    22.599] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    22.599] Current version of pixman: 0.20.2
[    22.599]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.599] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.599] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 27 02:46:56 2011
[    22.600] (==) Using config file: "/etc/X11/xorg.conf"
[    22.600] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.600] (==) No Layout section.  Using the first Screen section.
[    22.600] (==) No screen section available. Using defaults.
[    22.600] (**) |-->Screen "Default Screen Section" (0)
[    22.600] (**) |   |-->Monitor "<default monitor>"
[    22.600] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    22.600] (**) |   |-->Device "Default Device"
[    22.600] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    22.600] (==) Automatically adding devices
[    22.600] (==) Automatically enabling devices
[    22.600] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.600]     Entry deleted from font path.
[    22.600] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.600]     Entry deleted from font path.
[    22.600] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.600]     Entry deleted from font path.
[    22.600] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    22.600] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.601] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.601] (II) Loader magic: 0x81ffde0
[    22.601] (II) Module ABI versions:
[    22.601]     X.Org ANSI C Emulation: 0.4
[    22.601]     X.Org Video Driver: 10.0
[    22.601]     X.Org XInput driver : 12.3
[    22.601]     X.Org Server Extension : 5.0
[    22.601] (--) PCI:*(0:0:13:0) 10de:03d0:1565:1405 rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
[    22.602] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.602] (II) LoadModule: "extmod"
[    22.602] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.603] (II) Module extmod: vendor="X.Org Foundation"
[    22.603]     compiled for 1.10.1, module version = 1.0.0
[    22.603]     Module class: X.Org Server Extension
[    22.603]     ABI class: X.Org Server Extension, version 5.0
[    22.603] (II) Loading extension MIT-SCREEN-SAVER
[    22.603] (II) Loading extension XFree86-VidModeExtension
[    22.603] (II) Loading extension XFree86-DGA
[    22.603] (II) Loading extension DPMS
[    22.603] (II) Loading extension XVideo
[    22.603] (II) Loading extension XVideo-MotionCompensation
[    22.603] (II) Loading extension X-Resource
[    22.603] (II) LoadModule: "dbe"
[    22.603] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.603] (II) Module dbe: vendor="X.Org Foundation"
[    22.603]     compiled for 1.10.1, module version = 1.0.0
[    22.603]     Module class: X.Org Server Extension
[    22.603]     ABI class: X.Org Server Extension, version 5.0
[    22.603] (II) Loading extension DOUBLE-BUFFER
[    22.603] (II) LoadModule: "glx"
[    22.603] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    22.637] (II) Module glx: vendor="NVIDIA Corporation"
[    22.638]     compiled for 4.0.2, module version = 1.0.0
[    22.638]     Module class: X.Org Server Extension
[    22.638] (II) NVIDIA GLX Module  275.19  Tue Jul 12 18:48:27 PDT 2011
[    22.638] (II) Loading extension GLX
[    22.638] (II) LoadModule: "record"
[    22.638] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.638] (II) Module record: vendor="X.Org Foundation"
[    22.638]     compiled for 1.10.1, module version = 1.13.0
[    22.638]     Module class: X.Org Server Extension
[    22.638]     ABI class: X.Org Server Extension, version 5.0
[    22.638] (II) Loading extension RECORD
[    22.638] (II) LoadModule: "dri"
[    22.639] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.639] (II) Module dri: vendor="X.Org Foundation"
[    22.639]     compiled for 1.10.1, module version = 1.0.0
[    22.639]     ABI class: X.Org Server Extension, version 5.0
[    22.639] (II) Loading extension XFree86-DRI
[    22.639] (II) LoadModule: "dri2"
[    22.639] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.639] (II) Module dri2: vendor="X.Org Foundation"
[    22.639]     compiled for 1.10.1, module version = 1.2.0
[    22.639]     ABI class: X.Org Server Extension, version 5.0
[    22.639] (II) Loading extension DRI2
[    22.639] (==) Matched nvidia as autoconfigured driver 0
[    22.639] (==) Matched nouveau as autoconfigured driver 1
[    22.639] (==) Matched nv as autoconfigured driver 2
[    22.639] (==) Matched vesa as autoconfigured driver 3
[    22.639] (==) Matched fbdev as autoconfigured driver 4
[    22.639] (==) Assigned the driver to the xf86ConfigLayout
[    22.639] (II) LoadModule: "nvidia"
[    22.639] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.640] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.640]     compiled for 4.0.2, module version = 1.0.0
[    22.640]     Module class: X.Org Video Driver
[    22.640] (II) LoadModule: "nouveau"
[    22.641] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.641] (II) Module nouveau: vendor="X.Org Foundation"
[    22.641]     compiled for 1.10.0, module version = 0.0.16
[    22.641]     Module class: X.Org Video Driver
[    22.641]     ABI class: X.Org Video Driver, version 10.0
[    22.641] (II) LoadModule: "nv"
[    22.670] (WW) Warning, couldn't open module nv
[    22.670] (II) UnloadModule: "nv"
[    22.670] (II) Unloading nv
[    22.670] (EE) Failed to load module "nv" (module does not exist, 0)
[    22.670] (II) LoadModule: "vesa"
[    22.670] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.670] (II) Module vesa: vendor="X.Org Foundation"
[    22.671]     compiled for 1.10.0, module version = 2.3.0
[    22.671]     Module class: X.Org Video Driver
[    22.671]     ABI class: X.Org Video Driver, version 10.0
[    22.671] (II) LoadModule: "fbdev"
[    22.671] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.671] (II) Module fbdev: vendor="X.Org Foundation"
[    22.671]     compiled for 1.10.0, module version = 0.4.2
[    22.671]     ABI class: X.Org Video Driver, version 10.0
[    22.671] (II) NVIDIA dlloader X Driver  275.19  Tue Jul 12 18:30:49 PDT 2011
[    22.671] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.671] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    22.671] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.671]     RIVA TNT    (NV04)
[    22.671]     RIVA TNT2   (NV05)
[    22.671]     GeForce 256 (NV10)
[    22.671]     GeForce 2   (NV11, NV15)
[    22.671]     GeForce 4MX (NV17, NV18)
[    22.671]     GeForce 3   (NV20)
[    22.671]     GeForce 4Ti (NV25, NV28)
[    22.671]     GeForce FX  (NV3x)
[    22.671]     GeForce 6   (NV4x)
[    22.671]     GeForce 7   (G7x)
[    22.671]     GeForce 8   (G8x)
[    22.671] (II) VESA: driver for VESA chipsets: vesa
[    22.671] (II) FBDEV: driver for framebuffer: fbdev
[    22.671] (++) using VT number 7

[    22.671] (II) Loading sub module "fb"
[    22.671] (II) LoadModule: "fb"
[    22.672] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.672] (II) Module fb: vendor="X.Org Foundation"
[    22.672]     compiled for 1.10.1, module version = 1.0.0
[    22.672]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.672] (II) Loading sub module "wfb"
[    22.672] (II) LoadModule: "wfb"
[    22.673] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.673] (II) Module wfb: vendor="X.Org Foundation"
[    22.673]     compiled for 1.10.1, module version = 1.0.0
[    22.673]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.673] (II) Loading sub module "ramdac"
[    22.673] (II) LoadModule: "ramdac"
[    22.673] (II) Module "ramdac" already built-in
[    22.673] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.673] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.673] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.673] (WW) Falling back to old probe method for vesa
[    22.673] (WW) Falling back to old probe method for fbdev
[    22.673] (II) Loading sub module "fbdevhw"
[    22.673] (II) LoadModule: "fbdevhw"
[    22.673] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.674] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.674]     compiled for 1.10.1, module version = 0.0.2
[    22.674]     ABI class: X.Org Video Driver, version 10.0
[    22.674] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.674] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    22.674] (==) NVIDIA(0): RGB weight 888
[    22.674] (==) NVIDIA(0): Default visual is TrueColor
[    22.674] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.674] (**) NVIDIA(0): Option "NoLogo" "True"
[    23.549] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    23.550] (II) NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
[    23.550] (II) NVIDIA(0):     (GPU-0)
[    23.550] (--) NVIDIA(0): Memory: 524288 kBytes
[    23.550] (--) NVIDIA(0): VideoBIOS: 05.61.32.22.01
[    23.550] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    23.550] (--) NVIDIA(0): Connected display device(s) on GeForce 6150SE nForce 430 at
[    23.550] (--) NVIDIA(0):     PCI:0:13:0
[    23.550] (--) NVIDIA(0):     CRT-0
[    23.550] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[    23.550] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    23.550] (==) NVIDIA(0): 
[    23.550] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    23.550] (==) NVIDIA(0):     will be used as the requested mode.
[    23.550] (==) NVIDIA(0): 
[    23.550] (II) NVIDIA(0): Validated modes:
[    23.550] (II) NVIDIA(0):     "nvidia-auto-select"
[    23.550] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    23.551] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    23.551] (WW) NVIDIA(0):     from CRT-0's EDID.
[    23.551] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    23.551] (II) UnloadModule: "nouveau"
[    23.551] (II) Unloading nouveau
[    23.551] (II) UnloadModule: "vesa"
[    23.551] (II) Unloading vesa
[    23.551] (II) UnloadModule: "fbdev"
[    23.551] (II) Unloading fbdev
[    23.551] (II) UnloadModule: "fbdevhw"
[    23.551] (II) Unloading fbdevhw
[    23.551] (--) Depth 24 pixmap format is 32 bpp
[    23.556] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    23.621] (II) Loading extension NV-GLX
[    23.650] (==) NVIDIA(0): Disabling shared memory pixmaps
[    23.650] (==) NVIDIA(0): Backing store disabled
[    23.650] (==) NVIDIA(0): Silken mouse enabled
[    23.650] (==) NVIDIA(0): DPMS enabled
[    23.651] (II) Loading extension NV-CONTROL
[    23.651] (II) Loading extension XINERAMA
[    23.651] (II) Loading sub module "dri2"
[    23.651] (II) LoadModule: "dri2"
[    23.651] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.651] (II) Module dri2: vendor="X.Org Foundation"
[    23.652]     compiled for 1.10.1, module version = 1.2.0
[    23.652]     ABI class: X.Org Server Extension, version 5.0
[    23.652] (II) NVIDIA(0): [DRI2] Setup complete
[    23.652] (==) RandR enabled
[    23.652] (II) Initializing built-in extension Generic Event Extension
[    23.652] (II) Initializing built-in extension SHAPE
[    23.652] (II) Initializing built-in extension MIT-SHM
[    23.652] (II) Initializing built-in extension XInputExtension
[    23.652] (II) Initializing built-in extension XTEST
[    23.652] (II) Initializing built-in extension BIG-REQUESTS
[    23.652] (II) Initializing built-in extension SYNC
[    23.652] (II) Initializing built-in extension XKEYBOARD
[    23.652] (II) Initializing built-in extension XC-MISC
[    23.652] (II) Initializing built-in extension SECURITY
[    23.652] (II) Initializing built-in extension XINERAMA
[    23.652] (II) Initializing built-in extension XFIXES
[    23.652] (II) Initializing built-in extension RENDER
[    23.652] (II) Initializing built-in extension RANDR
[    23.652] (II) Initializing built-in extension COMPOSITE
[    23.652] (II) Initializing built-in extension DAMAGE
[    23.652] (II) Initializing built-in extension GESTURE
[    23.655] (II) Initializing extension GLX
[    23.687] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.697] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.697] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.697] (II) LoadModule: "evdev"
[    23.698] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.698] (II) Module evdev: vendor="X.Org Foundation"
[    23.698]     compiled for 1.10.0.902, module version = 2.6.0
[    23.698]     Module class: X.Org XInput Driver
[    23.698]     ABI class: X.Org XInput driver, version 12.3
[    23.698] (II) Using input driver 'evdev' for 'Power Button'
[    23.698] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.698] (**) Power Button: always reports core events
[    23.698] (**) Power Button: Device: "/dev/input/event1"
[    23.699] (--) Power Button: Found keys
[    23.699] (II) Power Button: Configuring as keyboard
[    23.699] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.699] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.699] (**) Option "xkb_rules" "evdev"
[    23.699] (**) Option "xkb_model" "pc105"
[    23.699] (**) Option "xkb_layout" "us"
[    23.703] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.703] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.703] (II) Using input driver 'evdev' for 'Power Button'
[    23.703] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.703] (**) Power Button: always reports core events
[    23.703] (**) Power Button: Device: "/dev/input/event0"
[    23.704] (--) Power Button: Found keys
[    23.704] (II) Power Button: Configuring as keyboard
[    23.704] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.704] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.704] (**) Option "xkb_rules" "evdev"
[    23.704] (**) Option "xkb_model" "pc105"
[    23.704] (**) Option "xkb_layout" "us"
[    23.711] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    23.711] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.711] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.711] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.711] (**) AT Translated Set 2 keyboard: always reports core events
[    23.711] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    23.711] (--) AT Translated Set 2 keyboard: Found keys
[    23.711] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    23.711] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    23.711] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    23.711] (**) Option "xkb_rules" "evdev"
[    23.711] (**) Option "xkb_model" "pc105"
[    23.711] (**) Option "xkb_layout" "us"
[    23.712] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event3)
[    23.712] (**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    23.712] (II) Using input driver 'evdev' for 'ImPS/2 Logitech Wheel Mouse'
[    23.712] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.712] (**) ImPS/2 Logitech Wheel Mouse: always reports core events
[    23.712] (**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event3"
[    23.712] (--) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[    23.712] (--) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
[    23.712] (--) ImPS/2 Logitech Wheel Mouse: Found relative axes
[    23.712] (--) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
[    23.712] (II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
[    23.712] (II) ImPS/2 Logitech Wheel Mouse: Adding scrollwheel support
[    23.712] (**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[    23.712] (**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.712] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    23.712] (II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
[    23.713] (II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
[    23.713] (**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[    23.713] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[    23.713] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[    23.713] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[    23.713] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[    23.713] (II) No input driver/identifier specified (ignoring)
[  1031.640] (II) Power Button: Close
[  1031.640] (II) UnloadModule: "evdev"
[  1031.640] (II) Unloading evdev
[  1031.704] (II) Power Button: Close
[  1031.704] (II) UnloadModule: "evdev"
[  1031.704] (II) Unloading evdev
[  1031.744] (II) AT Translated Set 2 keyboard: Close
[  1031.744] (II) UnloadModule: "evdev"
[  1031.744] (II) Unloading evdev
[  1031.796] (II) ImPS/2 Logitech Wheel Mouse: Close
[  1031.796] (II) UnloadModule: "evdev"
[  1031.796] (II) Unloading evdev
[  1032.146]  ddxSigGiveUp: Closing log

```

---

### Post by papibe on 2011-09-02
```
NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
```
Are you sure that was the log from a boot with the DVI cable connected? I only see references to CRT-0, which is usually analog (VGA) connection. A typical reference to a DVI connection would be named DFP-0 (digital flat panel). Please confirm that.

Anyway, I'll assume it is correct. It looks like the info containing the timings and resolutions supported by the monitor can not be obtained using the DVI connection (EDID).

If your VGA connection works fine, there is a chance that it can be obtained using the VGA connection. If you can get that info from the good connection it is possible to use it to feed it to the bad one.

To obtain the EDID data:
[LIST]
[*]Boot using the VGA cable.
[*]Go to: NVIDIA X Server Setting.
[*]From the left hand list choose: &#8220;CRT-0&#8221;
[*]Click the &#8220;Aquire EDID&#8221; button.
[*]Save &#8220;edid.bin&#8221; to a folder that you'll remember.
[*]Close &#8220;NVIDIA X Server Settings&#8221; window.
[/LIST]
Once you get the data post is as attachment (because is a binary file). I can take a look at it to check if it's not corrupted, and tell you if it can be used.

Regards.

---

