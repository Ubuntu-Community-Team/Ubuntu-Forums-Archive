---
title: "xfce fails to load after update"
date: 2013-02-22
forum: Desktop Environments
---

### Post by danBhentschel on 2013-02-22
I just updated my mythbuntu server for the first time in a couple of weeks, and when it rebooted, X would not start. I am running 12.04 LTS. I have been using it "headless" without a monitor, using x11vnc for several months now without a problem. After this recent update, I can't connect via VNC any more. Here's some information:


xorg.conf:

```
Section "InputDevice"
        Identifier      "Dummy Input"
        Driver          "void"
EndSection
Section "Device"
        Identifier      "Dummy Video"
        Driver          "dummy"
EndSection
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Dummy Video"
EndSection
Section "ServerLayout"
        Identifier      "DefaultLayout"
        Screen          "Default Screen"
        InputDevice     "Dummy Input"
EndSection

```
```
[    10.840]
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    10.840] X Protocol Version 11, Revision 0
[    10.840] Build Operating System: Linux 2.6.42-34-generic i686 Ubuntu
[    10.840] Current Operating System: Linux raidman 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686
[    10.840] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic-pae root=UUID=7a06a25d-ceba-45ea-a197-42d43bc4ef3e ro quiet splash bootdegraded=true vt.handoff=7
[    10.840] Build Date: 16 January 2013  11:05:18PM
[    10.840] xorg-server 2:1.11.4-0ubuntu10.11 (For technical support please see http://www.ubuntu.com/support)
[    10.840] Current version of pixman: 0.24.4
[    10.840]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    10.840] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.840] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 22 21:24:22 2013
[    10.841] (==) Using config file: "/etc/X11/xorg.conf"
[    10.841] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.841] (==) ServerLayout "DefaultLayout"
[    10.841] (**) |-->Screen "Default Screen" (0)
[    10.841] (**) |   |-->Monitor "Configured Monitor"
[    10.841] (**) |   |-->Device "Dummy Video"
[    10.841] (**) |-->Input Device "Dummy Input"
[    10.841] (==) Automatically adding devices
[    10.841] (==) Automatically enabling devices
[    10.841] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.841]    Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.841]    Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.841]    Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.841]    Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.841]    Entry deleted from font path.
[    10.841] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    10.841]    Entry deleted from font path.
[    10.841]    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    10.841] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    10.841] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.841] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.841] (II) Loader magic: 0xb77865a0
[    10.841] (II) Module ABI versions:
[    10.841]    X.Org ANSI C Emulation: 0.4
[    10.841]    X.Org Video Driver: 11.0
[    10.841]    X.Org XInput driver : 16.0
[    10.841]    X.Org Server Extension : 6.0
[    10.842] (II) Open ACPI successful (/var/run/acpid.socket)
[    10.842] (II) LoadModule: "extmod"
[    10.842] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    10.842] (II) Module extmod: vendor="X.Org Foundation"
[    10.842]    compiled for 1.11.3, module version = 1.0.0
[    10.842]    Module class: X.Org Server Extension
[    10.842]    ABI class: X.Org Server Extension, version 6.0
[    10.842] (II) Loading extension MIT-SCREEN-SAVER
[    10.842] (II) Loading extension XFree86-VidModeExtension
[    10.842] (II) Loading extension XFree86-DGA
[    10.842] (II) Loading extension DPMS
[    10.842] (II) Loading extension XVideo
[    10.842] (II) Loading extension XVideo-MotionCompensation
[    10.842] (II) Loading extension X-Resource
[    10.842] (II) LoadModule: "dbe"
[    10.842] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    10.842] (II) Module dbe: vendor="X.Org Foundation"
[    10.842]    compiled for 1.11.3, module version = 1.0.0
[    10.842]    Module class: X.Org Server Extension
[    10.842]    ABI class: X.Org Server Extension, version 6.0
[    10.842] (II) Loading extension DOUBLE-BUFFER
[    10.842] (II) LoadModule: "glx"
[    10.842] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    10.857] (II) Module glx: vendor="NVIDIA Corporation"
[    10.857]    compiled for 4.0.2, module version = 1.0.0
[    10.857]    Module class: X.Org Server Extension
[    10.857] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:49:54 PDT 2012
[    10.857] (II) Loading extension GLX
[    10.857] (II) LoadModule: "record"
[    10.857] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    10.857] (II) Module record: vendor="X.Org Foundation"
[    10.857]    compiled for 1.11.3, module version = 1.13.0
[    10.857]    Module class: X.Org Server Extension
[    10.857]    ABI class: X.Org Server Extension, version 6.0
[    10.857] (II) Loading extension RECORD
[    10.857] (II) LoadModule: "dri"
[    10.857] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    10.857] (II) Module dri: vendor="X.Org Foundation"
[    10.857]    compiled for 1.11.3, module version = 1.0.0
[    10.857]    ABI class: X.Org Server Extension, version 6.0
[    10.857] (II) Loading extension XFree86-DRI
[    10.857] (II) LoadModule: "dri2"
[    10.858] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.858] (II) Module dri2: vendor="X.Org Foundation"
[    10.858]    compiled for 1.11.3, module version = 1.2.0
[    10.858]    ABI class: X.Org Server Extension, version 6.0
[    10.858] (II) Loading extension DRI2
[    10.858] (II) LoadModule: "dummy"
[    10.858] (II) Loading /usr/lib/xorg/modules/drivers/dummy_drv.so
[    10.858] (II) Module dummy: vendor="X.Org Foundation"
[    10.858]    compiled for 1.11.3, module version = 0.3.4
[    10.858]    Module class: X.Org Video Driver
[    10.858]    ABI class: X.Org Video Driver, version 11.0
[    10.858] (II) LoadModule: "void"
[    10.858] (II) Loading /usr/lib/xorg/modules/input/void_drv.so
[    10.858] (II) Module void: vendor="X.Org Foundation"
[    10.858]    compiled for 1.11.3, module version = 1.4.0
[    10.858]    Module class: X.Org XInput Driver
[    10.858]    ABI class: X.Org XInput driver, version 16.0
[    10.858] (II) DUMMY: Driver for Dummy chipsets: dummy
[    10.858] (WW) Falling back to old probe method for dummy
[    10.858] (II) Loading /usr/lib/xorg/modules/drivers/dummy_drv.so
[    10.858] (II) DUMMY(0): Chipset is a DUMMY
[    10.858] (II) DUMMY(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
[    10.858] (==) DUMMY(0): Depth 24, (--) framebuffer bpp 32
[    10.858] (==) DUMMY(0): RGB weight 888
[    10.858] (==) DUMMY(0): Default visual is TrueColor
[    10.858] (==) DUMMY(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.858] (--) DUMMY(0): VideoRAM: 4096 kByte
[    10.858] (--) DUMMY(0): Max Clock: 230000 kHz
[    10.858] (II) DUMMY(0): Configured Monitor: Using default hsync range of 31.50-48.00 kHz
[    10.858] (II) DUMMY(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[    10.858] (II) DUMMY(0): Configured Monitor: Using default maximum pixel clock of 65.00 MHz
[    10.858] (WW) DUMMY(0): Unable to estimate virtual size
[    10.858] (II) DUMMY(0): Clock range:  11.00 to 300.00 MHz
[    10.858] (II) DUMMY(0): Not using default mode "640x350" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "320x175" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "640x400" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "320x200" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "720x400" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "360x200" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "640x480" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "320x240" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "640x480" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "320x240" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "640x480" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "320x240" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "800x600" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "400x300" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "800x600" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "400x300" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "400x300" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1024x768i" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "512x384i" (vrefresh out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "512x384" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "512x384" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "512x384" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1280x960" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "640x480" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1280x960" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "640x480" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1280x1024" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "640x512" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1280x1024" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "640x512" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1280x1024" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "640x512" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[    10.858] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[    10.858] (II) DUMMY(0): Not using default mode "1600x1200" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "800x600" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "896x672" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "896x672" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "928x696" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "928x696" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "960x720" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "960x720" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "832x624" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "416x312" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1152x864" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "576x432" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    10.859] (II) DUMMY(0): Not using default mode "1360x768" (mode clock too high)
[    10.859] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "700x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "700x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "700x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1400x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "700x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1440x900" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "720x450" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1600x1024" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "800x512" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "840x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "840x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "840x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "840x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1680x1050" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "840x525" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1920x1080" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "960x540" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "960x600" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "960x720" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[    10.859] (II) DUMMY(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    10.859] (II) DUMMY(0): Not using default mode "1024x768" (hsync out of range)
[    10.859] (--) DUMMY(0): Virtual size is 1024x768 (pitch 1024)
[    10.859] (**) DUMMY(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    10.859] (II) DUMMY(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    10.859] (**) DUMMY(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    10.859] (II) DUMMY(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    10.859] (**) DUMMY(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    10.859] (II) DUMMY(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    10.859] (**) DUMMY(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    10.859] (II) DUMMY(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    10.859] (**) DUMMY(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    10.859] (II) DUMMY(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    10.859] (**) DUMMY(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    10.859] (II) DUMMY(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    10.859] (**) DUMMY(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    10.859] (II) DUMMY(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    10.859] (**) DUMMY(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    10.859] (II) DUMMY(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    10.859] (**) DUMMY(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    10.859] (II) DUMMY(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    10.859] (**) DUMMY(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    10.859] (II) DUMMY(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    10.859] (==) DUMMY(0): DPI set to (96, 96)
[    10.859] (II) Loading sub module "fb"
[    10.859] (II) LoadModule: "fb"
[    10.859] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.859] (II) Module fb: vendor="X.Org Foundation"
[    10.859]    compiled for 1.11.3, module version = 1.0.0
[    10.859]    ABI class: X.Org ANSI C Emulation, version 0.4
[    10.859] (II) Loading sub module "ramdac"
[    10.859] (II) LoadModule: "ramdac"
[    10.859] (II) Module "ramdac" already built-in
[    10.859] (--) Depth 24 pixmap format is 32 bpp
[    10.859] (II) DUMMY(0): Using 256 scanlines of offscreen memory
[    10.859] (==) DUMMY(0): Backing store disabled
[    10.859] (==) DUMMY(0): Silken mouse enabled
[    10.859] (==) RandR enabled
[    10.859] (II) Initializing built-in extension Generic Event Extension
[    10.859] (II) Initializing built-in extension SHAPE
[    10.859] (II) Initializing built-in extension MIT-SHM
[    10.859] (II) Initializing built-in extension XInputExtension
[    10.859] (II) Initializing built-in extension XTEST
[    10.859] (II) Initializing built-in extension BIG-REQUESTS
[    10.859] (II) Initializing built-in extension SYNC
[    10.859] (II) Initializing built-in extension XKEYBOARD
[    10.859] (II) Initializing built-in extension XC-MISC
[    10.859] (II) Initializing built-in extension SECURITY
[    10.859] (II) Initializing built-in extension XINERAMA
[    10.859] (II) Initializing built-in extension XFIXES
[    10.859] (II) Initializing built-in extension RENDER
[    10.859] (II) Initializing built-in extension RANDR
[    10.859] (II) Initializing built-in extension COMPOSITE
[    10.859] (II) Initializing built-in extension DAMAGE
[    10.861] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    10.872] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.873] (II) Using input driver 'void' for 'Dummy Input'
[    10.873] (II) Loading /usr/lib/xorg/modules/input/void_drv.so
[    10.873] (**) Dummy Input: always reports core events
[    10.873] (II) XINPUT: Adding extended input device "Dummy Input" (type: Void, id 6)
[    10.873] (**) Dummy Input: (accel) keeping acceleration scheme 1
[    10.873] (**) Dummy Input: (accel) acceleration profile 0
[    10.873] (**) Dummy Input: (accel) acceleration factor: 2.000
[    10.873] (**) Dummy Input: (accel) acceleration threshold: 4
[    10.874] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    10.874] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.874] (II) LoadModule: "evdev"
[    10.874] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.875] (II) Module evdev: vendor="X.Org Foundation"
[    10.875]    compiled for 1.11.3, module version = 2.7.0
[    10.875]    Module class: X.Org XInput Driver
[    10.875]    ABI class: X.Org XInput driver, version 16.0
[    10.875] (II) Using input driver 'evdev' for 'Power Button'
[    10.875] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.875] (**) Power Button: always reports core events
[    10.875] (**) evdev: Power Button: Device: "/dev/input/event1"
[    10.875] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.875] (--) evdev: Power Button: Found keys
[    10.875] (II) evdev: Power Button: Configuring as keyboard
[    10.875] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    10.875] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    10.875] (**) Option "xkb_rules" "evdev"
[    10.875] (**) Option "xkb_model" "pc105"
[    10.875] (**) Option "xkb_layout" "us"
[    10.875] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    10.875] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.875] (II) Using input driver 'evdev' for 'Power Button'
[    10.875] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.875] (**) Power Button: always reports core events
[    10.875] (**) evdev: Power Button: Device: "/dev/input/event0"
[    10.875] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.875] (--) evdev: Power Button: Found keys
[    10.875] (II) evdev: Power Button: Configuring as keyboard
[    10.875] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    10.875] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    10.875] (**) Option "xkb_rules" "evdev"
[    10.875] (**) Option "xkb_model" "pc105"
[    10.875] (**) Option "xkb_layout" "us"
[    10.876] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event2)
[    10.876] (II) No input driver specified, ignoring this device.
[    10.876] (II) This device may have been added with another device file.
[    10.876] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event3)
[    10.876] (II) No input driver specified, ignoring this device.
[    10.876] (II) This device may have been added with another device file.
[    10.876] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event4)
[    10.876] (II) No input driver specified, ignoring this device.
[    10.876] (II) This device may have been added with another device file.
[    10.876] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event5)
[    10.876] (II) No input driver specified, ignoring this device.
[    10.876] (II) This device may have been added with another device file.
[    10.877] (II) config/udev: Adding input device HDA Intel Line-Out Side (/dev/input/event6)
[    10.877] (II) No input driver specified, ignoring this device.
[    10.877] (II) This device may have been added with another device file.
[    10.877] (II) config/udev: Adding input device HDA Intel Line-Out CLFE (/dev/input/event7)
[    10.877] (II) No input driver specified, ignoring this device.
[    10.877] (II) This device may have been added with another device file.
[    10.877] (II) config/udev: Adding input device HDA Intel Line-Out Surround (/dev/input/event8)
[    10.877] (II) No input driver specified, ignoring this device.
[    10.877] (II) This device may have been added with another device file.
[    10.877] (II) config/udev: Adding input device HDA Intel Line-Out Front (/dev/input/event9)
[    10.877] (II) No input driver specified, ignoring this device.
[    10.877] (II) This device may have been added with another device file.

```

