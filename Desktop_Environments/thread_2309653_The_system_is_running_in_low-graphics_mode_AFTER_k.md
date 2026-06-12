---
title: "The system is running in low-graphics mode AFTER keytouch-editor"
date: 2016-01-12
forum: Desktop Environments
---

### Post by chrie2 on 2016-01-12
I tried to change the special function keys on my MS Natural Multimedia Keyboard V.1.0A
 I used the app keytouch-editor. I did the installation over the Software Center.
 I tried to put a function to one of the Multimedia keys.
 However this shows now success. After that all special function keys doesn't work.
 I restarted the PC. After the restart Ubuntu shows the message “The system is running in low-graphics mode” the keyboard and the mouse doesn't reacted on the window.

 So I switched to the console and unistalled keytouch-editor.

 Now I can use the mouse on the screen “The system is running in low-graphics mode*
 But the available options have no impact?
 

 I use Ubuntu 14.04 and I am new to Ubuntu (Linux).
 

```
 Start-Date: 2016-01-12  12:07:54 
 Commandline: aptdaemon role='role-commit-packages' sender=':1.101' 
 Install: menu:amd64 (2.1.46ubuntu1, automatic), keytouch-editor:amd64 (3.2.0~beta-3) 
 End-Date: 2016-01-12  12:07:55 
  
 Start-Date: 2016-01-12  13:07:12 
 Commandline: apt-get purge keytouch-editor 
 Purge: keytouch-editor:amd64 (3.2.0~beta-3) 
 End-Date: 2016-01-12  13:07:13
```

---

### Post by chrie2 on 2016-01-12
Maybe the issue was not provoked by keytouch-editor.
I read so far a bunch of aritcles. I think Ubuntu did also an update before I restarted.

