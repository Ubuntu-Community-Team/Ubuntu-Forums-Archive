---
title: "Installed 11.04 - video goes bad"
date: 2011-06-08
forum: Desktop Environments
---

### Post by Skaperen on 2011-06-08
The video actually works fine when I run the 11.04 in LiveCD mode.  This is both the video for the Xorg+Unity desktop, as well as the video for the text console.  Both operate in exactly the same video mode and the text console font is nicer than in 10.10 (which otherwise works just as well).  The monitor is 1920x1200, and the video modes exactly match it.

I actually installed 11.04 this time (after a suggestion given to get around the failure of the installer to handle a large number of GPT based partitions).  I installed with a reduced subset of partitions in the table (though at the same sector positions as before), and the installation did not hang this time (so I suspect an issue with the total number of partitions).

This is where the video problems begin.

Upon booting the installed system, at first all looks well in the desktop.  Then I switched to text console mode (Ctrl+Alt+F1).  All I could see was black.  I waited a minute and nothing.  I pressed Enter a few times and eventually the login prompt started coming down the screen.  It had been unviewable off the top of the screen.  Also, the font was a terrible fuzzy one.  But that turns out to be because the video mode was all wrong.  Instead of the expected 1920x1200 video mode, the mode was now a strange 1200x1400 (according to the monitor's status menu).  So the fuzzy font was from the video conversion of 1200x1400 to 1920x1200 native LCD.

Then I switched back to the graphical display (Alt+Ctrl+F7) and things went from bad to worse.  The display was all bit splatter.  Pieces of some menus that should have appeared were split and scattered around, with most of the splitting being horizontal stripes.  There were many chunks of just random pixel and random bit garbage, much like you might get if video RAM contained binary program code or binary number data.  The monitor did report the video mode as 1920x1200 now.  But the transition had apparently corrupted the video RAM contents and/or mappings.  New windows opening up did come out OK.  When closed, if they had covered garbage, that garbage came back.  Setting a background image had no effect (most of the garbage was in the background area of the desktop).

The video chip is NVIDIA 6150SE, which is known to have a problem with some versions of the nouveau driver.  However, the nouveau driver was NOT in use.  Instead, it was the "tainted" nvidia driver.  I would have expected this nvidia driver to work flawlessly over all NVIDIA chips, including this one.  I guess my trust in NVIDIA is worthless.

This machine had a couple months earlier run 10.10 installed with no  issues.  Going to 11.04 was a fresh install, not an upgrade from the  10.10.  I did notice in the installation that it was downloading many  megabytes of packages from the internet even though I had NOT checked  the installation option to allow that.  Could this have been a video driver upgrade relative to what was in the DVD?   I guess, the next time, I need  to pull the network cable.

I had just previous to this 11.04 install experienced troubles with the nouveau driver in Slackware64-13.37.  That trouble didn't look the same, was only experienced in graphical mode, and was always fine in text mode.  It was also completely corrected by switching the kernel and its modules (and hence the nouveau module) from 2.6.37.6 that came in Slackware64-13.37 to 2.6.38.7 that came in Slackware64-current.  A report on this experience is over on LQ:  [http://www.linuxquestions.org/questions/slackware-14/troubles-with-nouveau-nvidia-driver-on-13-37-a-884794/](http://www.linuxquestions.org/questions/slackware-14/troubles-with-nouveau-nvidia-driver-on-13-37-a-884794/)

So now my big question is, how easy is it to go with the (2.6.38.X) nouveau driver in 11.04?

The following is (not much) details on the video card from dmesg:```

[    9.489285] nvidia: module license 'NVIDIA' taints kernel.
[    9.816875] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 22 (level, low) -> IRQ 22
[    9.816883] nvidia 0000:00:0d.0: setting latency timer to 64
[    9.817142] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.30  Sat Apr 16 21:49:29 PDT 2011
```Here is /var/log/Xorg.0.log:```

[    20.739] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    20.739] X Protocol Version 11, Revision 0
[    20.739] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    20.739] Current Operating System: Linux orcus 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    20.739] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=275aef40-7126-422f-8998-77be78ac5bd0 r
o quiet splash vt.handoff=7
[    20.739] Build Date: 19 April 2011  03:40:45PM
[    20.739] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    20.739] Current version of pixman: 0.20.2
[    20.739]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    20.739] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.740] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  7 22:09:23 2011
[    20.771] (==) Using config file: "/etc/X11/xorg.conf"
[    20.771] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.805] (==) No Layout section.  Using the first Screen section.
[    20.805] (==) No screen section available. Using defaults.
[    20.805] (**) |-->Screen "Default Screen Section" (0)
[    20.805] (**) |   |-->Monitor "<default monitor>"
[    20.806] (==) No device specified for screen "Default Screen Section".
        Using the first device section listed.
[    20.806] (**) |   |-->Device "Default Device"
[    20.806] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    20.806] (==) Automatically adding devices
[    20.806] (==) Automatically enabling devices
[    20.834] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.834]    Entry deleted from font path.
[    20.834] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.834]    Entry deleted from font path.
[    20.834] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.834]    Entry deleted from font path.
[    20.834] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.834]    Entry deleted from font path.
[    20.834] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.834]    Entry deleted from font path.
[    20.835] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    20.835] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.835] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.835] (II) Loader magic: 0x7e0280
[    20.835] (II) Module ABI versions:
[    20.835]    X.Org ANSI C Emulation: 0.4
[    20.835]    X.Org Video Driver: 10.0
[    20.835]    X.Org XInput driver : 12.3
[    20.835]    X.Org Server Extension : 5.0
[    20.836] (--) PCI:*(0:0:13:0) 10de:03d0:1025:0181 rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdd000
000/16777216, BIOS @ 0x????????/131072
[    20.836] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.836] (II) LoadModule: "extmod"
[    20.914] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.923] (II) Module extmod: vendor="X.Org Foundation"
[    20.923]    compiled for 1.10.1, module version = 1.0.0
[    20.923]    Module class: X.Org Server Extension
[    20.924]    ABI class: X.Org Server Extension, version 5.0
[    20.924] (II) Loading extension MIT-SCREEN-SAVER
[    20.924] (II) Loading extension XFree86-VidModeExtension
[    20.924] (II) Loading extension XFree86-DGA
[    20.924] (II) Loading extension DPMS
[    20.924] (II) Loading extension XVideo
[    20.924] (II) Loading extension XVideo-MotionCompensation
[    20.924] (II) Loading extension X-Resource
[    20.924] (II) LoadModule: "dbe"
[    20.924] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.925] (II) Module dbe: vendor="X.Org Foundation"
[    20.925]    compiled for 1.10.1, module version = 1.0.0
[    20.925]    Module class: X.Org Server Extension
[    20.925]    ABI class: X.Org Server Extension, version 5.0
[    20.925] (II) Loading extension DOUBLE-BUFFER
[    20.925] (II) LoadModule: "glx"
[    20.925] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.301] (II) Module glx: vendor="NVIDIA Corporation"
[    21.301]    compiled for 4.0.2, module version = 1.0.0
[    21.301]    Module class: X.Org Server Extension
[    21.301] (II) NVIDIA GLX Module  173.14.30  Sat Apr 16 22:45:09 PDT 2011
[    21.301] (II) Loading extension GLX
[    21.301] (II) LoadModule: "record"
[    21.301] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.317] (II) Module record: vendor="X.Org Foundation"
[    21.317]    compiled for 1.10.1, module version = 1.13.0
[    21.317]    Module class: X.Org Server Extension
[    21.317]    ABI class: X.Org Server Extension, version 5.0
[    21.317] (II) Loading extension RECORD
[    21.317] (II) LoadModule: "dri"
[    21.318] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.323] (II) Module dri: vendor="X.Org Foundation"
[    21.323]    compiled for 1.10.1, module version = 1.0.0
[    21.323]    ABI class: X.Org Server Extension, version 5.0
[    21.323] (II) Loading extension XFree86-DRI
[    21.323] (II) LoadModule: "dri2"
[    21.323] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.324] (II) Module dri2: vendor="X.Org Foundation"
[    21.324]    compiled for 1.10.1, module version = 1.2.0
[    21.324]    ABI class: X.Org Server Extension, version 5.0
[    21.324] (II) Loading extension DRI2
[    21.324] (==) Matched nvidia as autoconfigured driver 0
[    21.324] (==) Matched nouveau as autoconfigured driver 1
[    21.324] (==) Matched nv as autoconfigured driver 2
[    21.324] (==) Matched vesa as autoconfigured driver 3
[    21.324] (==) Matched fbdev as autoconfigured driver 4
[    21.324] (==) Assigned the driver to the xf86ConfigLayout
[    21.324] (II) LoadModule: "nvidia"
[    21.324] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.391] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.391]    compiled for 4.0.2, module version = 1.0.0
[    21.391]    Module class: X.Org Video Driver
[    21.404] (II) LoadModule: "nouveau"
[    21.404] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.416] (II) Module nouveau: vendor="X.Org Foundation"
[    21.416]    compiled for 1.10.0, module version = 0.0.16
[    21.416]    Module class: X.Org Video Driver
[    21.416]    ABI class: X.Org Video Driver, version 10.0
[    21.416] (II) LoadModule: "nv"
[    21.421] (WW) Warning, couldn't open module nv
[    21.421] (II) UnloadModule: "nv"
[    21.421] (II) Unloading nv
[    21.421] (EE) Failed to load module "nv" (module does not exist, 0)
[    21.421] (II) LoadModule: "vesa"
[    21.421] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.432] (II) Module vesa: vendor="X.Org Foundation"
[    21.432]    compiled for 1.10.0, module version = 2.3.0
[    21.432]    Module class: X.Org Video Driver
[    21.433]    ABI class: X.Org Video Driver, version 10.0
[    21.433] (II) LoadModule: "fbdev"
[    21.433] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.439] (II) Module fbdev: vendor="X.Org Foundation"
[    21.439]    compiled for 1.10.0, module version = 0.4.2
[    21.439]    ABI class: X.Org Video Driver, version 10.0
[    21.439] (II) NVIDIA dlloader X Driver  173.14.30  Sat Apr 16 22:18:29 PDT 2011
[    21.440] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.440] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    21.440] (II) NOUVEAU driver for NVIDIA chipset families :
[    21.440]    RIVA TNT    (NV04)
[    21.440]    RIVA TNT2   (NV05)
[    21.440]    GeForce 256 (NV10)
[    21.440]    GeForce 2   (NV11, NV15)
[    21.440]    GeForce 4MX (NV17, NV18)
[    21.440]    GeForce 3   (NV20)
[    21.440]    GeForce 4Ti (NV25, NV28)
[    21.440]    GeForce FX  (NV3x)
[    21.440]    GeForce 6   (NV4x)
[    21.440]    GeForce 7   (G7x)
[    21.440]    GeForce 8   (G8x)
[    21.440] (II) VESA: driver for VESA chipsets: vesa
[    21.440] (II) FBDEV: driver for framebuffer: fbdev
[    21.440] (++) using VT number 7

[    21.441] (II) Loading sub module "fb"
[    21.441] (II) LoadModule: "fb"
[    21.441] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.449] (II) Module fb: vendor="X.Org Foundation"
[    21.449]    compiled for 1.10.1, module version = 1.0.0
[    21.449]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.449] (II) Loading sub module "wfb"
[    21.449] (II) LoadModule: "wfb"
[    21.450] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.453] (II) Module wfb: vendor="X.Org Foundation"
[    21.453]    compiled for 1.10.1, module version = 1.0.0
[    21.453]    ABI class: X.Org ANSI C Emulation, version 0.4
[    21.453] (II) Loading sub module "ramdac"
[    21.453] (II) LoadModule: "ramdac"
[    21.453] (II) Module "ramdac" already built-in
[    21.453] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    21.453] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.453] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.454] (WW) Falling back to old probe method for vesa
[    21.454] (WW) Falling back to old probe method for fbdev
[    21.454] (II) Loading sub module "fbdevhw"
[    21.454] (II) LoadModule: "fbdevhw"
[    21.454] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.455] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.455]    compiled for 1.10.1, module version = 0.0.2
[    21.455]    ABI class: X.Org Video Driver, version 10.0
[    21.456] (II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    21.456] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    21.456] (==) NVIDIA(0): RGB weight 888
[    21.456] (==) NVIDIA(0): Default visual is TrueColor
[    21.456] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.456] (**) NVIDIA(0): Option "NoLogo" "True"
[    21.457] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.457] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.457] (II) NVIDIA(0):     enabled.
[    22.072] (II) NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
[    22.072] (II) NVIDIA(0):     (GPU-0)
[    22.072] (--) NVIDIA(0): Memory: 524288 kBytes
[    22.072] (--) NVIDIA(0): VideoBIOS: 05.61.32.28.03
[    22.072] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.072] (--) NVIDIA(0): Connected display device(s) on GeForce 6150SE nForce 430 at
[    22.072] (--) NVIDIA(0):     PCI:0:13:0:
[    22.072] (--) NVIDIA(0):     NEC EA241WM (CRT-0)
[    22.072] (--) NVIDIA(0): NEC EA241WM (CRT-0): 350.0 MHz maximum pixel clock
[    22.073] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    22.073] (==) NVIDIA(0): 
[    22.073] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    22.073] (==) NVIDIA(0):     will be used as the requested mode.
[    22.073] (==) NVIDIA(0): 
[    22.073] (II) NVIDIA(0): Validated modes:
[    22.073] (II) NVIDIA(0):     "nvidia-auto-select"
[    22.073] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    22.074] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    22.074] (--) NVIDIA(0):     option
[    22.074] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    22.085] (II) UnloadModule: "nouveau"
[    22.085] (II) Unloading nouveau
[    22.085] (II) UnloadModule: "vesa"
[    22.085] (II) Unloading vesa
[    22.085] (II) UnloadModule: "fbdev"
[    22.085] (II) Unloading fbdev
[    22.085] (II) UnloadModule: "fbdevhw"
[    22.085] (II) Unloading fbdevhw
[    22.085] (--) Depth 24 pixmap format is 32 bpp
[    22.087] (II) NVIDIA(0): Initialized GPU GART.
[    22.089] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    22.186] (II) Loading extension NV-GLX
[    22.240] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    22.256] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    22.256] (==) NVIDIA(0): Backing store disabled
[    22.256] (==) NVIDIA(0): Silken mouse enabled
[    22.269] (==) NVIDIA(0): DPMS enabled
[    22.269] (II) Loading extension NV-CONTROL
[    22.269] (==) RandR enabled
[    22.269] (II) Initializing built-in extension Generic Event Extension
[    22.269] (II) Initializing built-in extension SHAPE
[    22.269] (II) Initializing built-in extension MIT-SHM
[    22.269] (II) Initializing built-in extension XInputExtension
[    22.269] (II) Initializing built-in extension XTEST
[    22.269] (II) Initializing built-in extension BIG-REQUESTS
[    22.269] (II) Initializing built-in extension SYNC
[    22.269] (II) Initializing built-in extension XKEYBOARD
[    22.269] (II) Initializing built-in extension XC-MISC
[    22.269] (II) Initializing built-in extension SECURITY
[    22.269] (II) Initializing built-in extension XINERAMA
[    22.269] (II) Initializing built-in extension XFIXES
[    22.269] (II) Initializing built-in extension RENDER
[    22.269] (II) Initializing built-in extension RANDR
[    22.269] (II) Initializing built-in extension COMPOSITE
[    22.269] (II) Initializing built-in extension DAMAGE
[    22.269] (II) Initializing built-in extension GESTURE
[    22.272] (II) Initializing extension GLX
[    22.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.629] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.629] (II) LoadModule: "evdev"
[    22.629] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.718] (II) Module evdev: vendor="X.Org Foundation"
[    22.718]    compiled for 1.10.0.902, module version = 2.6.0
[    22.718]    Module class: X.Org XInput Driver
[    22.718]    ABI class: X.Org XInput driver, version 12.3
[    22.718] (II) Using input driver 'evdev' for 'Power Button'
[    22.718] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.718] (**) Power Button: always reports core events
[    22.718] (**) Power Button: Device: "/dev/input/event1"
[    22.740] (--) Power Button: Found keys
[    22.740] (II) Power Button: Configuring as keyboard
[    22.740] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.740] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.740] (**) Option "xkb_rules" "evdev"
[    22.740] (**) Option "xkb_model" "pc105"
[    22.740] (**) Option "xkb_layout" "us"
[    22.743] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.743] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.743] (II) Using input driver 'evdev' for 'Power Button'
[    22.743] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.743] (**) Power Button: always reports core events
[    22.743] (**) Power Button: Device: "/dev/input/event0"
[    22.744] (--) Power Button: Found keys
[    22.744] (II) Power Button: Configuring as keyboard
[    22.744] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.744] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.744] (**) Option "xkb_rules" "evdev"
[    22.744] (**) Option "xkb_model" "pc105"
[    22.744] (**) Option "xkb_layout" "us"
[    22.749] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event4)
[    22.749] (II) No input driver/identifier specified (ignoring)
[    22.761] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    22.761] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.761] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.761] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.761] (**) AT Translated Set 2 keyboard: always reports core events
[    22.761] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    22.762] (--) AT Translated Set 2 keyboard: Found keys
[    22.762] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    22.762] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    22.762] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    22.762] (**) Option "xkb_rules" "evdev"
[    22.762] (**) Option "xkb_model" "pc105"
[    22.762] (**) Option "xkb_layout" "us"
[    22.763] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    22.763] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    22.763] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    22.763] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.763] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    22.763] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    22.763] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    22.763] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    22.763] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    22.763] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    22.763] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    22.763] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    22.763] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    22.763] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.763] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    22.763] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    22.763] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    22.763] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    22.763] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    22.764] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    22.764] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    22.764] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    22.764] (II) No input driver/identifier specified (ignoring)
[    44.078] (II) Open ACPI successful (/var/run/acpid.socket)
[    44.172] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    94.700] (II) Power Button: Close
[    94.700] (II) UnloadModule: "evdev"
[    94.700] (II) Unloading evdev
[    94.790] (II) Power Button: Close
[    94.790] (II) UnloadModule: "evdev"
[    94.790] (II) Unloading evdev
[    94.890] (II) AT Translated Set 2 keyboard: Close
[    94.890] (II) UnloadModule: "evdev"
[    94.890] (II) Unloading evdev
[    94.960] (II) ImPS/2 Generic Wheel Mouse: Close
[    94.960] (II) UnloadModule: "evdev"
[    94.960] (II) Unloading evdev
[    95.906]  ddxSigGiveUp: Closing log
```The following is more details from dmesg as reported by Slackware running nouveau from 2.6.38.7 kernel:```

[    9.925419] nouveau 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 21 (level, low) -> IRQ 21
[    9.925705] nouveau 0000:00:0d.0: setting latency timer to 64
[    9.930957] [drm] nouveau 0000:00:0d.0: Detected an NV40 generation card (0x04c000a2)
[    9.933687] [drm] nouveau 0000:00:0d.0: Attempting to load BIOS image from PRAMIN
[    9.984783] [drm] nouveau 0000:00:0d.0: ... appears to be valid
[    9.984945] [drm] nouveau 0000:00:0d.0: BIT BIOS found
[    9.985115] [drm] nouveau 0000:00:0d.0: Bios version 05.61.32.28
[    9.985274] [drm] nouveau 0000:00:0d.0: TMDS table version 1.1
[    9.985431] [drm] nouveau 0000:00:0d.0: BIT table 'd' not found
[    9.985588] [drm] nouveau 0000:00:0d.0: Found Display Configuration Block version 3.0
[    9.985870] [drm] nouveau 0000:00:0d.0: Raw DCB entry 0: 01000310 00000023
[    9.986043] [drm] nouveau 0000:00:0d.0: Raw DCB entry 1: 00110204 942b0003
[    9.986203] [drm] nouveau 0000:00:0d.0: DCB connector table: VHER 0x30 5 10 2
[    9.986363] [drm] nouveau 0000:00:0d.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[    9.986645] [drm] nouveau 0000:00:0d.0:   1: 0x00001131: type 0x31 idx 1 tag 0x07
[    9.986925] [drm] nouveau 0000:00:0d.0:   2: 0x00000110: type 0x10 idx 2 tag 0xff
[    9.987219] [drm] nouveau 0000:00:0d.0:   3: 0x00000111: type 0x11 idx 3 tag 0xff
[    9.987500] [drm] nouveau 0000:00:0d.0:   4: 0x00000113: type 0x13 idx 4 tag 0xff
[    9.987785] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 0 at offset 0xD9C9
[    9.988077] [drm] nouveau 0000:00:0d.0: ======= misaligned reg 0x0060081D =======
[    9.988359] [drm] nouveau 0000:00:0d.0: ======= misaligned reg 0x0060081D =======
[    9.988702] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 1 at offset 0xDB17
[    9.988983] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 2 at offset 0xDB18
[    9.989355] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 3 at offset 0xDC9A
[    9.989641] [drm] nouveau 0000:00:0d.0: Parsing VBIOS init table 4 at offset 0xDCE3
[   10.230052] [drm] nouveau 0000:00:0d.0: 1 available performance level(s)
[   10.230218] [drm] nouveau 0000:00:0d.0: 0: memory 0MHz core 425MHz fanspeed 100%
[   10.230505] [drm] nouveau 0000:00:0d.0: c: memory 0MHz
[   10.230782] [TTM] Zone  kernel: Available graphics memory: 1893594 kiB.
[   10.230949] [TTM] Initializing pool allocator.
[   10.231141] [drm] nouveau 0000:00:0d.0: Detected 256MiB VRAM
[   10.232884] [drm] nouveau 0000:00:0d.0: 64 MiB GART (aperture)
[   10.233115] [drm] nouveau 0000:00:0d.0: Saving VGA fonts
[   10.282170] [drm] nouveau 0000:00:0d.0: unknown connector type: 0xff!!
[   10.283543] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.283725] [drm] No driver support for vblank timestamp query.
[   10.284320] [drm] nouveau 0000:00:0d.0: Setting dpms mode 3 on vga encoder (output 0)
[   10.413193] [drm] nouveau 0000:00:0d.0: allocated 1920x1200 fb: 0x49000, bo ffff880137121400
[   10.413696] fbcon: nouveaufb (fb0) is primary device
[   10.479078] [drm] nouveau 0000:00:0d.0: Setting dpms mode 0 on vga encoder (output 0)
[   10.479083] [drm] nouveau 0000:00:0d.0: Output VGA-1 is running on CRTC 0 using output A
[   10.483033] Console: switching to colour frame buffer device 240x75
[   10.487150] fb0: nouveaufb frame buffer device
[   10.487161] drm: registered panic notifier
[   10.487183] [drm] Initialized nouveau 0.0.16 20090420 for 0000:00:0d.0 on minor 0
```I have not been able to capture info from the 11.04 LiveCD (it works fine here), yet.  But I could do so if needed.

At work today, a user who regularly updates, and who has a machine with an NVIDIA chip built in, had exactly the same problem happen, though on a 1280x1024 monitor.  So it seems to be a recent update causing this.  Everything work for him before.  He had to reboot to fix it, and has to stay away from text console to avoid.

---