lightdm.log:

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1412
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for automatic login as user dannyb
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: X server :0 will replace Plymouth
[+0.03s] DEBUG: Using VT 7
[+0.03s] DEBUG: Activating VT 7
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1467: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.09s] DEBUG: Got signal 10 from process 1467
[+0.09s] DEBUG: Got signal from X server :0
[+0.09s] DEBUG: Stopping Plymouth, X server is ready
[+0.11s] DEBUG: Connecting to XServer :0
[+0.11s] DEBUG: Automatically logging in user dannyb
[+0.11s] DEBUG: Started session 1581 with service 'lightdm-autologin', username 'dannyb'
[+0.22s] DEBUG: Session 1581 authentication complete with return value 0: Success
[+0.22s] DEBUG: Autologin user dannyb authorized
[+0.23s] DEBUG: Autologin using session mythbuntu
[+0.28s] DEBUG: Dropping privileges to uid 1000
[+0.37s] DEBUG: Restoring privileges
[+0.38s] DEBUG: Dropping privileges to uid 1000
[+0.38s] DEBUG: Writing /home/dannyb/.dmrc
[+0.40s] DEBUG: Restoring privileges
[+0.42s] DEBUG: Starting session mythbuntu as user dannyb
[+0.42s] DEBUG: Session 1581 running command /usr/sbin/lightdm-session /usr/share/mythbuntu/session.sh
[+0.47s] DEBUG: New display ready, switching to it
[+0.47s] DEBUG: Activating VT 7
[+0.47s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+0.47s] DEBUG: Session 1581 exited with return value 1
[+0.47s] DEBUG: User session quit
[+0.47s] DEBUG: Stopping display
[+0.47s] DEBUG: Sending signal 15 to process 1467
[+0.53s] DEBUG: Process 1467 exited with return value 0
[+0.53s] DEBUG: X server stopped
[+0.53s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.53s] DEBUG: Releasing VT 7
[+0.53s] DEBUG: Display server stopped
[+0.53s] DEBUG: Display stopped
[+0.53s] DEBUG: Active display stopped, switching to greeter
[+0.53s] DEBUG: Switching to greeter
[+0.53s] DEBUG: Starting new display for greeter
[+0.53s] DEBUG: Starting local X display
[+0.53s] DEBUG: Using VT 7
[+0.53s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.53s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.53s] DEBUG: Launching X Server
[+0.53s] DEBUG: Launching process 1813: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.53s] DEBUG: Waiting for ready signal from X server :0
[+0.58s] DEBUG: Got signal 10 from process 1813
[+0.58s] DEBUG: Got signal from X server :0
[+0.58s] DEBUG: Connecting to XServer :0
[+0.58s] DEBUG: Starting greeter
[+0.58s] DEBUG: Started session 1861 with service 'lightdm', username 'lightdm'
[+0.60s] DEBUG: Session 1861 authentication complete with return value 0: Success
[+0.60s] DEBUG: Greeter authorized
[+0.60s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+0.60s] DEBUG: Session 1861 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+0.74s] DEBUG: Greeter connected version=1.2.3
[+0.74s] DEBUG: Greeter connected, display is ready
[+0.74s] DEBUG: New display ready, switching to it
[+0.74s] DEBUG: Activating VT 7
[+0.74s] DEBUG: Stopping greeter display being switched from
[+1.05s] DEBUG: Greeter start authentication for dannyb
[+1.05s] DEBUG: Started session 2194 with service 'lightdm', username 'dannyb'
[+1.10s] DEBUG: Session 2194 got 1 message(s) from PAM
[+1.10s] DEBUG: Prompt greeter with 1 message(s)