```
[     3.191] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[     3.191] X Protocol Version 11, Revision 0
[     3.191] Build Operating System: Linux 3.2.0-77-generic x86_64 Ubuntu
[     3.191] Current Operating System: Linux nix 3.19.0-43-generic #49~14.04.1-Ubuntu SMP Thu Dec 31 15:44:49 UTC 2015 x86_64
[     3.191] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-43-generic.efi.signed root=UUID=XXXXXXXXXXXXXXXXXXXXXXX ro quiet splash vt.handoff=7
[     3.191] Build Date: 13 May 2015  04:35:05AM
[     3.191] xorg-server 2:1.17.1-0ubuntu3~trusty1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     3.191] Current version of pixman: 0.30.2
[     3.191]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     3.191] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.191] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 12 21:46:11 2016
[     3.191] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.191] (==) No Layout section.  Using the first Screen section.
[     3.191] (==) No screen section available. Using defaults.
[     3.191] (**) |-->Screen "Default Screen Section" (0)
[     3.191] (**) |   |-->Monitor "<default monitor>"
[     3.191] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     3.191] (==) Automatically adding devices
[     3.191] (==) Automatically enabling devices
[     3.191] (==) Automatically adding GPU devices
[     3.191] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.191]     Entry deleted from font path.
[     3.191] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.191]     Entry deleted from font path.
[     3.191] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.191]     Entry deleted from font path.
[     3.191] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.191]     Entry deleted from font path.
[     3.191] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.191]     Entry deleted from font path.
[     3.191] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.191] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.191] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.191] (II) Loader magic: 0x55848cf73c60
[     3.191] (II) Module ABI versions:
[     3.191]     X.Org ANSI C Emulation: 0.4
[     3.191]     X.Org Video Driver: 19.0
[     3.191]     X.Org XInput driver : 21.0
[     3.191]     X.Org Server Extension : 9.0
[     3.191] (II) xfree86: Adding drm device (/dev/dri/card0)
[     3.192] (--) PCI:*(0:0:2:0) 8086:0412:1043:8534 rev 6, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     3.192] (II) LoadModule: "glx"
[     3.192] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.200] (II) Module glx: vendor="X.Org Foundation"
[     3.200]     compiled for 1.17.1, module version = 1.0.0
[     3.200]     ABI class: X.Org Server Extension, version 9.0
[     3.200] (==) AIGLX enabled
[     3.200] (==) Matched intel as autoconfigured driver 0
[     3.200] (==) Matched intel as autoconfigured driver 1
[     3.200] (==) Matched modesetting as autoconfigured driver 2
[     3.200] (==) Matched fbdev as autoconfigured driver 3
[     3.200] (==) Matched vesa as autoconfigured driver 4
[     3.200] (==) Assigned the driver to the xf86ConfigLayout
[     3.200] (II) LoadModule: "intel"
[     3.200] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.201] (II) Module intel: vendor="X.Org Foundation"
[     3.201]     compiled for 1.17.1, module version = 2.99.917
[     3.201]     Module class: X.Org Video Driver
[     3.201]     ABI class: X.Org Video Driver, version 19.0
[     3.201] (II) LoadModule: "modesetting"
[     3.201] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.201] (II) Module modesetting: vendor="X.Org Foundation"
[     3.201]     compiled for 1.17.1, module version = 1.17.1
[     3.201]     Module class: X.Org Video Driver
[     3.201]     ABI class: X.Org Video Driver, version 19.0
[     3.201] (II) LoadModule: "fbdev"
[     3.201] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.201] (II) Module fbdev: vendor="X.Org Foundation"
[     3.201]     compiled for 1.17.1, module version = 0.4.4
[     3.201]     Module class: X.Org Video Driver
[     3.201]     ABI class: X.Org Video Driver, version 19.0
[     3.201] (II) LoadModule: "vesa"
[     3.201] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.201] (II) Module vesa: vendor="X.Org Foundation"
[     3.201]     compiled for 1.17.1, module version = 2.3.3
[     3.201]     Module class: X.Org Video Driver
[     3.201]     ABI class: X.Org Video Driver, version 19.0
[     3.201] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     3.201] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     3.201] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     3.201] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     3.201] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     3.201] (II) FBDEV: driver for framebuffer: fbdev
[     3.201] (II) VESA: driver for VESA chipsets: vesa
[     3.201] (++) using VT number 7

[     3.201] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[     3.201] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-vivid 2:2.99.917-1~exp1ubuntu2.2~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[     3.201] (II) intel(0): SNA compiled for use with valgrind
[     3.202] (WW) Falling back to old probe method for modesetting
[     3.202] (WW) Falling back to old probe method for fbdev
[     3.202] (II) Loading sub module "fbdevhw"
[     3.202] (II) LoadModule: "fbdevhw"
[     3.202] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.202] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.202]     compiled for 1.17.1, module version = 0.0.2
[     3.202]     ABI class: X.Org Video Driver, version 19.0
[     3.202] (WW) Falling back to old probe method for vesa
[     3.202] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[     3.202] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     3.202] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     3.202] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     3.202] (==) intel(0): RGB weight 888
[     3.202] (==) intel(0): Default visual is TrueColor
[     3.202] (II) intel(0): Output VGA1 has no monitor section
[     3.202] (II) intel(0): Enabled output VGA1
[     3.202] (II) intel(0): Output DP1 has no monitor section
[     3.202] (II) intel(0): Enabled output DP1
[     3.202] (II) intel(0): Output HDMI1 has no monitor section
[     3.202] (II) intel(0): Enabled output HDMI1
[     3.202] (II) intel(0): Output HDMI2 has no monitor section
[     3.202] (II) intel(0): Enabled output HDMI2
[     3.202] (II) intel(0): Output HDMI3 has no monitor section
[     3.202] (II) intel(0): Enabled output HDMI3
[     3.202] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     3.216] (II) intel(0): Output VIRTUAL1 has no monitor section
[     3.216] (II) intel(0): Enabled output VIRTUAL1
[     3.216] (--) intel(0): Output HDMI2 using initial mode 1680x1050 on pipe 1
[     3.216] (--) intel(0): Output HDMI3 using initial mode 1920x1080 on pipe 0
[     3.216] (==) intel(0): TearFree disabled
[     3.216] (==) intel(0): DPI set to (96, 96)
[     3.216] (II) Loading sub module "dri2"
[     3.216] (II) LoadModule: "dri2"
[     3.216] (II) Module "dri2" already built-in
[     3.216] (II) Loading sub module "present"
[     3.216] (II) LoadModule: "present"
[     3.216] (II) Module "present" already built-in
[     3.216] (II) UnloadModule: "modesetting"
[     3.216] (II) Unloading modesetting
[     3.216] (II) UnloadModule: "fbdev"
[     3.216] (II) Unloading fbdev
[     3.216] (II) UnloadSubModule: "fbdevhw"
[     3.216] (II) Unloading fbdevhw
[     3.216] (II) UnloadModule: "vesa"
[     3.216] (II) Unloading vesa
[     3.216] (==) Depth 24 pixmap format is 32 bpp
[     3.216] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[     3.216] (==) intel(0): Backing store enabled
[     3.216] (==) intel(0): Silken mouse enabled
[     3.216] (II) intel(0): HW Cursor enabled
[     3.216] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     3.216] (==) intel(0): DPMS enabled
[     3.216] (==) intel(0): display hotplug detection enabled
[     3.216] (II) intel(0): [DRI2] Setup complete
[     3.216] (II) intel(0): [DRI2]   DRI driver: i965
[     3.216] (II) intel(0): [DRI2]   VDPAU driver: i965
[     3.216] (II) intel(0): direct rendering: DRI2 enabled
[     3.216] (II) intel(0): hardware support for Present enabled
[     3.216] (--) RandR disabled
[     3.235] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     3.235] (II) AIGLX: enabled GLX_ARB_create_context
[     3.235] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     3.235] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     3.235] (II) AIGLX: enabled GLX_INTEL_swap_event
[     3.235] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     3.235] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     3.235] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     3.235] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     3.235] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     3.235] (II) AIGLX: Loaded and initialized i965
[     3.235] (II) GLX: Initialized DRI2 GL provider for screen 0
[     3.237] (II) intel(0): switch to mode 1920x1080@50.0 on HDMI3 using pipe 0, position (0, 0), rotation normal, reflection none
[     3.252] (II) intel(0): switch to mode 1680x1050@59.9 on HDMI2 using pipe 1, position (0, 0), rotation normal, reflection none
[     3.263] (II) intel(0): Setting screen physical size to 508 x 285
[     3.267] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.268] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.268] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.268] (II) LoadModule: "evdev"
[     3.268] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.269] (II) Module evdev: vendor="X.Org Foundation"
[     3.269]     compiled for 1.17.1, module version = 2.9.0
[     3.269]     Module class: X.Org XInput Driver
[     3.269]     ABI class: X.Org XInput driver, version 21.0
[     3.269] (II) Using input driver 'evdev' for 'Power Button'
[     3.269] (**) Power Button: always reports core events
[     3.269] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.269] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.269] (--) evdev: Power Button: Found keys
[     3.269] (II) evdev: Power Button: Configuring as keyboard
[     3.269] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.269] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.269] (**) Option "xkb_rules" "evdev"
[     3.269] (**) Option "xkb_model" "pc105"
[     3.269] (**) Option "xkb_layout" "de"
[     3.271] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[     3.271] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.271] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.271] (II) Using input driver 'evdev' for 'Power Button'
[     3.271] (**) Power Button: always reports core events
[     3.271] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.271] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.271] (--) evdev: Power Button: Found keys
[     3.271] (II) evdev: Power Button: Configuring as keyboard
[     3.271] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     3.271] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     3.271] (**) Option "xkb_rules" "evdev"
[     3.271] (**) Option "xkb_model" "pc105"
[     3.271] (**) Option "xkb_layout" "de"
[     3.272] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[     3.272] (II) No input driver specified, ignoring this device.
[     3.272] (II) This device may have been added with another device file.
[     3.272] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event9)
[     3.272] (II) No input driver specified, ignoring this device.
[     3.272] (II) This device may have been added with another device file.
[     3.272] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event5)
[     3.272] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[     3.272] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[     3.272] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[     3.272] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event5"
[     3.272] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x800
[     3.272] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[     3.272] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[     3.272] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/0003:045E:0800.0002/input/input5/event5"
[     3.272] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 8)
[     3.272] (**) Option "xkb_rules" "evdev"
[     3.272] (**) Option "xkb_model" "pc105"
[     3.272] (**) Option "xkb_layout" "de"
[     3.272] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event6)
[     3.272] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev pointer catchall"
[     3.272] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[     3.272] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[     3.272] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event6"
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x800
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 9 mouse buttons
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y relative axes
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[     3.328] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[     3.328] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.328] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.1/0003:045E:0800.0003/input/input6/event6"
[     3.328] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: MOUSE, id 9)
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[     3.328] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/mouse1)
[     3.328] (II) No input driver specified, ignoring this device.
[     3.328] (II) This device may have been added with another device file.
[     3.328] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event7)
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[     3.328] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[     3.328] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event7"
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x800
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 1 mouse buttons
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute multitouch axes
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y absolute axes
[     3.328] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Forcing relative x/y axes to exist.
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[     3.328] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[     3.328] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.328] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.2/0003:045E:0800.0004/input/input7/event7"
[     3.328] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 10)
[     3.328] (**) Option "xkb_rules" "evdev"
[     3.328] (**) Option "xkb_model" "pc105"
[     3.328] (**) Option "xkb_layout" "de"
[     3.328] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[     3.328] (WW) evdev: Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[     3.328] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[     3.329] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/js0)
[     3.329] (II) No input driver specified, ignoring this device.
[     3.329] (II) This device may have been added with another device file.
[     3.329] (II) config/udev: Adding input device Microsoft Corporation Microsoft ® Laser Mouse 6000 (/dev/input/event4)
[     3.329] (**) Microsoft Corporation Microsoft ® Laser Mouse 6000: Applying InputClass "evdev pointer catchall"
[     3.329] (II) Using input driver 'evdev' for 'Microsoft Corporation Microsoft ® Laser Mouse 6000'
[     3.329] (**) Microsoft Corporation Microsoft ® Laser Mouse 6000: always reports core events
[     3.329] (**) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Device: "/dev/input/event4"
[     3.388] (--) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Vendor 0x45e Product 0xf0
[     3.388] (--) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Found 9 mouse buttons
[     3.388] (--) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Found scroll wheel(s)
[     3.388] (--) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Found relative axes
[     3.388] (--) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Found x and y relative axes
[     3.388] (II) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Configuring as mouse
[     3.388] (II) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Adding scrollwheel support
[     3.388] (**) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: YAxisMapping: buttons 4 and 5
[     3.388] (**) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.388] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/0003:045E:00F0.0001/input/input4/event4"
[     3.388] (II) XINPUT: Adding extended input device "Microsoft Corporation Microsoft ® Laser Mouse 6000" (type: MOUSE, id 11)
[     3.388] (II) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: initialized for relative axes.
[     3.388] (**) Microsoft Corporation Microsoft ® Laser Mouse 6000: (accel) keeping acceleration scheme 1
[     3.388] (**) Microsoft Corporation Microsoft ® Laser Mouse 6000: (accel) acceleration profile 0
[     3.388] (**) Microsoft Corporation Microsoft ® Laser Mouse 6000: (accel) acceleration factor: 2.000
[     3.388] (**) Microsoft Corporation Microsoft ® Laser Mouse 6000: (accel) acceleration threshold: 4
[     3.388] (II) config/udev: Adding input device Microsoft Corporation Microsoft ® Laser Mouse 6000 (/dev/input/mouse0)
[     3.388] (II) No input driver specified, ignoring this device.
[     3.388] (II) This device may have been added with another device file.
[     3.388] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event12)
[     3.388] (II) No input driver specified, ignoring this device.
[     3.388] (II) This device may have been added with another device file.
[     3.388] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event13)
[     3.388] (II) No input driver specified, ignoring this device.
[     3.388] (II) This device may have been added with another device file.
[     3.388] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event14)
[     3.388] (II) No input driver specified, ignoring this device.
[     3.388] (II) This device may have been added with another device file.
[     3.388] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event15)
[     3.388] (II) No input driver specified, ignoring this device.
[     3.388] (II) This device may have been added with another device file.
[     3.389] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event16)
[     3.389] (II) No input driver specified, ignoring this device.
[     3.389] (II) This device may have been added with another device file.
[     3.389] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event17)
[     3.389] (II) No input driver specified, ignoring this device.
[     3.389] (II) This device may have been added with another device file.
[     3.389] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[     3.389] (II) No input driver specified, ignoring this device.
[     3.389] (II) This device may have been added with another device file.
[     3.389] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event11)
[     3.389] (II) No input driver specified, ignoring this device.
[     3.389] (II) This device may have been added with another device file.
[     3.389] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event18)
[     3.389] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     3.389] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     3.389] (**) Eee PC WMI hotkeys: always reports core events
[     3.389] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event18"
[     3.389] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     3.389] (--) evdev: Eee PC WMI hotkeys: Found keys
[     3.389] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     3.389] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input18/event18"
[     3.389] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[     3.389] (**) Option "xkb_rules" "evdev"
[     3.389] (**) Option "xkb_model" "pc105"
[     3.389] (**) Option "xkb_layout" "de"
[     3.389] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     3.389] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     3.389] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     3.389] (**) AT Translated Set 2 keyboard: always reports core events
[     3.389] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[     3.389] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     3.389] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     3.389] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     3.389] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[     3.389] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[     3.389] (**) Option "xkb_rules" "evdev"
[     3.389] (**) Option "xkb_model" "pc105"
[     3.389] (**) Option "xkb_layout" "de"
[     3.552] (II) evdev: AT Translated Set 2 keyboard: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.552] (II) evdev: Eee PC WMI hotkeys: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.552] (II) evdev: Microsoft Corporation Microsoft ® Laser Mouse 6000: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.552] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.552] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.552] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.552] (II) evdev: Power Button: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.552] (II) evdev: Power Button: Close
[     3.552] (II) UnloadModule: "evdev"
[     3.556] (II) Server terminated successfully (0). Closing log file.
```

---