```


.xsession-errors:

```
08/02/2013 16:32:51 passing arg to libvncserver: -rfbauth
08/02/2013 16:32:51 passing arg to libvncserver: /home/dannyb/.vnc/passwd
08/02/2013 16:32:51 passing arg to libvncserver: -rfbport
08/02/2013 16:32:51 passing arg to libvncserver: 5900
08/02/2013 16:32:51 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 2131
08/02/2013 16:32:51 Using X display :0
08/02/2013 16:32:51 rootwin: 0x2a5 reswin: 0x800001 dpy: 0x95ce6c0
08/02/2013 16:32:51
08/02/2013 16:32:51 ------------------ USEFUL INFORMATION ------------------
08/02/2013 16:32:51 X DAMAGE available on display, using it for polling hints.
08/02/2013 16:32:51   To disable this behavior use: '-noxdamage'
08/02/2013 16:32:51
08/02/2013 16:32:51   Most compositing window managers like 'compiz' or 'beryl'
08/02/2013 16:32:51   cause X DAMAGE to fail, and so you may not see any screen
08/02/2013 16:32:51   updates via VNC.  Either disable 'compiz' (recommended) or
08/02/2013 16:32:51   supply the x11vnc '-noxdamage' command line option.
08/02/2013 16:32:51
08/02/2013 16:32:51 XFIXES available on display, resetting cursor mode
08/02/2013 16:32:51   to: '-cursor most'.
08/02/2013 16:32:51   to disable this behavior use: '-cursor arrow'
08/02/2013 16:32:51   or '-noxfixes'.
08/02/2013 16:32:51 using XFIXES for cursor drawing.
08/02/2013 16:32:51 GrabServer control via XTEST.
08/02/2013 16:32:51
08/02/2013 16:32:51 Scroll Detection: -scrollcopyrect mode is in effect to
08/02/2013 16:32:51   use RECORD extension to try to detect scrolling windows
08/02/2013 16:32:51   (induced by either user keystroke or mouse input).
08/02/2013 16:32:51   If this yields undesired behavior (poor response, painting
08/02/2013 16:32:51   errors, etc) it may be disabled via: '-noscr'
08/02/2013 16:32:51   Also see the -help entry for tuning parameters.
08/02/2013 16:32:51   You can press 3 Alt_L's (Left "Alt" key) in a row to
08/02/2013 16:32:51   repaint the screen, also see the -fixscreen option for
08/02/2013 16:32:51   periodic repaints.
08/02/2013 16:32:51 X FBPM extension not supported.
08/02/2013 16:32:51 X display is capable of DPMS.
08/02/2013 16:32:51 --------------------------------------------------------
08/02/2013 16:32:51
08/02/2013 16:32:51 Default visual ID: 0x21
08/02/2013 16:32:51 Read initial data from X display into framebuffer.
08/02/2013 16:32:51 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
08/02/2013 16:32:51
08/02/2013 16:32:51 X display :0 is 32bpp depth=24 true color
08/02/2013 16:32:51 WARNING: all TrueColor RGB masks are zero!
08/02/2013 16:32:51 WARNING: cooking something up for VNC fb...  B=8 M=255
 red_mask:   0x00ff0000  00000000111111110000000000000000
 green_mask: 0x0000ff00  00000000000000001111111100000000
 blue_mask:  0x000000ff  00000000000000000000000011111111
08/02/2013 16:32:51
08/02/2013 16:32:51 Listening for VNC connections on TCP port 5900
08/02/2013 16:32:51 Listening also on IPv6 port 5900 (socket 11)
08/02/2013 16:32:51 fb read rate: 915 MB/sec
08/02/2013 16:32:51 fast read: reset wait  ms to: 10
08/02/2013 16:32:51 fast read: reset defer ms to: 10
08/02/2013 16:32:51 The X server says there are 10 mouse buttons.
08/02/2013 16:32:51 screen setup finished.
08/02/2013 16:32:51

The VNC desktop is:      raidman:0

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching


(xfce4-settings-helper:2544): xfce4-settings-helper-CRITICAL **: Stored Xfconf properties disable all outputs, aborting.
xfce4-settings-helper: Another instance is already running. Leaving...

(polkit-gnome-authentication-agent-1:2559): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:2559): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
env: chromium-browser: No such file or directory
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32          use a 32-bit data model if available
    -d64          use a 64-bit data model if available
    -client       to select the "client" VM
    -server       to select the "server" VM
    -jamvm        to select the "jamvm" VM
    -cacao        to select the "cacao" VM
    -zero         to select the "zero" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is server,
                  because you are running on a server-class machine.


    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions with specified granularity
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions with specified granularity
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                  see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
See http://java.sun.com/javase/reference for more details.
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area
WARNING:root:timeout reached, exiting

(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint


(update-manager:12122): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
xfwm4: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
xfce4-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Thunar: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
xfdesktop: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(update-notifier:2579): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


(polkit-gnome-authentication-agent-1:2559): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

wrapper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(update-manager:12122): Gdk-WARNING **: update-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

xfce4-settings-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-terminal: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(nm-applet:2548): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


```

Sorry for the plethora of logs. I don't know which information is pertinent. I've been at this for a couple of hours now without any luck. Any recommendations would be appreciated. Thanks.

 - dan

---

### Post by brg7 on 2013-04-09
Sounds a lot like my issue: [http://ubuntuforums.org/showthread.php?t=2133492&p=12595092](http://ubuntuforums.org/showthread.php?t=2133492&p=12595092) - did you ever find a solution?

---

