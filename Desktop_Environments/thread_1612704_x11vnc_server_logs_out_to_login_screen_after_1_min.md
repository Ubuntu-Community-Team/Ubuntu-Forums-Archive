---
title: "x11vnc server logs out to login screen after 1 minute"
date: 2010-11-03
forum: Desktop Environments
---

### Post by nLinked on 2010-11-03
I have x11vnc server set up on my desktop PC. I can boot the computer and connect at the login screen if I want to. I can login to my computer as usual. But after about 1 minute of logging in, the computer logs off as if pressing Ctrl+Alt+Backspace and returns me to the login screen. This cycle repeats when I login and I have to kill the x11vnc process or remove the command from /etc/gdm/Init/Default.

Have tried so many things now but the end result is the same.

I have Ubuntu 10.10 fully updated and x11vnc 9.10-1 from the default repos.

I am using the following command in the /etc/gdm/Init/Default file:
```
/usr/bin/x11vnc -rfbauth ~/.vnc/passwd -rfbport 5901 -display :0 -forever -bg
```

I don't think it matters now whether I add **KillInitClients=false** into **/etc/gdm/gdm.conf-custom** or **/etc/gdm/gdm.conf** because of the x11vnc version I have. The manual says its not really needed. But I have tried this too with no better luck.

The computer will still log me out after about a minute of logging in. It can be between 1 min to 1.5 mins.

Running out of ideas and have tried the -noxfixes and -reopen commands.

Why does x11vnc crash out (or it may be gdm or x server?) after about a minute of logging in? If I am currently viewing my desktop through VNC viewer on another computer, it will still crash out after 1 min of log in, and lose the connection. I can reconnect through VNC again but I have to log back in to the remote computer and it will just log out after another minute.

**EDIT: SOLVED!!**

Maybe this will help someone.

At last, in 2 days I have finally solved it. As simple as creating my own version. The x11vnc 9.10-1 version my default Ubuntu 10.10 repos is buggy. Here's my fix (I used [this site]("http://www.karlrunge.com/x11vnc/#downloading")):

1. Downloaded latest x11vnc dev build from above site (x11vnc-0.9.13-dev.tar.gz at time of posting)
2. Extract it
3. Open Terminal > sudo -s > enter admin password
4. **cd LocationOfExtracted** folder
5. ./configure
6. Wait a while for above command to finish
7. Type in **make**, press enter
8. Wait to complete
9. When done it will make a folder in that extracted folder called x11vnc, and in there is a file called x11vnc.

This is the new binary I use. So replace the old one in /usr/bin/.

Sorted!

**EDIT 2: Not solved!**
Problem returns! When building x11vnc in Edit 1 above, during the ./configure bit, it said I should have libxtst-dev installed or mouse clicks and keyboard input won't work. So I installed libxtst-dev through Synaptic and recompiled x11vnc again.

When using this new x11vnc binary, the problem returned!!

So it is libxtst-dev causing the problem. If I remove libxtst-dev and compile x11vnc, everything works fine, but then I don't get input.

Stuck yet again! Need input!

**EDIT 3: SOLVED!**
Post #15 [here]("http://ubuntuforums.org/showpost.php?p=10082455&postcount=15") (same thread) fixes this issue.

---

### Post by krunge on 2010-11-03
Reproduce the problem, I suggest using the x11vnc 0.9.10 in the repos, and collect a log file (-o x11vnc option) and attach the log here.

Also examine /var/log/Xorg.log and /var/log/Xorg.log.old for errors.  From your description it sounds like your X server is crashing. Attach it here if you want to. There are lots of bugs in the Xorg X server that x11vnc can trigger (but I thought all of them were worked around in the 0.9.13 dev tarball...)

---

### Post by nLinked on 2010-11-04
> **krunge said:**
> Reproduce the problem, I suggest using the x11vnc 0.9.10 in the repos, and collect a log file (-o x11vnc option) and attach the log here.

Also examine /var/log/Xorg.log and /var/log/Xorg.log.old for errors.  From your description it sounds like your X server is crashing. Attach it here if you want to. There are lots of bugs in the Xorg X server that x11vnc can trigger (but I thought all of them were worked around in the 0.9.13 dev tarball...)

OK have installed x11vnc 0.9.10 from normal Ubuntu repos and removed my custom 0.9.13 binary.

I added the log command to the command I am using for x11vnc. Here is the full command I used in /etc/gdm/Init/Default: ```
/usr/bin/x11vnc -rfbauth /root/.vnc/passwd -rfbport 5901 -oa /var/log/x11vnc.log -forever -bg
```

When I logged into my user account, x11vnc was running successfully as a process. After about 1 minute, it logged me out again and returned to the login screen. x11vnc continued to run on the login screen because I could connect from another computer. I logged in again and checked the log file for why it logged me out. Here is the output in the log file at the exact point it logged me out: ```
caught XIO error:
04/11/2010 18:24:15 deleted 45 tile_row polling images.
```

Everything after this part of the log is just x11vnc process starting again at the login screen.

---

### Post by krunge on 2010-11-04
I believe your X server is crashing.  Do you see it in /var/log/Xorg.0.log and/or /var/log/Xorg.0.log.old?

---

### Post by nLinked on 2010-11-04
> **krunge said:**
> I believe your X server is crashing.  Do you see it in /var/log/Xorg.0.log and/or /var/log/Xorg.0.log.old?

2 things to note. Everything is fine and the crash to the login screen after about a minute doesn't happen if I do any of these two:
- I run the x11vnc... command from terminal after logging in (i.e not using the /etc/gdm/Init/Default file)
- or, if I compile my own binary with the 9.13-dev, but don't install the libxtst-dev package (which then disables any remote input), and then let the /etc/gdm/Init/Default file run the command.

In either of the above two scenarios, all is OK. But of course its not ideal because then I'm either going to not have connectivity at the login screen, or no remote input.

A new symptom discovered: When the crash to the login screen happens, when I log back in, the "compiz" process is taking nearly 100% CPU on one core (have a quad core). Don't know how significant this is at this point.

Also, when I log back in after the crash to login screen, there is some artificating at the top of the screen, like little black tiny rectangles. These go if I terminate the x11vnc process.

Not sure how to read the X logs. Here's Xorg.0.log: ```
[   159.787] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   159.787] X Protocol Version 11, Revision 0
[   159.787] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   159.787] Current Operating System: Linux 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[   159.787] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a4801d69-0ec7-4ab3-9598-c493c0851543 ro splash vga=799 quiet quiet splash
[   159.787] Build Date: 16 September 2010  05:39:22PM
[   159.787] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   159.787] Current version of pixman: 0.18.4
[   159.787] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   159.787] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   159.787] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  4 20:29:04 2010
[   159.787] (==) Using config file: "/etc/X11/xorg.conf"
[   159.787] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   159.787] (==) ServerLayout "Layout0"
[   159.787] (**) |-->Screen "Screen0" (0)
[   159.787] (**) |   |-->Monitor "Monitor0"
[   159.787] (**) |   |-->Device "Device0"
[   159.787] (**) |-->Input Device "Keyboard0"
[   159.787] (**) |-->Input Device "Mouse0"
[   159.787] (**) Option "Xinerama" "0"
[   159.787] (==) Automatically adding devices
[   159.787] (==) Automatically enabling devices
[   159.788] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   159.788] 	Entry deleted from font path.
[   159.788] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   159.788] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   159.788] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   159.788] (WW) Disabling Keyboard0
[   159.788] (WW) Disabling Mouse0
[   159.788] (II) Loader magic: 0x81f8e00
[   159.788] (II) Module ABI versions:
[   159.788] 	X.Org ANSI C Emulation: 0.4
[   159.788] 	X.Org Video Driver: 8.0
[   159.788] 	X.Org XInput driver : 11.0
[   159.788] 	X.Org Server Extension : 4.0
[   159.788] (--) PCI:*(0:1:0:0) 10de:05e2:10de:0585 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[   159.788] (II) Open ACPI successful (/var/run/acpid.socket)
[   159.788] (II) LoadModule: "extmod"
[   159.789] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   159.789] (II) Module extmod: vendor="X.Org Foundation"
[   159.789] 	compiled for 1.9.0, module version = 1.0.0
[   159.789] 	Module class: X.Org Server Extension
[   159.789] 	ABI class: X.Org Server Extension, version 4.0
[   159.789] (II) Loading extension MIT-SCREEN-SAVER
[   159.789] (II) Loading extension XFree86-VidModeExtension
[   159.789] (II) Loading extension XFree86-DGA
[   159.789] (II) Loading extension DPMS
[   159.789] (II) Loading extension XVideo
[   159.789] (II) Loading extension XVideo-MotionCompensation
[   159.789] (II) Loading extension X-Resource
[   159.789] (II) LoadModule: "dbe"
[   159.789] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   159.789] (II) Module dbe: vendor="X.Org Foundation"
[   159.789] 	compiled for 1.9.0, module version = 1.0.0
[   159.789] 	Module class: X.Org Server Extension
[   159.789] 	ABI class: X.Org Server Extension, version 4.0
[   159.789] (II) Loading extension DOUBLE-BUFFER
[   159.789] (II) LoadModule: "glx"
[   159.789] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   159.801] (II) Module glx: vendor="NVIDIA Corporation"
[   159.801] 	compiled for 4.0.2, module version = 1.0.0
[   159.801] 	Module class: X.Org Server Extension
[   159.801] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[   159.801] (II) Loading extension GLX
[   159.801] (II) LoadModule: "record"
[   159.801] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   159.801] (II) Module record: vendor="X.Org Foundation"
[   159.801] 	compiled for 1.9.0, module version = 1.13.0
[   159.801] 	Module class: X.Org Server Extension
[   159.801] 	ABI class: X.Org Server Extension, version 4.0
[   159.801] (II) Loading extension RECORD
[   159.801] (II) LoadModule: "dri"
[   159.802] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   159.802] (II) Module dri: vendor="X.Org Foundation"
[   159.802] 	compiled for 1.9.0, module version = 1.0.0
[   159.802] 	ABI class: X.Org Server Extension, version 4.0
[   159.802] (II) Loading extension XFree86-DRI
[   159.802] (II) LoadModule: "dri2"
[   159.802] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   159.802] (II) Module dri2: vendor="X.Org Foundation"
[   159.802] 	compiled for 1.9.0, module version = 1.2.0
[   159.802] 	ABI class: X.Org Server Extension, version 4.0
[   159.802] (II) Loading extension DRI2
[   159.802] (II) LoadModule: "nvidia"
[   159.802] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   159.802] (II) Module nvidia: vendor="NVIDIA Corporation"
[   159.802] 	compiled for 4.0.2, module version = 1.0.0
[   159.802] 	Module class: X.Org Video Driver
[   159.802] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[   159.802] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   160.651] (--) using VT number 8

[   160.938] (II) Loading sub module "fb"
[   160.938] (II) LoadModule: "fb"
[   160.938] (II) Loading /usr/lib/xorg/modules/libfb.so
[   160.938] (II) Module fb: vendor="X.Org Foundation"
[   160.938] 	compiled for 1.9.0, module version = 1.0.0
[   160.938] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   160.938] (II) Loading sub module "wfb"
[   160.938] (II) LoadModule: "wfb"
[   160.939] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   160.939] (II) Module wfb: vendor="X.Org Foundation"
[   160.939] 	compiled for 1.9.0, module version = 1.0.0
[   160.939] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   160.939] (II) Loading sub module "ramdac"
[   160.939] (II) LoadModule: "ramdac"
[   160.939] (II) Module "ramdac" already built-in
[   160.939] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   160.939] (==) NVIDIA(0): RGB weight 888
[   160.939] (==) NVIDIA(0): Default visual is TrueColor
[   160.939] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   160.939] (**) NVIDIA(0): Option "TwinView" "0"
[   160.939] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[   160.939] (**) NVIDIA(0): Enabling RENDER acceleration
[   160.940] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   160.940] (II) NVIDIA(0):     enabled.
[   161.770] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[   161.770] (--) NVIDIA(0): Memory: 917504 kBytes
[   161.770] (--) NVIDIA(0): VideoBIOS: 62.00.0e.00.04
[   161.770] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   161.770] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   161.770] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0
[   161.770] (--) NVIDIA(0):     DELL 2707WFP (DFP-1)
[   161.770] (--) NVIDIA(0): DELL 2707WFP (DFP-1): 330.0 MHz maximum pixel clock
[   161.770] (--) NVIDIA(0): DELL 2707WFP (DFP-1): Internal Dual Link TMDS
[   161.856] (II) NVIDIA(0): Assigned Display Device: DFP-1
[   161.856] (II) NVIDIA(0): Validated modes:
[   161.856] (II) NVIDIA(0):     "1440x900+0+0"
[   161.856] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[   161.890] (--) NVIDIA(0): DPI set to (63, 63); computed from "UseEdidDpi" X config
[   161.890] (--) NVIDIA(0):     option
[   161.890] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   161.890] (--) Depth 24 pixmap format is 32 bpp
[   161.890] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   161.892] (II) NVIDIA(0): Initialized GPU GART.
[   161.900] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[   161.938] (II) Loading extension NV-GLX
[   161.968] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   161.976] (==) NVIDIA(0): Disabling shared memory pixmaps
[   161.976] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   161.976] (==) NVIDIA(0): Backing store disabled
[   161.976] (==) NVIDIA(0): Silken mouse enabled
[   161.989] (**) NVIDIA(0): DPMS enabled
[   161.989] (II) Loading extension NV-CONTROL
[   161.989] (II) Loading extension XINERAMA
[   161.989] (II) Loading sub module "dri2"
[   161.989] (II) LoadModule: "dri2"
[   161.989] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   161.989] (II) NVIDIA(0): [DRI2] Setup complete
[   161.989] (==) RandR enabled
[   161.989] (II) Initializing built-in extension Generic Event Extension
[   161.989] (II) Initializing built-in extension SHAPE
[   161.989] (II) Initializing built-in extension MIT-SHM
[   161.989] (II) Initializing built-in extension XInputExtension
[   161.989] (II) Initializing built-in extension XTEST
[   161.989] (II) Initializing built-in extension BIG-REQUESTS
[   161.989] (II) Initializing built-in extension SYNC
[   161.989] (II) Initializing built-in extension XKEYBOARD
[   161.989] (II) Initializing built-in extension XC-MISC
[   161.989] (II) Initializing built-in extension SECURITY
[   161.989] (II) Initializing built-in extension XINERAMA
[   161.989] (II) Initializing built-in extension XFIXES
[   161.989] (II) Initializing built-in extension RENDER
[   161.989] (II) Initializing built-in extension RANDR
[   161.989] (II) Initializing built-in extension COMPOSITE
[   161.989] (II) Initializing built-in extension DAMAGE
[   161.989] (II) Initializing built-in extension GESTURE
[   161.991] (II) Initializing extension GLX
[   162.015] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   162.020] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   162.020] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   162.020] (II) LoadModule: "evdev"
[   162.020] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   162.021] (II) Module evdev: vendor="X.Org Foundation"
[   162.021] 	compiled for 1.9.0, module version = 2.3.2
[   162.021] 	Module class: X.Org XInput Driver
[   162.021] 	ABI class: X.Org XInput driver, version 11.0
[   162.021] (**) Power Button: always reports core events
[   162.021] (**) Power Button: Device: "/dev/input/event1"
[   162.052] (II) Power Button: Found keys
[   162.052] (II) Power Button: Configuring as keyboard
[   162.052] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   162.052] (**) Option "xkb_rules" "evdev"
[   162.052] (**) Option "xkb_model" "evdev"
[   162.052] (**) Option "xkb_layout" "gb"
[   162.056] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[   162.059] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   162.059] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   162.059] (**) Power Button: always reports core events
[   162.059] (**) Power Button: Device: "/dev/input/event0"
[   162.084] (II) Power Button: Found keys
[   162.084] (II) Power Button: Configuring as keyboard
[   162.084] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   162.084] (**) Option "xkb_rules" "evdev"
[   162.084] (**) Option "xkb_model" "evdev"
[   162.084] (**) Option "xkb_layout" "gb"
[   162.086] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[   162.087] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   162.087] (**) Logitech USB Receiver: always reports core events
[   162.087] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[   162.116] (II) Logitech USB Receiver: Found keys
[   162.116] (II) Logitech USB Receiver: Configuring as keyboard
[   162.116] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   162.116] (**) Option "xkb_rules" "evdev"
[   162.116] (**) Option "xkb_model" "evdev"
[   162.116] (**) Option "xkb_layout" "gb"
[   162.118] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[   162.118] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[   162.118] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   162.118] (**) Logitech USB Receiver: always reports core events
[   162.118] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[   162.148] (II) Logitech USB Receiver: Found 20 mouse buttons
[   162.148] (II) Logitech USB Receiver: Found scroll wheel(s)
[   162.148] (II) Logitech USB Receiver: Found relative axes
[   162.148] (II) Logitech USB Receiver: Found x and y relative axes
[   162.148] (II) Logitech USB Receiver: Found absolute axes
[   162.148] (II) evdev-grail: failed to open grail, no gesture support
[   162.148] (II) Logitech USB Receiver: Found keys
[   162.148] (II) Logitech USB Receiver: Configuring as mouse
[   162.148] (II) Logitech USB Receiver: Configuring as keyboard
[   162.148] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   162.148] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   162.148] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   162.148] (**) Option "xkb_rules" "evdev"
[   162.148] (**) Option "xkb_model" "evdev"
[   162.148] (**) Option "xkb_layout" "gb"
[   162.149] (II) Logitech USB Receiver: initialized for relative axes.
[   162.149] (WW) Logitech USB Receiver: ignoring absolute axes.
[   162.150] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[   162.150] (II) No input driver/identifier specified (ignoring)
[   162.152] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event6)
[   162.152] (II) No input driver/identifier specified (ignoring)
[   162.152] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[   162.153] (II) No input driver/identifier specified (ignoring)
[   162.153] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse2)
[   162.153] (II) No input driver/identifier specified (ignoring)
[   162.153] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event7)
[   162.153] (II) No input driver/identifier specified (ignoring)
[   162.154] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[   162.154] (II) No input driver/identifier specified (ignoring)
[   162.154] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse3)
[   162.154] (II) No input driver/identifier specified (ignoring)
[   162.155] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event8)
[   162.155] (II) No input driver/identifier specified (ignoring)
[   162.155] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[   162.155] (II) No input driver/identifier specified (ignoring)
[   162.156] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse4)
[   162.156] (II) No input driver/identifier specified (ignoring)
[   162.156] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event9)
[   162.156] (II) No input driver/identifier specified (ignoring)
[   162.157] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[   162.157] (II) No input driver/identifier specified (ignoring)
[   162.157] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse5)
[   162.157] (II) No input driver/identifier specified (ignoring)
[   162.161] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[   162.161] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   162.161] (**) Logitech USB Receiver: always reports core events
[   162.161] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[   162.180] (II) Logitech USB Receiver: Found keys
[   162.180] (II) Logitech USB Receiver: Configuring as keyboard
[   162.180] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   162.180] (**) Option "xkb_rules" "evdev"
[   162.180] (**) Option "xkb_model" "evdev"
[   162.180] (**) Option "xkb_layout" "gb"
[   162.181] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[   162.183] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[   162.183] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[   162.183] (**) Logitech USB Receiver: always reports core events
[   162.183] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[   162.212] (II) Logitech USB Receiver: Found 20 mouse buttons
[   162.212] (II) Logitech USB Receiver: Found scroll wheel(s)
[   162.212] (II) Logitech USB Receiver: Found relative axes
[   162.212] (II) Logitech USB Receiver: Found x and y relative axes
[   162.212] (II) Logitech USB Receiver: Found absolute axes
[   162.212] (II) evdev-grail: failed to open grail, no gesture support
[   162.212] (II) Logitech USB Receiver: Found keys
[   162.212] (II) Logitech USB Receiver: Configuring as mouse
[   162.212] (II) Logitech USB Receiver: Configuring as keyboard
[   162.212] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[   162.212] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   162.212] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[   162.212] (**) Option "xkb_rules" "evdev"
[   162.212] (**) Option "xkb_model" "evdev"
[   162.212] (**) Option "xkb_layout" "gb"
[   162.212] (II) Logitech USB Receiver: initialized for relative axes.
[   162.212] (WW) Logitech USB Receiver: ignoring absolute axes.
[   162.213] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[   162.213] (II) No input driver/identifier specified (ignoring)
```

Here's /var/log/Xorg.0.log.old: ```
[    15.248] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.248] X Protocol Version 11, Revision 0
[    15.248] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    15.248] Current Operating System: Linux 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    15.248] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a4801d69-0ec7-4ab3-9598-c493c0851543 ro splash vga=799 quiet quiet splash
[    15.248] Build Date: 16 September 2010  05:39:22PM
[    15.248] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    15.248] Current version of pixman: 0.18.4
[    15.248] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.248] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.248] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  4 20:26:39 2010
[    15.248] (==) Using config file: "/etc/X11/xorg.conf"
[    15.248] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.248] (==) ServerLayout "Layout0"
[    15.248] (**) |-->Screen "Screen0" (0)
[    15.248] (**) |   |-->Monitor "Monitor0"
[    15.248] (**) |   |-->Device "Device0"
[    15.248] (**) |-->Input Device "Keyboard0"
[    15.248] (**) |-->Input Device "Mouse0"
[    15.248] (**) Option "Xinerama" "0"
[    15.248] (==) Automatically adding devices
[    15.248] (==) Automatically enabling devices
[    15.249] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.249] 	Entry deleted from font path.
[    15.249] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.249] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.249] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.249] (WW) Disabling Keyboard0
[    15.249] (WW) Disabling Mouse0
[    15.249] (II) Loader magic: 0x81f8e00
[    15.249] (II) Module ABI versions:
[    15.249] 	X.Org ANSI C Emulation: 0.4
[    15.249] 	X.Org Video Driver: 8.0
[    15.249] 	X.Org XInput driver : 11.0
[    15.249] 	X.Org Server Extension : 4.0
[    15.249] (--) PCI:*(0:1:0:0) 10de:05e2:10de:0585 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    15.249] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    15.249] (II) LoadModule: "extmod"
[    15.267] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.267] (II) Module extmod: vendor="X.Org Foundation"
[    15.267] 	compiled for 1.9.0, module version = 1.0.0
[    15.267] 	Module class: X.Org Server Extension
[    15.267] 	ABI class: X.Org Server Extension, version 4.0
[    15.267] (II) Loading extension MIT-SCREEN-SAVER
[    15.267] (II) Loading extension XFree86-VidModeExtension
[    15.267] (II) Loading extension XFree86-DGA
[    15.267] (II) Loading extension DPMS
[    15.267] (II) Loading extension XVideo
[    15.267] (II) Loading extension XVideo-MotionCompensation
[    15.268] (II) Loading extension X-Resource
[    15.268] (II) LoadModule: "dbe"
[    15.268] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.268] (II) Module dbe: vendor="X.Org Foundation"
[    15.268] 	compiled for 1.9.0, module version = 1.0.0
[    15.268] 	Module class: X.Org Server Extension
[    15.268] 	ABI class: X.Org Server Extension, version 4.0
[    15.268] (II) Loading extension DOUBLE-BUFFER
[    15.268] (II) LoadModule: "glx"
[    15.268] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.279] (II) Module glx: vendor="NVIDIA Corporation"
[    15.279] 	compiled for 4.0.2, module version = 1.0.0
[    15.279] 	Module class: X.Org Server Extension
[    15.279] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    15.279] (II) Loading extension GLX
[    15.279] (II) LoadModule: "record"
[    15.280] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.280] (II) Module record: vendor="X.Org Foundation"
[    15.280] 	compiled for 1.9.0, module version = 1.13.0
[    15.280] 	Module class: X.Org Server Extension
[    15.280] 	ABI class: X.Org Server Extension, version 4.0
[    15.280] (II) Loading extension RECORD
[    15.280] (II) LoadModule: "dri"
[    15.280] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.280] (II) Module dri: vendor="X.Org Foundation"
[    15.280] 	compiled for 1.9.0, module version = 1.0.0
[    15.280] 	ABI class: X.Org Server Extension, version 4.0
[    15.280] (II) Loading extension XFree86-DRI
[    15.280] (II) LoadModule: "dri2"
[    15.280] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.280] (II) Module dri2: vendor="X.Org Foundation"
[    15.280] 	compiled for 1.9.0, module version = 1.2.0
[    15.280] 	ABI class: X.Org Server Extension, version 4.0
[    15.280] (II) Loading extension DRI2
[    15.280] (II) LoadModule: "nvidia"
[    15.280] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.281] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.281] 	compiled for 4.0.2, module version = 1.0.0
[    15.281] 	Module class: X.Org Video Driver
[    15.281] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[    15.281] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.281] (++) using VT number 7

[    15.281] (II) Loading sub module "fb"
[    15.281] (II) LoadModule: "fb"
[    15.281] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.281] (II) Module fb: vendor="X.Org Foundation"
[    15.281] 	compiled for 1.9.0, module version = 1.0.0
[    15.281] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.281] (II) Loading sub module "wfb"
[    15.281] (II) LoadModule: "wfb"
[    15.281] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.281] (II) Module wfb: vendor="X.Org Foundation"
[    15.281] 	compiled for 1.9.0, module version = 1.0.0
[    15.281] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.281] (II) Loading sub module "ramdac"
[    15.281] (II) LoadModule: "ramdac"
[    15.281] (II) Module "ramdac" already built-in
[    15.281] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    15.281] (==) NVIDIA(0): RGB weight 888
[    15.281] (==) NVIDIA(0): Default visual is TrueColor
[    15.281] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.281] (**) NVIDIA(0): Option "TwinView" "0"
[    15.281] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[    15.281] (**) NVIDIA(0): Enabling RENDER acceleration
[    15.282] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    15.282] (II) NVIDIA(0):     enabled.
[    16.576] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[    16.576] (--) NVIDIA(0): Memory: 917504 kBytes
[    16.576] (--) NVIDIA(0): VideoBIOS: 62.00.0e.00.04
[    16.576] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    16.576] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    16.576] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0
[    16.576] (--) NVIDIA(0):     DELL 2707WFP (DFP-1)
[    16.576] (--) NVIDIA(0): DELL 2707WFP (DFP-1): 330.0 MHz maximum pixel clock
[    16.576] (--) NVIDIA(0): DELL 2707WFP (DFP-1): Internal Dual Link TMDS
[    16.662] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    16.662] (II) NVIDIA(0): Validated modes:
[    16.662] (II) NVIDIA(0):     "1440x900+0+0"
[    16.662] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    16.697] (--) NVIDIA(0): DPI set to (63, 63); computed from "UseEdidDpi" X config
[    16.697] (--) NVIDIA(0):     option
[    16.697] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    16.698] (--) Depth 24 pixmap format is 32 bpp
[    16.698] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    16.699] (II) NVIDIA(0): Initialized GPU GART.
[    16.706] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[    16.743] (II) Loading extension NV-GLX
[    16.772] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    16.780] (==) NVIDIA(0): Disabling shared memory pixmaps
[    16.780] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    16.780] (==) NVIDIA(0): Backing store disabled
[    16.780] (==) NVIDIA(0): Silken mouse enabled
[    16.793] (**) NVIDIA(0): DPMS enabled
[    16.793] (II) Loading extension NV-CONTROL
[    16.793] (II) Loading extension XINERAMA
[    16.793] (II) Loading sub module "dri2"
[    16.793] (II) LoadModule: "dri2"
[    16.793] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.793] (II) NVIDIA(0): [DRI2] Setup complete
[    16.793] (==) RandR enabled
[    16.793] (II) Initializing built-in extension Generic Event Extension
[    16.793] (II) Initializing built-in extension SHAPE
[    16.793] (II) Initializing built-in extension MIT-SHM
[    16.793] (II) Initializing built-in extension XInputExtension
[    16.793] (II) Initializing built-in extension XTEST
[    16.793] (II) Initializing built-in extension BIG-REQUESTS
[    16.793] (II) Initializing built-in extension SYNC
[    16.793] (II) Initializing built-in extension XKEYBOARD
[    16.793] (II) Initializing built-in extension XC-MISC
[    16.793] (II) Initializing built-in extension SECURITY
[    16.793] (II) Initializing built-in extension XINERAMA
[    16.793] (II) Initializing built-in extension XFIXES
[    16.793] (II) Initializing built-in extension RENDER
[    16.793] (II) Initializing built-in extension RANDR
[    16.793] (II) Initializing built-in extension COMPOSITE
[    16.793] (II) Initializing built-in extension DAMAGE
[    16.793] (II) Initializing built-in extension GESTURE
[    16.795] (II) Initializing extension GLX
[    16.819] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.825] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.825] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.825] (II) LoadModule: "evdev"
[    16.825] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.825] (II) Module evdev: vendor="X.Org Foundation"
[    16.825] 	compiled for 1.9.0, module version = 2.3.2
[    16.825] 	Module class: X.Org XInput Driver
[    16.825] 	ABI class: X.Org XInput driver, version 11.0
[    16.825] (**) Power Button: always reports core events
[    16.825] (**) Power Button: Device: "/dev/input/event1"
[    16.836] (II) Power Button: Found keys
[    16.836] (II) Power Button: Configuring as keyboard
[    16.836] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.836] (**) Option "xkb_rules" "evdev"
[    16.836] (**) Option "xkb_model" "evdev"
[    16.836] (**) Option "xkb_layout" "gb"
[    16.838] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[    16.839] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.839] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.839] (**) Power Button: always reports core events
[    16.839] (**) Power Button: Device: "/dev/input/event0"
[    16.848] (II) Power Button: Found keys
[    16.848] (II) Power Button: Configuring as keyboard
[    16.848] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.848] (**) Option "xkb_rules" "evdev"
[    16.848] (**) Option "xkb_model" "evdev"
[    16.848] (**) Option "xkb_layout" "gb"
[    16.849] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    16.849] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.849] (**) Logitech USB Receiver: always reports core events
[    16.849] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    16.864] (II) Logitech USB Receiver: Found keys
[    16.864] (II) Logitech USB Receiver: Configuring as keyboard
[    16.864] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.864] (**) Option "xkb_rules" "evdev"
[    16.864] (**) Option "xkb_model" "evdev"
[    16.864] (**) Option "xkb_layout" "gb"
[    16.864] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    16.864] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.864] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.864] (**) Logitech USB Receiver: always reports core events
[    16.864] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    16.876] (II) Logitech USB Receiver: Found 20 mouse buttons
[    16.876] (II) Logitech USB Receiver: Found scroll wheel(s)
[    16.876] (II) Logitech USB Receiver: Found relative axes
[    16.876] (II) Logitech USB Receiver: Found x and y relative axes
[    16.876] (II) Logitech USB Receiver: Found absolute axes
[    16.876] (II) evdev-grail: failed to open grail, no gesture support
[    16.876] (II) Logitech USB Receiver: Found keys
[    16.876] (II) Logitech USB Receiver: Configuring as mouse
[    16.876] (II) Logitech USB Receiver: Configuring as keyboard
[    16.876] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.876] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.876] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.876] (**) Option "xkb_rules" "evdev"
[    16.876] (**) Option "xkb_model" "evdev"
[    16.876] (**) Option "xkb_layout" "gb"
[    16.876] (II) Logitech USB Receiver: initialized for relative axes.
[    16.876] (WW) Logitech USB Receiver: ignoring absolute axes.
[    16.876] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    16.876] (II) No input driver/identifier specified (ignoring)
[    16.877] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event6)
[    16.877] (II) No input driver/identifier specified (ignoring)
[    16.877] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[    16.877] (II) No input driver/identifier specified (ignoring)
[    16.878] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse2)
[    16.878] (II) No input driver/identifier specified (ignoring)
[    16.878] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event7)
[    16.878] (II) No input driver/identifier specified (ignoring)
[    16.878] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[    16.878] (II) No input driver/identifier specified (ignoring)
[    16.878] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse3)
[    16.878] (II) No input driver/identifier specified (ignoring)
[    16.878] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event8)
[    16.878] (II) No input driver/identifier specified (ignoring)
[    16.878] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[    16.878] (II) No input driver/identifier specified (ignoring)
[    16.879] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse4)
[    16.879] (II) No input driver/identifier specified (ignoring)
[    16.879] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event9)
[    16.879] (II) No input driver/identifier specified (ignoring)
[    16.879] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[    16.879] (II) No input driver/identifier specified (ignoring)
[    16.879] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse5)
[    16.879] (II) No input driver/identifier specified (ignoring)
[    16.881] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    16.881] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.881] (**) Logitech USB Receiver: always reports core events
[    16.881] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    16.904] (II) Logitech USB Receiver: Found keys
[    16.904] (II) Logitech USB Receiver: Configuring as keyboard
[    16.904] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.904] (**) Option "xkb_rules" "evdev"
[    16.904] (**) Option "xkb_model" "evdev"
[    16.904] (**) Option "xkb_layout" "gb"
[    16.904] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    16.904] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.904] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.904] (**) Logitech USB Receiver: always reports core events
[    16.904] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    16.936] (II) Logitech USB Receiver: Found 20 mouse buttons
[    16.936] (II) Logitech USB Receiver: Found scroll wheel(s)
[    16.936] (II) Logitech USB Receiver: Found relative axes
[    16.936] (II) Logitech USB Receiver: Found x and y relative axes
[    16.936] (II) Logitech USB Receiver: Found absolute axes
[    16.936] (II) evdev-grail: failed to open grail, no gesture support
[    16.936] (II) Logitech USB Receiver: Found keys
[    16.936] (II) Logitech USB Receiver: Configuring as mouse
[    16.936] (II) Logitech USB Receiver: Configuring as keyboard
[    16.936] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.936] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.936] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.936] (**) Option "xkb_rules" "evdev"
[    16.936] (**) Option "xkb_model" "evdev"
[    16.936] (**) Option "xkb_layout" "gb"
[    16.936] (II) Logitech USB Receiver: initialized for relative axes.
[    16.936] (WW) Logitech USB Receiver: ignoring absolute axes.
[    16.937] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    16.937] (II) No input driver/identifier specified (ignoring)
```

Have just removed my NVIDIA drivers and used Ubuntu's default driver. Same issue.

Your help is greatly appreciated.

---

### Post by krunge on 2010-11-05
Are those really the entire Xorg logs?  They don't seem to show that the X server is exiting normally or print a stack trace...  Usually Xorg prints a stacktrace for the crash.

Have you tried the x11vnc -noxfixes option?  Search these forums for noxfixes+x11vnc for more info.

**EDIT:**
I should have also suggested the "-noxrecord" option here.  It solved the user's problem.  See the following posts for more info.

---

### Post by nLinked on 2010-11-05
> **krunge said:**
> Are those really the entire Xorg logs?  They don't seem to show that the X server is exiting normally or print a stack trace...  Usually Xorg prints a stacktrace for the crash.

Have you tried the x11vnc -noxfixes option?  Search these forums for noxfixes+x11vnc for more info.

Have tried -noxfixes, same ~1 min logout problem. I tried a fresh Ubuntu 10.10 install in VirtualBox and it didn't have the same problem. I tried it on my laptop, it had the same exact problem. My desktop has an NVIDIA card, laptop is Intel onboard. It's not a graphics issue.

When the crash happens, when I log back in, the compiz process is taking 100% on one core. If I wait another minute or so and let the crash happen again and log back in, compiz is now taking 187 (nearly 200%), on two cores. 2 more crashes will result in all 4 cores. Have to restart to fix compiz CPU utilisation.

There are two more logs, I will attach them later today. They had the same name but instead of 0 in the filename they were "1".

---

### Post by krunge on 2010-11-05
Check that the X server PID goes away at the expected time and a new one starts up.  You can use ps and top for this.

Strange that compiz would still be running if the X server went away.

I suggest strace-ing (as root) the X server process to watch it go thru the failure (so you will have to attach strace to it before the 1 minute is up.) You could strace compiz too to try to see what it is doing.

---

### Post by nLinked on 2010-11-05
Is the Xorg process the correct one to monitor with strace? If so, I just did, and as soon as it happened, the log showed the following (everything before this part is normal): ```
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
```
Also, I just installed a fresh Ubuntu 10.10 on my 2nd hard drive, didn't update it, just installed x11vnc. All I did was add the following command to /etc/gdm/Init/Default:

```
/usr/bin/x11vnc -rfbauth /root/.vnc/passwd -rfbport 5901 -o /var/log/x11vnc.log -forever -bg
```

It too crashed out after about a minute. Same on my laptop. It doesn't crash out on a new VirtualBox Ubuntu 10.10 install. But it does on my desktop Ubuntu 10.10, my just-installed Ubuntu 10.10 on the same desktop on a 2nd HDD, and my laptop Ubuntu 10.10.

---

### Post by krunge on 2010-11-05
> **nLinked said:**
> Is the Xorg process the correct one to monitor with strace? If so, I just did, and as soon as it happened, the log showed the following (everything before this part is normal): ```
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
```

Excellent!  I'm very surprised the Xorg process doesn't log a backtrace to its /var/log/Xorg..  Those stack traces are very useful. Here is an example of one:
[INDENT][http://ubuntuforums.org/showpost.php?p=6132263&postcount=13](http://ubuntuforums.org/showpost.php?p=6132263&postcount=13)[/INDENT]
Are you sure you don't see something like that in the log file (be sure you are looking at the correct one, look for timestamps on the file, etc.)

In any event, you've shown there is a serious bug in the Xorg X server. It should never get a segmentation violation.

---

### Post by nLinked on 2010-11-06
**Xorg.0.log**
```
[  2611.008] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  2611.008] X Protocol Version 11, Revision 0
[  2611.008] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  2611.008] Current Operating System: Linux nb-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[  2611.008] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a4801d69-0ec7-4ab3-9598-c493c0851543 ro splash vga=799 quiet quiet splash
[  2611.008] Build Date: 16 September 2010  05:39:22PM
[  2611.008] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  2611.008] Current version of pixman: 0.18.4
[  2611.008] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  2611.008] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2611.009] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  6 16:18:14 2010
[  2611.009] (==) Using config file: "/etc/X11/xorg.conf"
[  2611.009] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2611.009] (==) ServerLayout "Layout0"
[  2611.009] (**) |-->Screen "Screen0" (0)
[  2611.009] (**) |   |-->Monitor "Monitor0"
[  2611.009] (**) |   |-->Device "Device0"
[  2611.009] (**) |-->Input Device "Keyboard0"
[  2611.009] (**) |-->Input Device "Mouse0"
[  2611.009] (**) Option "Xinerama" "0"
[  2611.009] (==) Automatically adding devices
[  2611.009] (==) Automatically enabling devices
[  2611.009] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2611.009] 	Entry deleted from font path.
[  2611.009] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  2611.009] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2611.009] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  2611.009] (WW) Disabling Keyboard0
[  2611.009] (WW) Disabling Mouse0
[  2611.009] (II) Loader magic: 0x81f8e00
[  2611.009] (II) Module ABI versions:
[  2611.009] 	X.Org ANSI C Emulation: 0.4
[  2611.009] 	X.Org Video Driver: 8.0
[  2611.009] 	X.Org XInput driver : 11.0
[  2611.009] 	X.Org Server Extension : 4.0
[  2611.010] (--) PCI:*(0:1:0:0) 10de:05e2:10de:0585 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[  2611.010] (II) Open ACPI successful (/var/run/acpid.socket)
[  2611.010] (II) LoadModule: "extmod"
[  2611.010] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2611.010] (II) Module extmod: vendor="X.Org Foundation"
[  2611.010] 	compiled for 1.9.0, module version = 1.0.0
[  2611.010] 	Module class: X.Org Server Extension
[  2611.010] 	ABI class: X.Org Server Extension, version 4.0
[  2611.010] (II) Loading extension MIT-SCREEN-SAVER
[  2611.010] (II) Loading extension XFree86-VidModeExtension
[  2611.010] (II) Loading extension XFree86-DGA
[  2611.010] (II) Loading extension DPMS
[  2611.010] (II) Loading extension XVideo
[  2611.010] (II) Loading extension XVideo-MotionCompensation
[  2611.010] (II) Loading extension X-Resource
[  2611.010] (II) LoadModule: "dbe"
[  2611.011] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2611.011] (II) Module dbe: vendor="X.Org Foundation"
[  2611.011] 	compiled for 1.9.0, module version = 1.0.0
[  2611.011] 	Module class: X.Org Server Extension
[  2611.011] 	ABI class: X.Org Server Extension, version 4.0
[  2611.011] (II) Loading extension DOUBLE-BUFFER
[  2611.011] (II) LoadModule: "glx"
[  2611.011] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  2611.022] (II) Module glx: vendor="NVIDIA Corporation"
[  2611.022] 	compiled for 4.0.2, module version = 1.0.0
[  2611.022] 	Module class: X.Org Server Extension
[  2611.022] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[  2611.022] (II) Loading extension GLX
[  2611.022] (II) LoadModule: "record"
[  2611.023] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2611.023] (II) Module record: vendor="X.Org Foundation"
[  2611.023] 	compiled for 1.9.0, module version = 1.13.0
[  2611.023] 	Module class: X.Org Server Extension
[  2611.023] 	ABI class: X.Org Server Extension, version 4.0
[  2611.023] (II) Loading extension RECORD
[  2611.023] (II) LoadModule: "dri"
[  2611.023] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2611.023] (II) Module dri: vendor="X.Org Foundation"
[  2611.023] 	compiled for 1.9.0, module version = 1.0.0
[  2611.023] 	ABI class: X.Org Server Extension, version 4.0
[  2611.023] (II) Loading extension XFree86-DRI
[  2611.023] (II) LoadModule: "dri2"
[  2611.023] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2611.023] (II) Module dri2: vendor="X.Org Foundation"
[  2611.023] 	compiled for 1.9.0, module version = 1.2.0
[  2611.023] 	ABI class: X.Org Server Extension, version 4.0
[  2611.024] (II) Loading extension DRI2
[  2611.024] (II) LoadModule: "nvidia"
[  2611.024] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  2611.024] (II) Module nvidia: vendor="NVIDIA Corporation"
[  2611.024] 	compiled for 4.0.2, module version = 1.0.0
[  2611.024] 	Module class: X.Org Video Driver
[  2611.024] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[  2611.024] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  2611.787] (--) using VT number 9

[  2612.077] (II) Loading sub module "fb"
[  2612.077] (II) LoadModule: "fb"
[  2612.077] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2612.077] (II) Module fb: vendor="X.Org Foundation"
[  2612.077] 	compiled for 1.9.0, module version = 1.0.0
[  2612.077] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2612.077] (II) Loading sub module "wfb"
[  2612.077] (II) LoadModule: "wfb"
[  2612.078] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  2612.078] (II) Module wfb: vendor="X.Org Foundation"
[  2612.078] 	compiled for 1.9.0, module version = 1.0.0
[  2612.078] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2612.078] (II) Loading sub module "ramdac"
[  2612.078] (II) LoadModule: "ramdac"
[  2612.078] (II) Module "ramdac" already built-in
[  2612.078] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  2612.078] (==) NVIDIA(0): RGB weight 888
[  2612.078] (==) NVIDIA(0): Default visual is TrueColor
[  2612.078] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  2612.079] (**) NVIDIA(0): Option "TwinView" "0"
[  2612.079] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[  2612.079] (**) NVIDIA(0): Enabling RENDER acceleration
[  2612.079] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  2612.079] (II) NVIDIA(0):     enabled.
[  2613.062] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[  2613.062] (--) NVIDIA(0): Memory: 917504 kBytes
[  2613.062] (--) NVIDIA(0): VideoBIOS: 62.00.0e.00.04
[  2613.062] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  2613.062] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  2613.063] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0
[  2613.063] (--) NVIDIA(0):     DELL 2707WFP (DFP-1)
[  2613.063] (--) NVIDIA(0): DELL 2707WFP (DFP-1): 330.0 MHz maximum pixel clock
[  2613.063] (--) NVIDIA(0): DELL 2707WFP (DFP-1): Internal Dual Link TMDS
[  2613.270] (II) NVIDIA(0): Assigned Display Device: DFP-1
[  2613.271] (II) NVIDIA(0): Validated modes:
[  2613.271] (II) NVIDIA(0):     "1440x900+0+0"
[  2613.271] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[  2613.297] (--) NVIDIA(0): DPI set to (63, 63); computed from "UseEdidDpi" X config
[  2613.297] (--) NVIDIA(0):     option
[  2613.297] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[  2613.297] (--) Depth 24 pixmap format is 32 bpp
[  2613.297] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  2613.299] (II) NVIDIA(0): Initialized GPU GART.
[  2613.305] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[  2613.342] (II) Loading extension NV-GLX
[  2613.371] (II) NVIDIA(0): Initialized OpenGL Acceleration
[  2613.379] (==) NVIDIA(0): Disabling shared memory pixmaps
[  2613.379] (II) NVIDIA(0): Initialized X Rendering Acceleration
[  2613.379] (==) NVIDIA(0): Backing store disabled
[  2613.379] (==) NVIDIA(0): Silken mouse enabled
[  2613.392] (**) NVIDIA(0): DPMS enabled
[  2613.392] (II) Loading extension NV-CONTROL
[  2613.392] (II) Loading extension XINERAMA
[  2613.392] (II) Loading sub module "dri2"
[  2613.392] (II) LoadModule: "dri2"
[  2613.393] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[  2613.393] (II) NVIDIA(0): [DRI2] Setup complete
[  2613.393] (==) RandR enabled
[  2613.393] (II) Initializing built-in extension Generic Event Extension
[  2613.393] (II) Initializing built-in extension SHAPE
[  2613.393] (II) Initializing built-in extension MIT-SHM
[  2613.393] (II) Initializing built-in extension XInputExtension
[  2613.393] (II) Initializing built-in extension XTEST
[  2613.393] (II) Initializing built-in extension BIG-REQUESTS
[  2613.393] (II) Initializing built-in extension SYNC
[  2613.393] (II) Initializing built-in extension XKEYBOARD
[  2613.393] (II) Initializing built-in extension XC-MISC
[  2613.393] (II) Initializing built-in extension SECURITY
[  2613.393] (II) Initializing built-in extension XINERAMA
[  2613.393] (II) Initializing built-in extension XFIXES
[  2613.393] (II) Initializing built-in extension RENDER
[  2613.393] (II) Initializing built-in extension RANDR
[  2613.393] (II) Initializing built-in extension COMPOSITE
[  2613.393] (II) Initializing built-in extension DAMAGE
[  2613.393] (II) Initializing built-in extension GESTURE
[  2613.395] (II) Initializing extension GLX
[  2613.418] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2613.424] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  2613.424] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2613.424] (II) LoadModule: "evdev"
[  2613.424] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2613.424] (II) Module evdev: vendor="X.Org Foundation"
[  2613.424] 	compiled for 1.9.0, module version = 2.3.2
[  2613.424] 	Module class: X.Org XInput Driver
[  2613.424] 	ABI class: X.Org XInput driver, version 11.0
[  2613.424] (**) Power Button: always reports core events
[  2613.424] (**) Power Button: Device: "/dev/input/event1"
[  2613.452] (II) Power Button: Found keys
[  2613.452] (II) Power Button: Configuring as keyboard
[  2613.452] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2613.452] (**) Option "xkb_rules" "evdev"
[  2613.452] (**) Option "xkb_model" "evdev"
[  2613.452] (**) Option "xkb_layout" "gb"
[  2613.456] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[  2613.459] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  2613.459] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2613.459] (**) Power Button: always reports core events
[  2613.459] (**) Power Button: Device: "/dev/input/event0"
[  2613.484] (II) Power Button: Found keys
[  2613.484] (II) Power Button: Configuring as keyboard
[  2613.484] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2613.484] (**) Option "xkb_rules" "evdev"
[  2613.484] (**) Option "xkb_model" "evdev"
[  2613.484] (**) Option "xkb_layout" "gb"
[  2613.486] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[  2613.487] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2613.487] (**) Logitech USB Receiver: always reports core events
[  2613.487] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[  2613.516] (II) Logitech USB Receiver: Found keys
[  2613.516] (II) Logitech USB Receiver: Configuring as keyboard
[  2613.516] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2613.516] (**) Option "xkb_rules" "evdev"
[  2613.516] (**) Option "xkb_model" "evdev"
[  2613.516] (**) Option "xkb_layout" "gb"
[  2613.518] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[  2613.518] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  2613.518] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2613.518] (**) Logitech USB Receiver: always reports core events
[  2613.518] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[  2613.548] (II) Logitech USB Receiver: Found 20 mouse buttons
[  2613.548] (II) Logitech USB Receiver: Found scroll wheel(s)
[  2613.548] (II) Logitech USB Receiver: Found relative axes
[  2613.548] (II) Logitech USB Receiver: Found x and y relative axes
[  2613.548] (II) Logitech USB Receiver: Found absolute axes
[  2613.548] (II) evdev-grail: failed to open grail, no gesture support
[  2613.548] (II) Logitech USB Receiver: Found keys
[  2613.548] (II) Logitech USB Receiver: Configuring as mouse
[  2613.548] (II) Logitech USB Receiver: Configuring as keyboard
[  2613.548] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  2613.548] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2613.548] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2613.548] (**) Option "xkb_rules" "evdev"
[  2613.548] (**) Option "xkb_model" "evdev"
[  2613.548] (**) Option "xkb_layout" "gb"
[  2613.549] (II) Logitech USB Receiver: initialized for relative axes.
[  2613.549] (WW) Logitech USB Receiver: ignoring absolute axes.
[  2613.550] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[  2613.550] (II) No input driver/identifier specified (ignoring)
[  2613.552] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event4)
[  2613.552] (II) No input driver/identifier specified (ignoring)
[  2613.553] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[  2613.553] (II) No input driver/identifier specified (ignoring)
[  2613.553] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse1)
[  2613.553] (II) No input driver/identifier specified (ignoring)
[  2613.553] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event5)
[  2613.554] (II) No input driver/identifier specified (ignoring)
[  2613.554] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[  2613.554] (II) No input driver/identifier specified (ignoring)
[  2613.554] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse2)
[  2613.554] (II) No input driver/identifier specified (ignoring)
[  2613.555] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event6)
[  2613.555] (II) No input driver/identifier specified (ignoring)
[  2613.555] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[  2613.555] (II) No input driver/identifier specified (ignoring)
[  2613.556] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse3)
[  2613.556] (II) No input driver/identifier specified (ignoring)
[  2613.556] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event7)
[  2613.556] (II) No input driver/identifier specified (ignoring)
[  2613.557] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[  2613.557] (II) No input driver/identifier specified (ignoring)
[  2613.557] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse4)
[  2613.557] (II) No input driver/identifier specified (ignoring)
[  2613.561] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[  2613.561] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2613.561] (**) Logitech USB Receiver: always reports core events
[  2613.561] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[  2613.580] (II) Logitech USB Receiver: Found keys
[  2613.580] (II) Logitech USB Receiver: Configuring as keyboard
[  2613.580] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2613.580] (**) Option "xkb_rules" "evdev"
[  2613.580] (**) Option "xkb_model" "evdev"
[  2613.580] (**) Option "xkb_layout" "gb"
[  2613.581] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event9)
[  2613.581] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  2613.581] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2613.581] (**) Logitech USB Receiver: always reports core events
[  2613.581] (**) Logitech USB Receiver: Device: "/dev/input/event9"
[  2613.612] (II) Logitech USB Receiver: Found 20 mouse buttons
[  2613.612] (II) Logitech USB Receiver: Found scroll wheel(s)
[  2613.612] (II) Logitech USB Receiver: Found relative axes
[  2613.612] (II) Logitech USB Receiver: Found x and y relative axes
[  2613.612] (II) Logitech USB Receiver: Found absolute axes
[  2613.612] (II) evdev-grail: failed to open grail, no gesture support
[  2613.612] (II) Logitech USB Receiver: Found keys
[  2613.612] (II) Logitech USB Receiver: Configuring as mouse
[  2613.612] (II) Logitech USB Receiver: Configuring as keyboard
[  2613.612] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  2613.612] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2613.612] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2613.612] (**) Option "xkb_rules" "evdev"
[  2613.612] (**) Option "xkb_model" "evdev"
[  2613.612] (**) Option "xkb_layout" "gb"
[  2613.612] (II) Logitech USB Receiver: initialized for relative axes.
[  2613.612] (WW) Logitech USB Receiver: ignoring absolute axes.
[  2613.613] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse5)
[  2613.613] (II) No input driver/identifier specified (ignoring)
```
**Xorg.0.log.old**
```
[  2437.263] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  2437.264] X Protocol Version 11, Revision 0
[  2437.264] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  2437.264] Current Operating System: Linux nb-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[  2437.264] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a4801d69-0ec7-4ab3-9598-c493c0851543 ro splash vga=799 quiet quiet splash
[  2437.264] Build Date: 16 September 2010  05:39:22PM
[  2437.264] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  2437.264] Current version of pixman: 0.18.4
[  2437.264] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  2437.264] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2437.264] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  6 16:15:20 2010
[  2437.264] (==) Using config file: "/etc/X11/xorg.conf"
[  2437.264] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2437.265] (==) ServerLayout "Layout0"
[  2437.265] (**) |-->Screen "Screen0" (0)
[  2437.265] (**) |   |-->Monitor "Monitor0"
[  2437.265] (**) |   |-->Device "Device0"
[  2437.265] (**) |-->Input Device "Keyboard0"
[  2437.265] (**) |-->Input Device "Mouse0"
[  2437.265] (**) Option "Xinerama" "0"
[  2437.265] (==) Automatically adding devices
[  2437.265] (==) Automatically enabling devices
[  2437.266] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2437.266] 	Entry deleted from font path.
[  2437.266] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  2437.266] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2437.266] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  2437.266] (WW) Disabling Keyboard0
[  2437.266] (WW) Disabling Mouse0
[  2437.266] (II) Loader magic: 0x81f8e00
[  2437.266] (II) Module ABI versions:
[  2437.266] 	X.Org ANSI C Emulation: 0.4
[  2437.266] 	X.Org Video Driver: 8.0
[  2437.266] 	X.Org XInput driver : 11.0
[  2437.266] 	X.Org Server Extension : 4.0
[  2437.267] (--) PCI:*(0:1:0:0) 10de:05e2:10de:0585 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[  2437.267] (II) Open ACPI successful (/var/run/acpid.socket)
[  2437.267] (II) LoadModule: "extmod"
[  2437.268] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2437.268] (II) Module extmod: vendor="X.Org Foundation"
[  2437.268] 	compiled for 1.9.0, module version = 1.0.0
[  2437.268] 	Module class: X.Org Server Extension
[  2437.268] 	ABI class: X.Org Server Extension, version 4.0
[  2437.268] (II) Loading extension MIT-SCREEN-SAVER
[  2437.268] (II) Loading extension XFree86-VidModeExtension
[  2437.268] (II) Loading extension XFree86-DGA
[  2437.268] (II) Loading extension DPMS
[  2437.268] (II) Loading extension XVideo
[  2437.268] (II) Loading extension XVideo-MotionCompensation
[  2437.268] (II) Loading extension X-Resource
[  2437.268] (II) LoadModule: "dbe"
[  2437.269] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2437.269] (II) Module dbe: vendor="X.Org Foundation"
[  2437.269] 	compiled for 1.9.0, module version = 1.0.0
[  2437.269] 	Module class: X.Org Server Extension
[  2437.269] 	ABI class: X.Org Server Extension, version 4.0
[  2437.269] (II) Loading extension DOUBLE-BUFFER
[  2437.269] (II) LoadModule: "glx"
[  2437.269] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  2437.282] (II) Module glx: vendor="NVIDIA Corporation"
[  2437.282] 	compiled for 4.0.2, module version = 1.0.0
[  2437.282] 	Module class: X.Org Server Extension
[  2437.282] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[  2437.282] (II) Loading extension GLX
[  2437.282] (II) LoadModule: "record"
[  2437.283] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2437.283] (II) Module record: vendor="X.Org Foundation"
[  2437.283] 	compiled for 1.9.0, module version = 1.13.0
[  2437.283] 	Module class: X.Org Server Extension
[  2437.283] 	ABI class: X.Org Server Extension, version 4.0
[  2437.283] (II) Loading extension RECORD
[  2437.283] (II) LoadModule: "dri"
[  2437.283] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2437.283] (II) Module dri: vendor="X.Org Foundation"
[  2437.283] 	compiled for 1.9.0, module version = 1.0.0
[  2437.283] 	ABI class: X.Org Server Extension, version 4.0
[  2437.283] (II) Loading extension XFree86-DRI
[  2437.283] (II) LoadModule: "dri2"
[  2437.283] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2437.284] (II) Module dri2: vendor="X.Org Foundation"
[  2437.284] 	compiled for 1.9.0, module version = 1.2.0
[  2437.284] 	ABI class: X.Org Server Extension, version 4.0
[  2437.284] (II) Loading extension DRI2
[  2437.284] (II) LoadModule: "nvidia"
[  2437.284] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  2437.284] (II) Module nvidia: vendor="NVIDIA Corporation"
[  2437.284] 	compiled for 4.0.2, module version = 1.0.0
[  2437.284] 	Module class: X.Org Video Driver
[  2437.284] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[  2437.284] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  2437.284] (--) using VT number 8

[  2437.529] (II) Loading sub module "fb"
[  2437.529] (II) LoadModule: "fb"
[  2437.529] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2437.529] (II) Module fb: vendor="X.Org Foundation"
[  2437.529] 	compiled for 1.9.0, module version = 1.0.0
[  2437.529] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2437.529] (II) Loading sub module "wfb"
[  2437.529] (II) LoadModule: "wfb"
[  2437.530] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  2437.530] (II) Module wfb: vendor="X.Org Foundation"
[  2437.530] 	compiled for 1.9.0, module version = 1.0.0
[  2437.530] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2437.530] (II) Loading sub module "ramdac"
[  2437.530] (II) LoadModule: "ramdac"
[  2437.530] (II) Module "ramdac" already built-in
[  2437.530] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  2437.530] (==) NVIDIA(0): RGB weight 888
[  2437.530] (==) NVIDIA(0): Default visual is TrueColor
[  2437.530] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  2437.530] (**) NVIDIA(0): Option "TwinView" "0"
[  2437.531] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[  2437.531] (**) NVIDIA(0): Enabling RENDER acceleration
[  2437.531] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  2437.531] (II) NVIDIA(0):     enabled.
[  2438.530] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[  2438.530] (--) NVIDIA(0): Memory: 917504 kBytes
[  2438.530] (--) NVIDIA(0): VideoBIOS: 62.00.0e.00.04
[  2438.530] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  2438.530] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  2438.530] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0
[  2438.530] (--) NVIDIA(0):     DELL 2707WFP (DFP-1)
[  2438.530] (--) NVIDIA(0): DELL 2707WFP (DFP-1): 330.0 MHz maximum pixel clock
[  2438.530] (--) NVIDIA(0): DELL 2707WFP (DFP-1): Internal Dual Link TMDS
[  2438.705] (II) NVIDIA(0): Assigned Display Device: DFP-1
[  2438.705] (II) NVIDIA(0): Validated modes:
[  2438.705] (II) NVIDIA(0):     "1440x900+0+0"
[  2438.705] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[  2438.731] (--) NVIDIA(0): DPI set to (63, 63); computed from "UseEdidDpi" X config
[  2438.731] (--) NVIDIA(0):     option
[  2438.731] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[  2438.731] (--) Depth 24 pixmap format is 32 bpp
[  2438.731] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  2438.732] (II) NVIDIA(0): Initialized GPU GART.
[  2438.739] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[  2438.778] (II) Loading extension NV-GLX
[  2438.807] (II) NVIDIA(0): Initialized OpenGL Acceleration
[  2438.815] (==) NVIDIA(0): Disabling shared memory pixmaps
[  2438.815] (II) NVIDIA(0): Initialized X Rendering Acceleration
[  2438.815] (==) NVIDIA(0): Backing store disabled
[  2438.815] (==) NVIDIA(0): Silken mouse enabled
[  2438.828] (**) NVIDIA(0): DPMS enabled
[  2438.828] (II) Loading extension NV-CONTROL
[  2438.828] (II) Loading extension XINERAMA
[  2438.828] (II) Loading sub module "dri2"
[  2438.828] (II) LoadModule: "dri2"
[  2438.829] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[  2438.829] (II) NVIDIA(0): [DRI2] Setup complete
[  2438.829] (==) RandR enabled
[  2438.829] (II) Initializing built-in extension Generic Event Extension
[  2438.829] (II) Initializing built-in extension SHAPE
[  2438.829] (II) Initializing built-in extension MIT-SHM
[  2438.829] (II) Initializing built-in extension XInputExtension
[  2438.829] (II) Initializing built-in extension XTEST
[  2438.829] (II) Initializing built-in extension BIG-REQUESTS
[  2438.829] (II) Initializing built-in extension SYNC
[  2438.829] (II) Initializing built-in extension XKEYBOARD
[  2438.829] (II) Initializing built-in extension XC-MISC
[  2438.829] (II) Initializing built-in extension SECURITY
[  2438.829] (II) Initializing built-in extension XINERAMA
[  2438.829] (II) Initializing built-in extension XFIXES
[  2438.829] (II) Initializing built-in extension RENDER
[  2438.829] (II) Initializing built-in extension RANDR
[  2438.829] (II) Initializing built-in extension COMPOSITE
[  2438.829] (II) Initializing built-in extension DAMAGE
[  2438.829] (II) Initializing built-in extension GESTURE
[  2438.831] (II) Initializing extension GLX
[  2438.854] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2438.860] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  2438.860] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2438.860] (II) LoadModule: "evdev"
[  2438.860] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2438.860] (II) Module evdev: vendor="X.Org Foundation"
[  2438.860] 	compiled for 1.9.0, module version = 2.3.2
[  2438.860] 	Module class: X.Org XInput Driver
[  2438.860] 	ABI class: X.Org XInput driver, version 11.0
[  2438.860] (**) Power Button: always reports core events
[  2438.860] (**) Power Button: Device: "/dev/input/event1"
[  2438.888] (II) Power Button: Found keys
[  2438.888] (II) Power Button: Configuring as keyboard
[  2438.888] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2438.888] (**) Option "xkb_rules" "evdev"
[  2438.888] (**) Option "xkb_model" "evdev"
[  2438.888] (**) Option "xkb_layout" "gb"
[  2438.892] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[  2438.895] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  2438.895] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2438.895] (**) Power Button: always reports core events
[  2438.895] (**) Power Button: Device: "/dev/input/event0"
[  2438.920] (II) Power Button: Found keys
[  2438.920] (II) Power Button: Configuring as keyboard
[  2438.920] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  2438.920] (**) Option "xkb_rules" "evdev"
[  2438.920] (**) Option "xkb_model" "evdev"
[  2438.920] (**) Option "xkb_layout" "gb"
[  2438.922] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[  2438.923] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2438.923] (**) Logitech USB Receiver: always reports core events
[  2438.923] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[  2438.952] (II) Logitech USB Receiver: Found keys
[  2438.952] (II) Logitech USB Receiver: Configuring as keyboard
[  2438.952] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2438.952] (**) Option "xkb_rules" "evdev"
[  2438.952] (**) Option "xkb_model" "evdev"
[  2438.952] (**) Option "xkb_layout" "gb"
[  2438.954] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[  2438.954] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  2438.954] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2438.954] (**) Logitech USB Receiver: always reports core events
[  2438.954] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[  2438.984] (II) Logitech USB Receiver: Found 20 mouse buttons
[  2438.984] (II) Logitech USB Receiver: Found scroll wheel(s)
[  2438.984] (II) Logitech USB Receiver: Found relative axes
[  2438.984] (II) Logitech USB Receiver: Found x and y relative axes
[  2438.984] (II) Logitech USB Receiver: Found absolute axes
[  2438.984] (II) evdev-grail: failed to open grail, no gesture support
[  2438.984] (II) Logitech USB Receiver: Found keys
[  2438.984] (II) Logitech USB Receiver: Configuring as mouse
[  2438.984] (II) Logitech USB Receiver: Configuring as keyboard
[  2438.984] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  2438.984] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2438.984] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2438.984] (**) Option "xkb_rules" "evdev"
[  2438.984] (**) Option "xkb_model" "evdev"
[  2438.984] (**) Option "xkb_layout" "gb"
[  2438.985] (II) Logitech USB Receiver: initialized for relative axes.
[  2438.985] (WW) Logitech USB Receiver: ignoring absolute axes.
[  2438.986] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[  2438.986] (II) No input driver/identifier specified (ignoring)
[  2438.988] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event4)
[  2438.988] (II) No input driver/identifier specified (ignoring)
[  2438.989] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[  2438.989] (II) No input driver/identifier specified (ignoring)
[  2438.989] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse1)
[  2438.989] (II) No input driver/identifier specified (ignoring)
[  2438.989] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event5)
[  2438.990] (II) No input driver/identifier specified (ignoring)
[  2438.990] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[  2438.990] (II) No input driver/identifier specified (ignoring)
[  2438.990] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse2)
[  2438.990] (II) No input driver/identifier specified (ignoring)
[  2438.991] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event6)
[  2438.991] (II) No input driver/identifier specified (ignoring)
[  2438.991] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[  2438.991] (II) No input driver/identifier specified (ignoring)
[  2438.992] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse3)
[  2438.992] (II) No input driver/identifier specified (ignoring)
[  2438.992] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event7)
[  2438.992] (II) No input driver/identifier specified (ignoring)
[  2438.993] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[  2438.993] (II) No input driver/identifier specified (ignoring)
[  2438.993] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse4)
[  2438.993] (II) No input driver/identifier specified (ignoring)
[  2438.997] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[  2438.997] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2438.997] (**) Logitech USB Receiver: always reports core events
[  2438.997] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[  2439.016] (II) Logitech USB Receiver: Found keys
[  2439.016] (II) Logitech USB Receiver: Configuring as keyboard
[  2439.016] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2439.016] (**) Option "xkb_rules" "evdev"
[  2439.016] (**) Option "xkb_model" "evdev"
[  2439.016] (**) Option "xkb_layout" "gb"
[  2439.018] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event9)
[  2439.018] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  2439.018] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  2439.018] (**) Logitech USB Receiver: always reports core events
[  2439.018] (**) Logitech USB Receiver: Device: "/dev/input/event9"
[  2439.048] (II) Logitech USB Receiver: Found 20 mouse buttons
[  2439.048] (II) Logitech USB Receiver: Found scroll wheel(s)
[  2439.048] (II) Logitech USB Receiver: Found relative axes
[  2439.048] (II) Logitech USB Receiver: Found x and y relative axes
[  2439.048] (II) Logitech USB Receiver: Found absolute axes
[  2439.048] (II) evdev-grail: failed to open grail, no gesture support
[  2439.048] (II) Logitech USB Receiver: Found keys
[  2439.048] (II) Logitech USB Receiver: Configuring as mouse
[  2439.048] (II) Logitech USB Receiver: Configuring as keyboard
[  2439.048] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  2439.048] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2439.048] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  2439.048] (**) Option "xkb_rules" "evdev"
[  2439.048] (**) Option "xkb_model" "evdev"
[  2439.048] (**) Option "xkb_layout" "gb"
[  2439.048] (II) Logitech USB Receiver: initialized for relative axes.
[  2439.048] (WW) Logitech USB Receiver: ignoring absolute axes.
[  2439.049] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse5)
[  2439.049] (II) No input driver/identifier specified (ignoring)
```
**Xorg.1.log**
```
[  3493.049] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  3493.049] X Protocol Version 11, Revision 0
[  3493.049] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  3493.049] Current Operating System: Linux nb-desktop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[  3493.049] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a4801d69-0ec7-4ab3-9598-c493c0851543 ro splash vga=799 quiet quiet splash
[  3493.049] Build Date: 16 September 2010  05:39:22PM
[  3493.049] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  3493.049] Current version of pixman: 0.18.4
[  3493.049] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  3493.049] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3493.050] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Nov  1 19:46:47 2010
[  3493.050] (==) Using config file: "/etc/X11/xorg.conf"
[  3493.050] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3493.099] (==) ServerLayout "Layout0"
[  3493.099] (**) |-->Screen "Screen0" (0)
[  3493.099] (**) |   |-->Monitor "Monitor0"
[  3493.099] (**) |   |-->Device "Device0"
[  3493.099] (**) |-->Input Device "Keyboard0"
[  3493.099] (**) |-->Input Device "Mouse0"
[  3493.099] (**) Option "Xinerama" "0"
[  3493.099] (==) Automatically adding devices
[  3493.099] (==) Automatically enabling devices
[  3493.099] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3493.099] 	Entry deleted from font path.
[  3493.099] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  3493.099] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3493.099] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  3493.099] (WW) Disabling Keyboard0
[  3493.099] (WW) Disabling Mouse0
[  3493.099] (II) Loader magic: 0x81f8e00
[  3493.099] (II) Module ABI versions:
[  3493.099] 	X.Org ANSI C Emulation: 0.4
[  3493.099] 	X.Org Video Driver: 8.0
[  3493.099] 	X.Org XInput driver : 11.0
[  3493.099] 	X.Org Server Extension : 4.0
[  3493.100] (--) PCI:*(0:1:0:0) 10de:05e2:10de:0585 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[  3493.100] (II) Open ACPI successful (/var/run/acpid.socket)
[  3493.100] (II) LoadModule: "extmod"
[  3493.100] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  3493.108] (II) Module extmod: vendor="X.Org Foundation"
[  3493.108] 	compiled for 1.9.0, module version = 1.0.0
[  3493.108] 	Module class: X.Org Server Extension
[  3493.108] 	ABI class: X.Org Server Extension, version 4.0
[  3493.108] (II) Loading extension MIT-SCREEN-SAVER
[  3493.108] (II) Loading extension XFree86-VidModeExtension
[  3493.108] (II) Loading extension XFree86-DGA
[  3493.108] (II) Loading extension DPMS
[  3493.108] (II) Loading extension XVideo
[  3493.108] (II) Loading extension XVideo-MotionCompensation
[  3493.108] (II) Loading extension X-Resource
[  3493.108] (II) LoadModule: "dbe"
[  3493.108] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  3493.109] (II) Module dbe: vendor="X.Org Foundation"
[  3493.109] 	compiled for 1.9.0, module version = 1.0.0
[  3493.109] 	Module class: X.Org Server Extension
[  3493.109] 	ABI class: X.Org Server Extension, version 4.0
[  3493.109] (II) Loading extension DOUBLE-BUFFER
[  3493.109] (II) LoadModule: "glx"
[  3493.109] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  3493.152] (II) Module glx: vendor="NVIDIA Corporation"
[  3493.152] 	compiled for 4.0.2, module version = 1.0.0
[  3493.152] 	Module class: X.Org Server Extension
[  3493.152] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[  3493.152] (II) Loading extension GLX
[  3493.152] (II) LoadModule: "record"
[  3493.152] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  3493.152] (II) Module record: vendor="X.Org Foundation"
[  3493.152] 	compiled for 1.9.0, module version = 1.13.0
[  3493.152] 	Module class: X.Org Server Extension
[  3493.152] 	ABI class: X.Org Server Extension, version 4.0
[  3493.153] (II) Loading extension RECORD
[  3493.153] (II) LoadModule: "dri"
[  3493.153] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  3493.174] (II) Module dri: vendor="X.Org Foundation"
[  3493.174] 	compiled for 1.9.0, module version = 1.0.0
[  3493.174] 	ABI class: X.Org Server Extension, version 4.0
[  3493.174] (II) Loading extension XFree86-DRI
[  3493.174] (II) LoadModule: "dri2"
[  3493.175] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  3493.175] (II) Module dri2: vendor="X.Org Foundation"
[  3493.175] 	compiled for 1.9.0, module version = 1.2.0
[  3493.175] 	ABI class: X.Org Server Extension, version 4.0
[  3493.175] (II) Loading extension DRI2
[  3493.175] (II) LoadModule: "nvidia"
[  3493.175] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  3493.210] (II) Module nvidia: vendor="NVIDIA Corporation"
[  3493.210] 	compiled for 4.0.2, module version = 1.0.0
[  3493.210] 	Module class: X.Org Video Driver
[  3493.227] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 06:37:13 PDT 2010
[  3493.231] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  3493.231] (--) using VT number 8

[  3495.242] (II) Loading sub module "fb"
[  3495.242] (II) LoadModule: "fb"
[  3495.242] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3495.268] (II) Module fb: vendor="X.Org Foundation"
[  3495.268] 	compiled for 1.9.0, module version = 1.0.0
[  3495.268] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3495.268] (II) Loading sub module "wfb"
[  3495.268] (II) LoadModule: "wfb"
[  3495.268] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  3495.276] (II) Module wfb: vendor="X.Org Foundation"
[  3495.276] 	compiled for 1.9.0, module version = 1.0.0
[  3495.276] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3495.276] (II) Loading sub module "ramdac"
[  3495.276] (II) LoadModule: "ramdac"
[  3495.276] (II) Module "ramdac" already built-in
[  3495.287] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  3495.287] (==) NVIDIA(0): RGB weight 888
[  3495.287] (==) NVIDIA(0): Default visual is TrueColor
[  3495.287] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  3495.288] (**) NVIDIA(0): Option "TwinView" "0"
[  3495.288] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[  3495.288] (**) NVIDIA(0): Enabling RENDER acceleration
[  3495.291] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  3495.291] (II) NVIDIA(0):     enabled.
[  3495.435] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[  3495.435] (--) NVIDIA(0): Memory: 917504 kBytes
[  3495.435] (--) NVIDIA(0): VideoBIOS: 62.00.0e.00.04
[  3495.435] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  3495.435] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  3495.435] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0
[  3495.435] (--) NVIDIA(0):     DELL 2707WFP (DFP-1)
[  3495.435] (--) NVIDIA(0): DELL 2707WFP (DFP-1): 330.0 MHz maximum pixel clock
[  3495.435] (--) NVIDIA(0): DELL 2707WFP (DFP-1): Internal Dual Link TMDS
[  3495.523] (II) NVIDIA(0): Assigned Display Device: DFP-1
[  3495.523] (II) NVIDIA(0): Validated modes:
[  3495.523] (II) NVIDIA(0):     "1440x900+0+0"
[  3495.523] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[  3495.554] (--) NVIDIA(0): DPI set to (63, 63); computed from "UseEdidDpi" X config
[  3495.554] (--) NVIDIA(0):     option
[  3495.554] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[  3495.565] (--) Depth 24 pixmap format is 32 bpp
[  3495.565] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  3495.567] (II) NVIDIA(0): Initialized GPU GART.
[  3495.575] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[  3495.621] (II) Loading extension NV-GLX
[  3495.645] (II) NVIDIA(0): Initialized OpenGL Acceleration
[  3495.669] (==) NVIDIA(0): Disabling shared memory pixmaps
[  3495.669] (II) NVIDIA(0): Initialized X Rendering Acceleration
[  3495.669] (==) NVIDIA(0): Backing store disabled
[  3495.669] (==) NVIDIA(0): Silken mouse enabled
[  3495.682] (**) NVIDIA(0): DPMS enabled
[  3495.682] (II) Loading extension NV-CONTROL
[  3495.682] (II) Loading extension XINERAMA
[  3495.682] (II) Loading sub module "dri2"
[  3495.682] (II) LoadModule: "dri2"
[  3495.682] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[  3495.682] (II) NVIDIA(0): [DRI2] Setup complete
[  3495.682] (==) RandR enabled
[  3495.682] (II) Initializing built-in extension Generic Event Extension
[  3495.682] (II) Initializing built-in extension SHAPE
[  3495.682] (II) Initializing built-in extension MIT-SHM
[  3495.682] (II) Initializing built-in extension XInputExtension
[  3495.682] (II) Initializing built-in extension XTEST
[  3495.682] (II) Initializing built-in extension BIG-REQUESTS
[  3495.682] (II) Initializing built-in extension SYNC
[  3495.682] (II) Initializing built-in extension XKEYBOARD
[  3495.682] (II) Initializing built-in extension XC-MISC
[  3495.682] (II) Initializing built-in extension SECURITY
[  3495.682] (II) Initializing built-in extension XINERAMA
[  3495.682] (II) Initializing built-in extension XFIXES
[  3495.682] (II) Initializing built-in extension RENDER
[  3495.682] (II) Initializing built-in extension RANDR
[  3495.682] (II) Initializing built-in extension COMPOSITE
[  3495.682] (II) Initializing built-in extension DAMAGE
[  3495.682] (II) Initializing built-in extension GESTURE
[  3495.684] (II) Initializing extension GLX
[  3495.832] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3495.856] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  3495.856] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3495.856] (II) LoadModule: "evdev"
[  3495.857] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3495.889] (II) Module evdev: vendor="X.Org Foundation"
[  3495.889] 	compiled for 1.9.0, module version = 2.3.2
[  3495.889] 	Module class: X.Org XInput Driver
[  3495.889] 	ABI class: X.Org XInput driver, version 11.0
[  3495.889] (**) Power Button: always reports core events
[  3495.889] (**) Power Button: Device: "/dev/input/event1"
[  3495.908] (II) Power Button: Found keys
[  3495.908] (II) Power Button: Configuring as keyboard
[  3495.908] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  3495.908] (**) Option "xkb_rules" "evdev"
[  3495.908] (**) Option "xkb_model" "evdev"
[  3495.908] (**) Option "xkb_layout" "gb"
[  3495.912] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[  3495.915] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  3495.915] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3495.915] (**) Power Button: always reports core events
[  3495.915] (**) Power Button: Device: "/dev/input/event0"
[  3495.940] (II) Power Button: Found keys
[  3495.940] (II) Power Button: Configuring as keyboard
[  3495.940] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  3495.940] (**) Option "xkb_rules" "evdev"
[  3495.940] (**) Option "xkb_model" "evdev"
[  3495.940] (**) Option "xkb_layout" "gb"
[  3495.942] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[  3495.942] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  3495.942] (**) Logitech USB Receiver: always reports core events
[  3495.942] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[  3495.972] (II) Logitech USB Receiver: Found keys
[  3495.972] (II) Logitech USB Receiver: Configuring as keyboard
[  3495.972] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  3495.972] (**) Option "xkb_rules" "evdev"
[  3495.972] (**) Option "xkb_model" "evdev"
[  3495.972] (**) Option "xkb_layout" "gb"
[  3495.973] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[  3495.973] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  3495.973] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  3495.973] (**) Logitech USB Receiver: always reports core events
[  3495.973] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[  3496.020] (II) Logitech USB Receiver: Found 20 mouse buttons
[  3496.020] (II) Logitech USB Receiver: Found scroll wheel(s)
[  3496.020] (II) Logitech USB Receiver: Found relative axes
[  3496.020] (II) Logitech USB Receiver: Found x and y relative axes
[  3496.020] (II) Logitech USB Receiver: Found absolute axes
[  3496.020] (II) evdev-grail: failed to open grail, no gesture support
[  3496.020] (II) Logitech USB Receiver: Found keys
[  3496.020] (II) Logitech USB Receiver: Configuring as mouse
[  3496.020] (II) Logitech USB Receiver: Configuring as keyboard
[  3496.020] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  3496.020] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3496.020] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  3496.020] (**) Option "xkb_rules" "evdev"
[  3496.020] (**) Option "xkb_model" "evdev"
[  3496.020] (**) Option "xkb_layout" "gb"
[  3496.020] (II) Logitech USB Receiver: initialized for relative axes.
[  3496.020] (WW) Logitech USB Receiver: ignoring absolute axes.
[  3496.021] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[  3496.021] (II) No input driver/identifier specified (ignoring)
[  3496.024] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event6)
[  3496.024] (II) No input driver/identifier specified (ignoring)
[  3496.024] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[  3496.024] (II) No input driver/identifier specified (ignoring)
[  3496.025] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse2)
[  3496.025] (II) No input driver/identifier specified (ignoring)
[  3496.025] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event7)
[  3496.025] (II) No input driver/identifier specified (ignoring)
[  3496.025] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[  3496.026] (II) No input driver/identifier specified (ignoring)
[  3496.026] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse3)
[  3496.026] (II) No input driver/identifier specified (ignoring)
[  3496.026] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event8)
[  3496.026] (II) No input driver/identifier specified (ignoring)
[  3496.027] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[  3496.027] (II) No input driver/identifier specified (ignoring)
[  3496.027] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse4)
[  3496.027] (II) No input driver/identifier specified (ignoring)
[  3496.028] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event9)
[  3496.028] (II) No input driver/identifier specified (ignoring)
[  3496.028] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[  3496.028] (II) No input driver/identifier specified (ignoring)
[  3496.029] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse5)
[  3496.029] (II) No input driver/identifier specified (ignoring)
[  3496.032] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[  3496.032] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  3496.032] (**) Logitech USB Receiver: always reports core events
[  3496.032] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[  3496.052] (II) Logitech USB Receiver: Found keys
[  3496.052] (II) Logitech USB Receiver: Configuring as keyboard
[  3496.052] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  3496.052] (**) Option "xkb_rules" "evdev"
[  3496.052] (**) Option "xkb_model" "evdev"
[  3496.052] (**) Option "xkb_layout" "gb"
[  3496.053] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[  3496.053] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  3496.053] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  3496.053] (**) Logitech USB Receiver: always reports core events
[  3496.053] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[  3496.084] (II) Logitech USB Receiver: Found 20 mouse buttons
[  3496.084] (II) Logitech USB Receiver: Found scroll wheel(s)
[  3496.084] (II) Logitech USB Receiver: Found relative axes
[  3496.084] (II) Logitech USB Receiver: Found x and y relative axes
[  3496.084] (II) Logitech USB Receiver: Found absolute axes
[  3496.084] (II) evdev-grail: failed to open grail, no gesture support
[  3496.084] (II) Logitech USB Receiver: Found keys
[  3496.084] (II) Logitech USB Receiver: Configuring as mouse
[  3496.084] (II) Logitech USB Receiver: Configuring as keyboard
[  3496.084] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  3496.084] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3496.084] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  3496.084] (**) Option "xkb_rules" "evdev"
[  3496.084] (**) Option "xkb_model" "evdev"
[  3496.084] (**) Option "xkb_layout" "gb"
[  3496.085] (II) Logitech USB Receiver: initialized for relative axes.
[  3496.085] (WW) Logitech USB Receiver: ignoring absolute axes.
[  3496.085] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[  3496.085] (II) No input driver/identifier specified (ignoring)
[  4367.524] (II) Power Button: Close
[  4367.524] (II) UnloadModule: "evdev"
[  4367.544] (II) Power Button: Close
[  4367.544] (II) UnloadModule: "evdev"
[  4367.572] (II) Logitech USB Receiver: Close
[  4367.572] (II) UnloadModule: "evdev"
[  4367.644] (II) Logitech USB Receiver: Close
[  4367.644] (II) UnloadModule: "evdev"
[  4367.676] (II) Logitech USB Receiver: Close
[  4367.676] (II) UnloadModule: "evdev"
[  4367.704] (II) Logitech USB Receiver: Close
[  4367.704] (II) UnloadModule: "evdev"
[  4369.129]  ddxSigGiveUp: Closing log
```
**Xorg.1.log.old**
```
[ 13821.322] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[ 13821.322] X Protocol Version 11, Revision 0
[ 13821.322] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[ 13821.322] Current Operating System: Linux nb-desktop 2.6.35-22-generic #32-Ubuntu SMP Wed Sep 15 23:39:25 UTC 2010 i686
[ 13821.322] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a4801d69-0ec7-4ab3-9598-c493c0851543 ro splash vga=799 quiet quiet splash
[ 13821.322] Build Date: 16 September 2010  05:39:22PM
[ 13821.322] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[ 13821.322] Current version of pixman: 0.18.4
[ 13821.322] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 13821.322] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 13821.323] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Sep 23 21:17:13 2010
[ 13821.326] (==) Using config file: "/etc/X11/xorg.conf"
[ 13821.326] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 13821.377] (==) ServerLayout "Layout0"
[ 13821.377] (**) |-->Screen "Screen0" (0)
[ 13821.377] (**) |   |-->Monitor "Monitor0"
[ 13821.377] (**) |   |-->Device "Device0"
[ 13821.377] (**) |-->Input Device "Keyboard0"
[ 13821.377] (**) |-->Input Device "Mouse0"
[ 13821.377] (**) Option "Xinerama" "0"
[ 13821.377] (==) Automatically adding devices
[ 13821.377] (==) Automatically enabling devices
[ 13821.377] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 13821.377] 	Entry deleted from font path.
[ 13821.377] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[ 13821.377] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 13821.377] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 13821.377] (WW) Disabling Keyboard0
[ 13821.377] (WW) Disabling Mouse0
[ 13821.377] (II) Loader magic: 0x81f8e00
[ 13821.377] (II) Module ABI versions:
[ 13821.377] 	X.Org ANSI C Emulation: 0.4
[ 13821.377] 	X.Org Video Driver: 8.0
[ 13821.377] 	X.Org XInput driver : 11.0
[ 13821.377] 	X.Org Server Extension : 4.0
[ 13821.378] (--) PCI:*(0:1:0:0) 10de:05e2:10de:0585 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[ 13821.378] (II) Open ACPI successful (/var/run/acpid.socket)
[ 13821.378] (II) LoadModule: "extmod"
[ 13821.379] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 13821.379] (II) Module extmod: vendor="X.Org Foundation"
[ 13821.379] 	compiled for 1.9.0, module version = 1.0.0
[ 13821.379] 	Module class: X.Org Server Extension
[ 13821.379] 	ABI class: X.Org Server Extension, version 4.0
[ 13821.379] (II) Loading extension MIT-SCREEN-SAVER
[ 13821.379] (II) Loading extension XFree86-VidModeExtension
[ 13821.379] (II) Loading extension XFree86-DGA
[ 13821.379] (II) Loading extension DPMS
[ 13821.379] (II) Loading extension XVideo
[ 13821.379] (II) Loading extension XVideo-MotionCompensation
[ 13821.379] (II) Loading extension X-Resource
[ 13821.379] (II) LoadModule: "dbe"
[ 13821.379] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 13821.379] (II) Module dbe: vendor="X.Org Foundation"
[ 13821.379] 	compiled for 1.9.0, module version = 1.0.0
[ 13821.379] 	Module class: X.Org Server Extension
[ 13821.379] 	ABI class: X.Org Server Extension, version 4.0
[ 13821.379] (II) Loading extension DOUBLE-BUFFER
[ 13821.379] (II) LoadModule: "glx"
[ 13821.379] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[ 13821.433] (II) Module glx: vendor="NVIDIA Corporation"
[ 13821.433] 	compiled for 4.0.2, module version = 1.0.0
[ 13821.433] 	Module class: X.Org Server Extension
[ 13821.433] (II) NVIDIA GLX Module  256.53  Fri Aug 27 21:28:41 PDT 2010
[ 13821.433] (II) Loading extension GLX
[ 13821.433] (II) LoadModule: "record"
[ 13821.434] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 13821.444] (II) Module record: vendor="X.Org Foundation"
[ 13821.444] 	compiled for 1.9.0, module version = 1.13.0
[ 13821.444] 	Module class: X.Org Server Extension
[ 13821.444] 	ABI class: X.Org Server Extension, version 4.0
[ 13821.444] (II) Loading extension RECORD
[ 13821.444] (II) LoadModule: "dri"
[ 13821.445] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 13821.447] (II) Module dri: vendor="X.Org Foundation"
[ 13821.447] 	compiled for 1.9.0, module version = 1.0.0
[ 13821.447] 	ABI class: X.Org Server Extension, version 4.0
[ 13821.447] (II) Loading extension XFree86-DRI
[ 13821.447] (II) LoadModule: "dri2"
[ 13821.447] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 13821.448] (II) Module dri2: vendor="X.Org Foundation"
[ 13821.448] 	compiled for 1.9.0, module version = 1.2.0
[ 13821.448] 	ABI class: X.Org Server Extension, version 4.0
[ 13821.448] (II) Loading extension DRI2
[ 13821.448] (II) LoadModule: "nvidia"
[ 13821.448] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[ 13821.477] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 13821.477] 	compiled for 4.0.2, module version = 1.0.0
[ 13821.477] 	Module class: X.Org Video Driver
[ 13821.490] (II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 21:05:55 PDT 2010
[ 13821.492] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 13821.492] (--) using VT number 8

[ 13823.472] (II) Loading sub module "fb"
[ 13823.472] (II) LoadModule: "fb"
[ 13823.472] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 13823.480] (II) Module fb: vendor="X.Org Foundation"
[ 13823.480] 	compiled for 1.9.0, module version = 1.0.0
[ 13823.480] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 13823.480] (II) Loading sub module "wfb"
[ 13823.480] (II) LoadModule: "wfb"
[ 13823.480] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 13823.480] (II) Module wfb: vendor="X.Org Foundation"
[ 13823.480] 	compiled for 1.9.0, module version = 1.0.0
[ 13823.480] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 13823.481] (II) Loading sub module "ramdac"
[ 13823.481] (II) LoadModule: "ramdac"
[ 13823.481] (II) Module "ramdac" already built-in
[ 13823.481] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 13823.481] (==) NVIDIA(0): RGB weight 888
[ 13823.481] (==) NVIDIA(0): Default visual is TrueColor
[ 13823.481] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 13823.481] (**) NVIDIA(0): Option "TwinView" "0"
[ 13823.481] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[ 13823.481] (**) NVIDIA(0): Enabling RENDER acceleration
[ 13823.481] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[ 13823.481] (II) NVIDIA(0):     enabled.
[ 13823.606] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[ 13823.606] (--) NVIDIA(0): Memory: 917504 kBytes
[ 13823.606] (--) NVIDIA(0): VideoBIOS: 62.00.0e.00.04
[ 13823.606] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 13823.606] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 13823.606] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0:
[ 13823.606] (--) NVIDIA(0):     DELL 2707WFP (DFP-1)
[ 13823.606] (--) NVIDIA(0): DELL 2707WFP (DFP-1): 330.0 MHz maximum pixel clock
[ 13823.606] (--) NVIDIA(0): DELL 2707WFP (DFP-1): Internal Dual Link TMDS
[ 13823.709] (II) NVIDIA(0): Assigned Display Device: DFP-1
[ 13823.709] (II) NVIDIA(0): Validated modes:
[ 13823.709] (II) NVIDIA(0):     "1440x900+0+0"
[ 13823.709] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[ 13823.733] (--) NVIDIA(0): DPI set to (63, 63); computed from "UseEdidDpi" X config
[ 13823.733] (--) NVIDIA(0):     option
[ 13823.733] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[ 13823.734] (--) Depth 24 pixmap format is 32 bpp
[ 13823.734] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[ 13823.735] (II) NVIDIA(0): Initialized GPU GART.
[ 13823.742] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[ 13823.779] (II) Loading extension NV-GLX
[ 13823.808] (II) NVIDIA(0): Initialized OpenGL Acceleration
[ 13823.827] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 13823.827] (II) NVIDIA(0): Initialized X Rendering Acceleration
[ 13823.827] (==) NVIDIA(0): Backing store disabled
[ 13823.827] (==) NVIDIA(0): Silken mouse enabled
[ 13823.844] (**) NVIDIA(0): DPMS enabled
[ 13823.844] (II) Loading extension NV-CONTROL
[ 13823.844] (II) Loading extension XINERAMA
[ 13823.844] (II) Loading sub module "dri2"
[ 13823.844] (II) LoadModule: "dri2"
[ 13823.845] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[ 13823.845] (II) NVIDIA(0): [DRI2] Setup complete
[ 13823.845] (==) RandR enabled
[ 13823.845] (II) Initializing built-in extension Generic Event Extension
[ 13823.845] (II) Initializing built-in extension SHAPE
[ 13823.845] (II) Initializing built-in extension MIT-SHM
[ 13823.845] (II) Initializing built-in extension XInputExtension
[ 13823.845] (II) Initializing built-in extension XTEST
[ 13823.845] (II) Initializing built-in extension BIG-REQUESTS
[ 13823.845] (II) Initializing built-in extension SYNC
[ 13823.845] (II) Initializing built-in extension XKEYBOARD
[ 13823.845] (II) Initializing built-in extension XC-MISC
[ 13823.845] (II) Initializing built-in extension SECURITY
[ 13823.845] (II) Initializing built-in extension XINERAMA
[ 13823.845] (II) Initializing built-in extension XFIXES
[ 13823.845] (II) Initializing built-in extension RENDER
[ 13823.845] (II) Initializing built-in extension RANDR
[ 13823.845] (II) Initializing built-in extension COMPOSITE
[ 13823.845] (II) Initializing built-in extension DAMAGE
[ 13823.845] (II) Initializing built-in extension GESTURE
[ 13823.847] (II) Initializing extension GLX
[ 13823.981] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 13824.002] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 13824.002] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 13824.002] (II) LoadModule: "evdev"
[ 13824.003] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 13824.027] (II) Module evdev: vendor="X.Org Foundation"
[ 13824.027] 	compiled for 1.9.0, module version = 2.3.2
[ 13824.027] 	Module class: X.Org XInput Driver
[ 13824.027] 	ABI class: X.Org XInput driver, version 11.0
[ 13824.027] (**) Power Button: always reports core events
[ 13824.027] (**) Power Button: Device: "/dev/input/event1"
[ 13824.048] (II) Power Button: Found keys
[ 13824.048] (II) Power Button: Configuring as keyboard
[ 13824.048] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 13824.048] (**) Option "xkb_rules" "evdev"
[ 13824.048] (**) Option "xkb_model" "evdev"
[ 13824.048] (**) Option "xkb_layout" "gb"
[ 13824.050] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[ 13824.051] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 13824.051] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 13824.051] (**) Power Button: always reports core events
[ 13824.051] (**) Power Button: Device: "/dev/input/event0"
[ 13824.072] (II) Power Button: Found keys
[ 13824.072] (II) Power Button: Configuring as keyboard
[ 13824.072] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[ 13824.072] (**) Option "xkb_rules" "evdev"
[ 13824.072] (**) Option "xkb_model" "evdev"
[ 13824.072] (**) Option "xkb_layout" "gb"
[ 13824.073] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event6)
[ 13824.073] (II) No input driver/identifier specified (ignoring)
[ 13824.073] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[ 13824.073] (II) No input driver/identifier specified (ignoring)
[ 13824.073] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse2)
[ 13824.074] (II) No input driver/identifier specified (ignoring)
[ 13824.074] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event7)
[ 13824.074] (II) No input driver/identifier specified (ignoring)
[ 13824.074] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[ 13824.074] (II) No input driver/identifier specified (ignoring)
[ 13824.074] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse3)
[ 13824.074] (II) No input driver/identifier specified (ignoring)
[ 13824.074] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event8)
[ 13824.074] (II) No input driver/identifier specified (ignoring)
[ 13824.074] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[ 13824.074] (II) No input driver/identifier specified (ignoring)
[ 13824.075] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse4)
[ 13824.075] (II) No input driver/identifier specified (ignoring)
[ 13824.075] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event9)
[ 13824.075] (II) No input driver/identifier specified (ignoring)
[ 13824.075] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[ 13824.075] (II) No input driver/identifier specified (ignoring)
[ 13824.075] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse5)
[ 13824.075] (II) No input driver/identifier specified (ignoring)
[ 13824.077] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[ 13824.077] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 13824.077] (**) Logitech USB Receiver: always reports core events
[ 13824.077] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[ 13824.104] (II) Logitech USB Receiver: Found keys
[ 13824.104] (II) Logitech USB Receiver: Configuring as keyboard
[ 13824.104] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 13824.104] (**) Option "xkb_rules" "evdev"
[ 13824.104] (**) Option "xkb_model" "evdev"
[ 13824.104] (**) Option "xkb_layout" "gb"
[ 13824.105] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[ 13824.105] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[ 13824.105] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 13824.105] (**) Logitech USB Receiver: always reports core events
[ 13824.105] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[ 13824.136] (II) Logitech USB Receiver: Found 20 mouse buttons
[ 13824.136] (II) Logitech USB Receiver: Found scroll wheel(s)
[ 13824.136] (II) Logitech USB Receiver: Found relative axes
[ 13824.136] (II) Logitech USB Receiver: Found x and y relative axes
[ 13824.136] (II) Logitech USB Receiver: Found absolute axes
[ 13824.136] (II) evdev-grail: failed to open grail, no gesture support
[ 13824.136] (II) Logitech USB Receiver: Found keys
[ 13824.136] (II) Logitech USB Receiver: Configuring as mouse
[ 13824.136] (II) Logitech USB Receiver: Configuring as keyboard
[ 13824.136] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[ 13824.136] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 13824.136] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 13824.136] (**) Option "xkb_rules" "evdev"
[ 13824.136] (**) Option "xkb_model" "evdev"
[ 13824.136] (**) Option "xkb_layout" "gb"
[ 13824.136] (II) Logitech USB Receiver: initialized for relative axes.
[ 13824.136] (WW) Logitech USB Receiver: ignoring absolute axes.
[ 13824.136] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[ 13824.136] (II) No input driver/identifier specified (ignoring)
[ 13824.137] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[ 13824.137] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 13824.137] (**) Logitech USB Receiver: always reports core events
[ 13824.137] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[ 13824.168] (II) Logitech USB Receiver: Found keys
[ 13824.168] (II) Logitech USB Receiver: Configuring as keyboard
[ 13824.168] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 13824.168] (**) Option "xkb_rules" "evdev"
[ 13824.168] (**) Option "xkb_model" "evdev"
[ 13824.168] (**) Option "xkb_layout" "gb"
[ 13824.168] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[ 13824.168] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[ 13824.168] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[ 13824.168] (**) Logitech USB Receiver: always reports core events
[ 13824.168] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[ 13824.200] (II) Logitech USB Receiver: Found 20 mouse buttons
[ 13824.200] (II) Logitech USB Receiver: Found scroll wheel(s)
[ 13824.200] (II) Logitech USB Receiver: Found relative axes
[ 13824.200] (II) Logitech USB Receiver: Found x and y relative axes
[ 13824.200] (II) Logitech USB Receiver: Found absolute axes
[ 13824.200] (II) evdev-grail: failed to open grail, no gesture support
[ 13824.200] (II) Logitech USB Receiver: Found keys
[ 13824.200] (II) Logitech USB Receiver: Configuring as mouse
[ 13824.200] (II) Logitech USB Receiver: Configuring as keyboard
[ 13824.200] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[ 13824.200] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 13824.200] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[ 13824.200] (**) Option "xkb_rules" "evdev"
[ 13824.200] (**) Option "xkb_model" "evdev"
[ 13824.200] (**) Option "xkb_layout" "gb"
[ 13824.200] (II) Logitech USB Receiver: initialized for relative axes.
[ 13824.200] (WW) Logitech USB Receiver: ignoring absolute axes.
[ 13824.200] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[ 13824.200] (II) No input driver/identifier specified (ignoring)
[ 16169.320] (II) Logitech USB Receiver: Close
[ 16169.706] (II) UnloadModule: "evdev"
[ 16169.706] (II) Logitech USB Receiver: Close
[ 16169.706] (II) UnloadModule: "evdev"
[ 16169.706] (II) Logitech USB Receiver: Close
[ 16169.706] (II) UnloadModule: "evdev"
[ 16169.706] (II) Logitech USB Receiver: Close
[ 16169.706] (II) UnloadModule: "evdev"
[ 16169.706] (II) Power Button: Close
[ 16169.706] (II) UnloadModule: "evdev"
[ 16169.706] (II) Power Button: Close
[ 16169.706] (II) UnloadModule: "evdev"
[ 16171.103]  ddxSigGiveUp: Closing log
```
**Xorg.2.log**
```
[  4055.087] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  4055.087] X Protocol Version 11, Revision 0
[  4055.087] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  4055.087] Current Operating System: Linux nb-desktop 2.6.35-22-generic #32-Ubuntu SMP Wed Sep 15 23:39:25 UTC 2010 i686
[  4055.087] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a4801d69-0ec7-4ab3-9598-c493c0851543 ro splash vga=799 quiet quiet splash
[  4055.088] Build Date: 16 September 2010  05:39:22PM
[  4055.088] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  4055.088] Current version of pixman: 0.18.4
[  4055.088] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  4055.088] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4055.088] (==) Log file: "/var/log/Xorg.2.log", Time: Sun Sep 19 15:03:16 2010
[  4055.088] (==) Using config file: "/etc/X11/xorg.conf"
[  4055.088] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  4055.088] (==) ServerLayout "Layout0"
[  4055.088] (**) |-->Screen "Screen0" (0)
[  4055.089] (**) |   |-->Monitor "Monitor0"
[  4055.089] (**) |   |-->Device "Device0"
[  4055.089] (**) |-->Input Device "Keyboard0"
[  4055.089] (**) |-->Input Device "Mouse0"
[  4055.089] (**) Option "Xinerama" "0"
[  4055.089] (==) Automatically adding devices
[  4055.089] (==) Automatically enabling devices
[  4055.089] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4055.089] 	Entry deleted from font path.
[  4055.089] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  4055.089] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  4055.089] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  4055.089] (WW) Disabling Keyboard0
[  4055.090] (WW) Disabling Mouse0
[  4055.090] (II) Loader magic: 0x81f8e00
[  4055.090] (II) Module ABI versions:
[  4055.090] 	X.Org ANSI C Emulation: 0.4
[  4055.090] 	X.Org Video Driver: 8.0
[  4055.090] 	X.Org XInput driver : 11.0
[  4055.090] 	X.Org Server Extension : 4.0
[  4055.091] (--) PCI:*(0:1:0:0) 10de:05e2:10de:0585 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[  4055.091] (II) Open ACPI successful (/var/run/acpid.socket)
[  4055.091] (II) LoadModule: "extmod"
[  4055.092] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  4055.092] (II) Module extmod: vendor="X.Org Foundation"
[  4055.092] 	compiled for 1.9.0, module version = 1.0.0
[  4055.092] 	Module class: X.Org Server Extension
[  4055.092] 	ABI class: X.Org Server Extension, version 4.0
[  4055.092] (II) Loading extension MIT-SCREEN-SAVER
[  4055.092] (II) Loading extension XFree86-VidModeExtension
[  4055.092] (II) Loading extension XFree86-DGA
[  4055.092] (II) Loading extension DPMS
[  4055.092] (II) Loading extension XVideo
[  4055.092] (II) Loading extension XVideo-MotionCompensation
[  4055.092] (II) Loading extension X-Resource
[  4055.092] (II) LoadModule: "dbe"
[  4055.093] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  4055.093] (II) Module dbe: vendor="X.Org Foundation"
[  4055.093] 	compiled for 1.9.0, module version = 1.0.0
[  4055.093] 	Module class: X.Org Server Extension
[  4055.093] 	ABI class: X.Org Server Extension, version 4.0
[  4055.093] (II) Loading extension DOUBLE-BUFFER
[  4055.093] (II) LoadModule: "glx"
[  4055.093] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  4055.107] (II) Module glx: vendor="NVIDIA Corporation"
[  4055.107] 	compiled for 4.0.2, module version = 1.0.0
[  4055.107] 	Module class: X.Org Server Extension
[  4055.107] (II) NVIDIA GLX Module  256.53  Fri Aug 27 21:28:41 PDT 2010
[  4055.107] (II) Loading extension GLX
[  4055.107] (II) LoadModule: "record"
[  4055.107] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  4055.107] (II) Module record: vendor="X.Org Foundation"
[  4055.107] 	compiled for 1.9.0, module version = 1.13.0
[  4055.107] 	Module class: X.Org Server Extension
[  4055.107] 	ABI class: X.Org Server Extension, version 4.0
[  4055.107] (II) Loading extension RECORD
[  4055.107] (II) LoadModule: "dri"
[  4055.108] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  4055.108] (II) Module dri: vendor="X.Org Foundation"
[  4055.108] 	compiled for 1.9.0, module version = 1.0.0
[  4055.108] 	ABI class: X.Org Server Extension, version 4.0
[  4055.108] (II) Loading extension XFree86-DRI
[  4055.108] (II) LoadModule: "dri2"
[  4055.108] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4055.108] (II) Module dri2: vendor="X.Org Foundation"
[  4055.108] 	compiled for 1.9.0, module version = 1.2.0
[  4055.108] 	ABI class: X.Org Server Extension, version 4.0
[  4055.108] (II) Loading extension DRI2
[  4055.108] (II) LoadModule: "nvidia"
[  4055.108] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  4055.108] (II) Module nvidia: vendor="NVIDIA Corporation"
[  4055.108] 	compiled for 4.0.2, module version = 1.0.0
[  4055.108] 	Module class: X.Org Video Driver
[  4055.108] (II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 21:05:55 PDT 2010
[  4055.108] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  4055.108] (--) using VT number 8

[  4056.724] (II) Loading sub module "fb"
[  4056.724] (II) LoadModule: "fb"
[  4056.725] (II) Loading /usr/lib/xorg/modules/libfb.so
[  4056.725] (II) Module fb: vendor="X.Org Foundation"
[  4056.725] 	compiled for 1.9.0, module version = 1.0.0
[  4056.725] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  4056.725] (II) Loading sub module "wfb"
[  4056.725] (II) LoadModule: "wfb"
[  4056.725] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  4056.725] (II) Module wfb: vendor="X.Org Foundation"
[  4056.725] 	compiled for 1.9.0, module version = 1.0.0
[  4056.725] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  4056.725] (II) Loading sub module "ramdac"
[  4056.725] (II) LoadModule: "ramdac"
[  4056.725] (II) Module "ramdac" already built-in
[  4056.725] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[  4056.725] (==) NVIDIA(0): RGB weight 888
[  4056.725] (==) NVIDIA(0): Default visual is TrueColor
[  4056.725] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  4056.725] (**) NVIDIA(0): Option "TwinView" "0"
[  4056.725] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[  4056.725] (**) NVIDIA(0): Enabling RENDER acceleration
[  4056.725] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  4056.725] (II) NVIDIA(0):     enabled.
[  4056.870] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[  4056.870] (--) NVIDIA(0): Memory: 917504 kBytes
[  4056.870] (--) NVIDIA(0): VideoBIOS: 62.00.0e.00.04
[  4056.870] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  4056.870] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  4056.870] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0:
[  4056.870] (--) NVIDIA(0):     DELL 2707WFP (DFP-1)
[  4056.870] (--) NVIDIA(0): DELL 2707WFP (DFP-1): 330.0 MHz maximum pixel clock
[  4056.870] (--) NVIDIA(0): DELL 2707WFP (DFP-1): Internal Dual Link TMDS
[  4056.955] (II) NVIDIA(0): Assigned Display Device: DFP-1
[  4056.956] (II) NVIDIA(0): Validated modes:
[  4056.956] (II) NVIDIA(0):     "1440x900+0+0"
[  4056.956] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[  4056.980] (--) NVIDIA(0): DPI set to (63, 63); computed from "UseEdidDpi" X config
[  4056.980] (--) NVIDIA(0):     option
[  4056.980] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[  4056.980] (--) Depth 24 pixmap format is 32 bpp
[  4056.980] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[  4056.982] (II) NVIDIA(0): Initialized GPU GART.
[  4056.989] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[  4057.023] (II) Loading extension NV-GLX
[  4057.038] (II) NVIDIA(0): Initialized OpenGL Acceleration
[  4057.046] (==) NVIDIA(0): Disabling shared memory pixmaps
[  4057.046] (II) NVIDIA(0): Initialized X Rendering Acceleration
[  4057.046] (==) NVIDIA(0): Backing store disabled
[  4057.046] (==) NVIDIA(0): Silken mouse enabled
[  4057.057] (**) NVIDIA(0): DPMS enabled
[  4057.057] (II) Loading extension NV-CONTROL
[  4057.058] (II) Loading extension XINERAMA
[  4057.058] (II) Loading sub module "dri2"
[  4057.058] (II) LoadModule: "dri2"
[  4057.058] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[  4057.058] (II) NVIDIA(0): [DRI2] Setup complete
[  4057.058] (==) RandR enabled
[  4057.058] (II) Initializing built-in extension Generic Event Extension
[  4057.058] (II) Initializing built-in extension SHAPE
[  4057.058] (II) Initializing built-in extension MIT-SHM
[  4057.058] (II) Initializing built-in extension XInputExtension
[  4057.058] (II) Initializing built-in extension XTEST
[  4057.058] (II) Initializing built-in extension BIG-REQUESTS
[  4057.058] (II) Initializing built-in extension SYNC
[  4057.058] (II) Initializing built-in extension XKEYBOARD
[  4057.058] (II) Initializing built-in extension XC-MISC
[  4057.058] (II) Initializing built-in extension SECURITY
[  4057.058] (II) Initializing built-in extension XINERAMA
[  4057.058] (II) Initializing built-in extension XFIXES
[  4057.058] (II) Initializing built-in extension RENDER
[  4057.058] (II) Initializing built-in extension RANDR
[  4057.058] (II) Initializing built-in extension COMPOSITE
[  4057.058] (II) Initializing built-in extension DAMAGE
[  4057.058] (II) Initializing built-in extension GESTURE
[  4057.060] (II) Initializing extension GLX
[  4057.084] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  4057.089] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  4057.089] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  4057.089] (II) LoadModule: "evdev"
[  4057.089] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4057.090] (II) Module evdev: vendor="X.Org Foundation"
[  4057.090] 	compiled for 1.9.0, module version = 2.3.2
[  4057.090] 	Module class: X.Org XInput Driver
[  4057.090] 	ABI class: X.Org XInput driver, version 11.0
[  4057.090] (**) Power Button: always reports core events
[  4057.090] (**) Power Button: Device: "/dev/input/event1"
[  4057.116] (II) Power Button: Found keys
[  4057.116] (II) Power Button: Configuring as keyboard
[  4057.116] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  4057.117] (**) Option "xkb_rules" "evdev"
[  4057.117] (**) Option "xkb_model" "evdev"
[  4057.117] (**) Option "xkb_layout" "gb"
[  4057.121] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[  4057.124] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  4057.124] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  4057.124] (**) Power Button: always reports core events
[  4057.124] (**) Power Button: Device: "/dev/input/event0"
[  4057.140] (II) Power Button: Found keys
[  4057.140] (II) Power Button: Configuring as keyboard
[  4057.140] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  4057.140] (**) Option "xkb_rules" "evdev"
[  4057.141] (**) Option "xkb_model" "evdev"
[  4057.141] (**) Option "xkb_layout" "gb"
[  4057.143] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event2)
[  4057.143] (II) No input driver/identifier specified (ignoring)
[  4057.144] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js0)
[  4057.144] (II) No input driver/identifier specified (ignoring)
[  4057.144] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse0)
[  4057.144] (II) No input driver/identifier specified (ignoring)
[  4057.145] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event3)
[  4057.145] (II) No input driver/identifier specified (ignoring)
[  4057.145] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js1)
[  4057.145] (II) No input driver/identifier specified (ignoring)
[  4057.145] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse1)
[  4057.146] (II) No input driver/identifier specified (ignoring)
[  4057.146] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event4)
[  4057.146] (II) No input driver/identifier specified (ignoring)
[  4057.146] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js2)
[  4057.146] (II) No input driver/identifier specified (ignoring)
[  4057.147] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse2)
[  4057.147] (II) No input driver/identifier specified (ignoring)
[  4057.147] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/event5)
[  4057.147] (II) No input driver/identifier specified (ignoring)
[  4057.148] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/js3)
[  4057.148] (II) No input driver/identifier specified (ignoring)
[  4057.148] (II) config/udev: Adding input device Xbox 360 Wireless Receiver (/dev/input/mouse3)
[  4057.148] (II) No input driver/identifier specified (ignoring)
[  4057.152] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[  4057.152] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  4057.152] (**) Logitech USB Receiver: always reports core events
[  4057.152] (**) Logitech USB Receiver: Device: "/dev/input/event8"
[  4057.172] (II) Logitech USB Receiver: Found keys
[  4057.173] (II) Logitech USB Receiver: Configuring as keyboard
[  4057.173] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  4057.173] (**) Option "xkb_rules" "evdev"
[  4057.173] (**) Option "xkb_model" "evdev"
[  4057.173] (**) Option "xkb_layout" "gb"
[  4057.174] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event9)
[  4057.174] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  4057.174] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  4057.174] (**) Logitech USB Receiver: always reports core events
[  4057.174] (**) Logitech USB Receiver: Device: "/dev/input/event9"
[  4057.204] (II) Logitech USB Receiver: Found 20 mouse buttons
[  4057.204] (II) Logitech USB Receiver: Found scroll wheel(s)
[  4057.204] (II) Logitech USB Receiver: Found relative axes
[  4057.204] (II) Logitech USB Receiver: Found x and y relative axes
[  4057.204] (II) Logitech USB Receiver: Found absolute axes
[  4057.204] (II) evdev-grail: failed to open grail, no gesture support
[  4057.204] (II) Logitech USB Receiver: Found keys
[  4057.204] (II) Logitech USB Receiver: Configuring as mouse
[  4057.204] (II) Logitech USB Receiver: Configuring as keyboard
[  4057.204] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  4057.204] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  4057.204] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  4057.204] (**) Option "xkb_rules" "evdev"
[  4057.204] (**) Option "xkb_model" "evdev"
[  4057.204] (**) Option "xkb_layout" "gb"
[  4057.204] (II) Logitech USB Receiver: initialized for relative axes.
[  4057.205] (WW) Logitech USB Receiver: ignoring absolute axes.
[  4057.205] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse5)
[  4057.205] (II) No input driver/identifier specified (ignoring)
[  4057.208] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[  4057.208] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  4057.208] (**) Logitech USB Receiver: always reports core events
[  4057.208] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[  4057.236] (II) Logitech USB Receiver: Found keys
[  4057.236] (II) Logitech USB Receiver: Configuring as keyboard
[  4057.236] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  4057.236] (**) Option "xkb_rules" "evdev"
[  4057.236] (**) Option "xkb_model" "evdev"
[  4057.236] (**) Option "xkb_layout" "gb"
[  4057.237] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[  4057.237] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  4057.237] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  4057.237] (**) Logitech USB Receiver: always reports core events
[  4057.237] (**) Logitech USB Receiver: Device: "/dev/input/event7"
[  4057.268] (II) Logitech USB Receiver: Found 20 mouse buttons
[  4057.268] (II) Logitech USB Receiver: Found scroll wheel(s)
[  4057.268] (II) Logitech USB Receiver: Found relative axes
[  4057.268] (II) Logitech USB Receiver: Found x and y relative axes
[  4057.268] (II) Logitech USB Receiver: Found absolute axes
[  4057.268] (II) evdev-grail: failed to open grail, no gesture support
[  4057.268] (II) Logitech USB Receiver: Found keys
[  4057.268] (II) Logitech USB Receiver: Configuring as mouse
[  4057.268] (II) Logitech USB Receiver: Configuring as keyboard
[  4057.268] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  4057.268] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  4057.268] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  4057.268] (**) Option "xkb_rules" "evdev"
[  4057.268] (**) Option "xkb_model" "evdev"
[  4057.268] (**) Option "xkb_layout" "gb"
[  4057.268] (II) Logitech USB Receiver: initialized for relative axes.
[  4057.268] (WW) Logitech USB Receiver: ignoring absolute axes.
[  4057.269] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse4)
[  4057.269] (II) No input driver/identifier specified (ignoring)
[  4066.092] (II) Power Button: Close
[  4066.092] (II) UnloadModule: "evdev"
[  4066.120] (II) Power Button: Close
[  4066.120] (II) UnloadModule: "evdev"
[  4066.168] (II) Logitech USB Receiver: Close
[  4066.169] (II) UnloadModule: "evdev"
[  4066.196] (II) Logitech USB Receiver: Close
[  4066.204] (II) UnloadModule: "evdev"
[  4066.232] (II) Logitech USB Receiver: Close
[  4066.237] (II) UnloadModule: "evdev"
[  4066.268] (II) Logitech USB Receiver: Close
[  4066.269] (II) UnloadModule: "evdev"
[  4067.333]  ddxSigGiveUp: Closing log
```

---

### Post by krunge on 2010-11-06
OK, so the Xorg server receives a SEGV and doesn't print a backtrace. I guess that can happen.

BTW, for reference you should know which $DISPLAY is crashing (I suspect it is :0 ) and so you only need to look at /var/log/Xorg.$DISPLAY.log*  You can also look at the timestamps on these log files (ls -l) to see which ones are older than the current crash.

Anyway, back to troubleshooting.  What happens if you get rid of your /etc/gdm/Init/Default x11vnc line completely, and then log in at the physical display and then quickly start x11vnc manually (or via a desktop app Startup) and attach a VNC viewer to it quickly as well?  Does it still crash the X server? I'm not saying this is your solution, just asking what happens.

For reasons I have never fully understood, starting x11vnc from /etc/gdm/Init/Default always seems to have the best chance at triggering Xorg SEGV and other bugs.

---

### Post by nLinked on 2010-11-06
> **krunge said:**
> OK, so the Xorg server receives a SEGV and doesn't print a backtrace. I guess that can happen.

BTW, for reference you should know which $DISPLAY is crashing (I suspect it is :0 ) and so you only need to look at /var/log/Xorg.$DISPLAY.log*  You can also look at the timestamps on these log files (ls -l) to see which ones are older than the current crash.

Anyway, back to troubleshooting.  What happens if you get rid of your /etc/gdm/Init/Default x11vnc line completely, and then log in at the physical display and then quickly start x11vnc manually (or via a desktop app Startup) and attach a VNC viewer to it quickly as well?  Does it still crash the X server? I'm not saying this is your solution, just asking what happens.

For reasons I have never fully understood, starting x11vnc from /etc/gdm/Init/Default always seems to have the best chance at triggering Xorg SEGV and other bugs.

Thanks for your continued help with all this :)

Yup, am only interested in display 0 (as seen sitting at the local computer). If I remove the line from /etc/gdm/Init/Default, login and enter the command manually, everything is fine. It will not log out. And connecting to it is fine as well and works.

Only happens if using the /etc/gdm/Init/Default file.

I have just installed another fresh copy of 10.10 on another new partition. I didn't update it. I didn't install graphics drivers. I installed only x11vnc and entered the command in the /etc/gdm/Init/Default file. I logged out and back in. x11vnc was running as a process.

About 2 minutes later, it logged me out. It's happening on a fresh install. It doesn't happen in VirtualBox.

The only difference between my fresh installs and fresh Vbox installs, is that when I install to my hard drive, I install using a Live USB I made with Ubuntu's Startup Disk Creator (System, > Administration). It is the latest current 10.10 Ubuntu from their site.

When I install to a VirtualBox VM machine, I use the ISO.

This is the only difference I can think of. But it's not my computer either because it's happening on my laptop too (which I also installed using the same Live USB but same ISO).

Would you mind creating a Live USB with 10.10 32-bit, and trying this on a fresh install? I use the following command in the /etc/gdm/Init/Default file:
```
/usr/bin/x11vnc -rfbauth /root/.vnc/passwd -rfbport 5901 -o /var/log/x11vnc.log -forever -bg
```

But it doesn't matter if I even just use the following one, it still crashes out: ```
/usr/bin/x11vnc -forever -bg
```

---

### Post by krunge on 2010-11-06
I'm a little bit too busy to verify this on a live cd at the moment, so I will hold off that for now.

BTW, you often say the system "logged you out" but it is much more serious than that: the X server is crashing with a SEGV and taking down everything else with it. Then the X server is restarted with the login greeter showing.

Anyway, does the following work?  I note you have the '-forever' x11vnc option.  What if you connect the first time and login at the GDM greeter. As soon as you see your desktop coming up you quickly disconnect your VNC viewer.  Then you wait 1-2 minutes and reconnect with your VNC viewer (this time seeing your desktop instead of the GDM greeter.)  Do you see any crashes in that case?  Again, I don't intend this to be your solution, just gathering info.

---

### Post by nLinked on 2010-11-06
No problem. You're right, it is more serious than a log out, it just crashes out straight.

**I think I've just fixed it!** Fingers crossed.

I saw [this]("http://ubuntuforums.org/showpost.php?p=9931688&postcount=8") post.

Which led me to "Comment 1" [here]("http://bugs.freedesktop.org/show_bug.cgi?id=30032#c1").

I just added the -noxrecord to the command in the /etc/gdm/Init/Default file. Logged out and in. x11vnc process is started. So far no crash! Am just going to restart the computer and see how it goes.

If it happens again I'll give your method above a test.

What exactly is this -noxrecord doing though?

**EDIT: After a restart, it is still working!**
Adding -noxrecord to the command in the /etc/gdm/Init/Default file has stopped X from crashing out every minute or two after logging in!

This is a relief! Finally all is good and I have a VNC server running.

Thanks for all your help! Will edit original post with solution. Hopefully the X people will fix that bug.

---

### Post by krunge on 2010-11-06
> **nLinked said:**
> 
**I think I've just fixed it!** Fingers crossed.

I saw [this]("http://ubuntuforums.org/showpost.php?p=9931688&postcount=8") post.

Which led me to "Comment 1" [here]("http://bugs.freedesktop.org/show_bug.cgi?id=30032#c1").

Doh! That is MY post!  I thought I asked you if you had tried "-noxrecord" but it appears I only asked about "-noxfixes".

This XRECORD bug in the Xorg X server is a relatively new one. The good news is, as seen in the Comment 1, is that they might actually fix it quickly.

I will tell you how the XRECORD works with x11vnc.  X has an extension called "RECORD" that lets an app record the dialog between the X server and the various applications that are connected to the X server. x11vnc snoops this way to see if any app is scrolling the contents of a window (e.g. when you hit down-arrow inside a browser window.)  When detected, x11vnc can do a great speedup called CopyRect that tells the VNC viewer to  copy a rectangle to emulate the scroll.  That way the entire scrolling window's pixel contents does not need to be resent over the network (for each down-arrow, etc.)  This method is heuristic and it doesn't detect all scrolls.

By using -noxrecord you disable this speedup. Working of a lan you probably will never notice it.  Working over a slow broadband link you'd probably only notice it because I just described what to look for!

Anyway, glad you have a workaround and let's hope Xorg pushes its fix quickly.

---

### Post by nLinked on 2010-11-06
> **krunge said:**
> Doh! That is MY post!

So it is! Haha, completely missed that! Thanks.

Have a slight issue here. The crashout problem is gone. But I did a little test.

I connected via VNC on my LAN to this computer. I was at the login screen. I logged into my account via VNC. Everything was fine.

I logged out and back in. Was fine.

I logged out and went into the 2nd user account on this computer via VNC, was fine.

I now did a 'switch user' to lock-out of that account, and then logged into this one. But the screen became black on the remote computer I was working from.

VNC became useless remotely. I had to go over the this computer to restart x11vnc. I also noticed there were 2 Xorg processes running now.

Don't know if this can be fixed.

Do you know a way where I can connect with VNC so I can see the login screen, but as soon as I login, another x11vnc command can run at startup of that user account (through say Startup Applications), which kills all x11vnc processes (namely the GDM one), and runs off the current user account? Of course I will have to reconnect VNC remotely again.

And then when I log out, the GDM x11vnc comes back in (should do anyway since its in the file). This should help workaround my switch user blackout issue.

---

### Post by krunge on 2010-11-06
> **nLinked said:**
> 
I logged out and went into the 2nd user account on this computer via VNC, was fine.

I now did a 'switch user' to lock-out of that account, and then logged into this one. But the screen became black on the remote computer I was working from.

VNC became useless remotely. I had to go over the this computer to restart x11vnc. I also noticed there were 2 Xorg processes running now.

Don't know if this can be fixed.

I describe this problem here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc](http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc)[/INDENT]

Yes, of course there are two X servers, one for each user session.  These are likely what caused your $DISPLAY :1 and :2 you included logs for earlier.

There are two X servers, but only one of them can control the physical graphics hardware (and keyboard and mouse too) at a given time. See the above link for more info.

The bottom line is you can use the chvt(1) program to switch between the virtual terminals for the two X sessions.

x11vnc can even do this (run chvt) automatically for you, but you have to specify some options to do it and use it in a certain mode...
> 
Do you know a way where I can connect with VNC so I can see the login screen, but as soon as I login, another x11vnc command can run at startup of that user account (through say Startup Applications), which kills all x11vnc processes (namely the GDM one), and runs off the current user account? Of course I will have to reconnect VNC remotely again.

This should be possible with a script that runs from the user's startup.  The script could run 'x11vnc -R stop' to stop the first x11vnc, and then run the new x11vnc cmd you want.  I'm not sure what you are trying to do, but that will work.

---

### Post by Tatayet on 2010-11-18
> **nLinked said:**
> 

**EDIT: After a restart, it is still working!**
Adding -noxrecord to the command in the /etc/gdm/Init/Default file has stopped X from crashing out every minute or two after logging in!

Hello,

Sorry but I don't find where exactly I have to put -noxrecord in file?

Thanks

---

### Post by krunge on 2010-11-18
> **Tatayet said:**
> 
Sorry but I don't find where exactly I have to put -noxrecord in file?

Are you are sure you are running the x11vnc program and not something else?

I believe you (the user or admin) have to manually put the x11vnc command line in a config file someplace for GDM to launch it. It is on that x11vnc command line you add '-noxrecord'.

---

### Post by nLinked on 2010-11-18
> **krunge said:**
> Are you are sure you are running the x11vnc program and not something else?

I believe you (the user or admin) have to manually put the x11vnc command line in a config file someplace for GDM to launch it. It is on that x11vnc command line you add '-noxrecord'.

That's correct. My entire x11vnc command is in the  /etc/gdm/Init/Default file, and I placed -noxrecord in the same command and it solved the problem.

---

### Post by Tatayet on 2010-11-19
I'm very sorry.
I don't see for install xvnc11.

But today I install a fresh install of Xubuntu because it's an old laptop and I have exactly the same problem. With nothing install and upgrade.

So I think it's another problem, but what?
:(

Sorry

---

### Post by krunge on 2010-11-19
> **Tatayet said:**
> I'm very sorry.
I don't see for install xvnc11.

So I think it's another problem, but what?

Sorry
Please start another thread.

---

### Post by Tatayet on 2010-11-19
Start Ubuntu Server install.

---

### Post by szandor on 2010-12-08
**EDIT 3: SOLVED!**
Post #15 [here]("http://ubuntuforums.org/showpost.php?p=10082455&postcount=15") (same thread) fixes this issue.[/QUOTE]

thanks, this solved my x issues.

---

### Post by negora on 2010-12-12
Finally I also could solve this problem, which was driving me crazy. Thank you a lot for the solution :) .

---

### Post by cboling on 2010-12-16
> What exactly is this -noxrecord doing though?

From the man page:
*Disable any use of the RECORD extension.  This is currently used by the -scrollcopyrect scheme and to monitor X server grabs.*
As I understand it, this X extension provides a simple way to record/playback events within the X server.

PS: Thanks for this workaround!

---

### Post by djchester on 2010-12-22
> **krunge said:**
> Doh! That is MY post!  I thought I asked you if you had tried "-noxrecord" but it appears I only asked about "-noxfixes".

This XRECORD bug in the Xorg X server is a relatively new one. The good news is, as seen in the Comment 1, is that they might actually fix it quickly.

I will tell you how the XRECORD works with x11vnc.  X has an extension called "RECORD" that lets an app record the dialog between the X server and the various applications that are connected to the X server. x11vnc snoops this way to see if any app is scrolling the contents of a window (e.g. when you hit down-arrow inside a browser window.)  When detected, x11vnc can do a great speedup called CopyRect that tells the VNC viewer to  copy a rectangle to emulate the scroll.  That way the entire scrolling window's pixel contents does not need to be resent over the network (for each down-arrow, etc.)  This method is heuristic and it doesn't detect all scrolls.

By using -noxrecord you disable this speedup. Working of a lan you probably will never notice it.  Working over a slow broadband link you'd probably only notice it because I just described what to look for!

Anyway, glad you have a workaround and let's hope Xorg pushes its fix quickly.

Finally! I erased every error I could find in my logs but was not able to fix my X crashing on me until I found this thread. I have been relying on x11vnc for so long it was the last thing I thought of searching for in connection to this error. 

Thank you! 
/djchester (ubuntu 10.10)

---

### Post by darwin_te on 2010-12-29
> **nLinked said:**
> No problem. You're right, it is more serious than a log out, it just crashes out straight.

**I think I've just fixed it!** Fingers crossed.

I saw [this]("http://ubuntuforums.org/showpost.php?p=9931688&postcount=8") post.

Which led me to "Comment 1" [here]("http://bugs.freedesktop.org/show_bug.cgi?id=30032#c1").

I just added the -noxrecord to the command in the /etc/gdm/Init/Default file. Logged out and in. x11vnc process is started. So far no crash! Am just going to restart the computer and see how it goes.

If it happens again I'll give your method above a test.

What exactly is this -noxrecord doing though?

**EDIT: After a restart, it is still working!**
Adding -noxrecord to the command in the /etc/gdm/Init/Default file has stopped X from crashing out every minute or two after logging in!

This is a relief! Finally all is good and I have a VNC server running.

Thanks for all your help! Will edit original post with solution. Hopefully the X people will fix that bug.

Solved my x11vnc crash too!  I'm using Kubuntu 10.10,

- Nvidia binary driver 260.19.29
- GEForce 8400 GS with dual monitor output
- kernel 2.6.35-24-generic-pae
- x11vnc version 0.9.10 lastmod: 2010-04-28
- X.Org X Server 1.9.0

---

### Post by darwin_te on 2010-12-29
Seems the bug has been reported as a bug to Xorg developers:


[https://bugs.freedesktop.org/show_bug.cgi?id=30032](https://bugs.freedesktop.org/show_bug.cgi?id=30032)

---

### Post by AlwaysLearning on 2011-01-25
> **EDIT 3: SOLVED!**
Post #15 [here]("http://ubuntuforums.org/showpost.php?p=10082455&postcount=15") (same thread) fixes this issue.

Thank you, the [-noxrecord fix]("http://ubuntuforums.org/showpost.php?p=10082455&postcount=15") definitely works.

Finally got around to upgrading from Lucid to Maverick last night and hit this issue, too. Was pounding my head on the desk after uninstalling nVidia/173 to go back to nouveau and it was still crashing.

---

### Post by maxim99 on 2011-02-15
> **nLinked said:**
> 
I just added the -noxrecord to the command in the /etc/gdm/Init/Default file. Logged out and in. x11vnc process is started. So far no crash! Am just going to restart the computer and see how it goes.

Thank you for this. It sorted out the issue quite nicely!

---

### Post by war59312 on 2011-05-15
Hey,

OK I am trying to get x11vnc to start on boot up on Ubuntu 10.10 Server.

Using Webmin I have added this Upstart service:

> # x11vnc
#
# This x11vnc server provides secure remote access (via SSH2) to the desktop.

description  "x11vnc server"

start on local-filesystems
stop on runlevel [!2345]

respawn
respawn limit 10 5
umask 022

exec x11vnc -env FD_XDM=1 -auth guess -display :0 -rfbport 5901 -rfbauth /home/user/.vnc/passwd -forever -localhost -solid black -ncache 10 -ncache_cr -rfbversion 3.6 -permitfiletransfer -ultrafilexfer -xkb -o /media/RAID/x11vnc/x11vnc.log -bg -shared -noxfixes -cursor arrow -arrow 3 -reopen -noxrecordTook me awhile to figure that out. Works OK.

Guess I will explain the options I use in case someone else needs help with this.

> 1.) "-env FD_XDM=1 -auth guess" I got from [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/) . Only way I could find the correct XAUTHORITY file.

2.) "-display :0" Must tell it what display to use. This is the default.

3.) "-rfbport 5901" Port to use. If you don't use then it uses 5900 by default. I got something else running on that port. A back up VNC viewer in fact.

4.) "-rfbauth /home/user/.vnc/passwd" I am using a password for acess. So this is where my password file is stored.

5.) "-forever" Keep x11vnc running forever even after disconnecting.

6.) "-localhost" Only allow localhost connections. I am using SSH2 with forwarding to allow secure remote connections. So only allows access via SSH2.

7.) "-solid black" No need to load background image, so just use black instead.

8.) "-ncache 10 -ncache_cr" See: [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-ncache](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-ncache)

9.) "-rfbversion 3.6 -permitfiletransfer -ultrafilexfer" This tells x11vnc I want to use ultra vnc style file transferring.

10.) "-xkb" Correct keyboard layout, see: [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-xkb](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-xkb)

11.) "-o /media/RAID/x11vnc/x11vnc.log" Location of logging file.

12.) "-bg" See: [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-bg](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-bg)

13.) "-shared" Allows more than 1 viewer at a time. See: [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-shared](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-shared)

14.) "-noxfixes" Without this x11 crashes. See: [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-noxfixes](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-noxfixes)

15.) "-cursor arrow -arrow 3" Use a nicer mouse cursor. Needed since using "-noxfixes" option.

16.) "-reopen" See: [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen)

17.) "-noxrecord" Workaround for "disconnecting bug". Without this option you get automatically logged out after a minute of use or so.The problem is, that for some odd reason though it does NOT start on boot even though I have told it to. I am having to manually start it every time. Lame.

So how do I get it really to run on boot?

I don't understand why it's not working since in Webmin the option "Start at boot time?" is set to "yes". Guess it does not work properly?

That or more than likely an issue with my script. I am pretty much a newbie at this.

Any help would be great.

Thanks,

Will

---

### Post by krunge on 2011-05-15
Are you sure the way you are launching it you want x11vnc to put itself into the background (-bg option)? I don't know about upstart, etc. and whether the application should put itself into the background or not.  If not, get rid of "-bg"

You can get rid of "-rfbversion 3.6 -permitfiletransfer" because "-ultrafilexfer" is an ALIAS for exactly that.

Note that "-reopen" is a somewhat dangerous/unstable scheme. It is a last-ditch effort to try to work around all the bugs in Xorg that cause Xorg to crash.  Note that recent versions of x11vnc try to automatically work around the xfixes problem.

If you are still having problems having it autostart at boot attach the entire log file for a failed case here.

Note that there are more natural ways to have x11vnc start up at boot time on the physical display. See the "Continuously" section here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

---

### Post by krunge on 2011-05-15
> 
Note that there are more natural ways to have x11vnc start up at boot time on the physical display. See the "Continuously" section here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
Oh, BTW what is there in your upstart config that makes sure x11vnc is started AFTER the Xorg X server is started and ready to accept connections?

If your upstart starts x11vnc before the X server is ready x11vnc will have to exit.

The "Continously" section in the FAQ above is a good way to avoid this problem.

For your method you could also add as a kludge "-sleepin 60" to have x11vnc wait 1 minute before trying to connect to the X server. It should be up by then if it is going to come up.

---

### Post by war59312 on 2011-05-17
@krunge Thanks for the tips. Yeah some of those I have been using for years but looks like not required any more, just like you said. :)

And indeed must be the "If your upstart starts x11vnc before the X server is ready x11vnc will have to exit." issue you mentioned.

Since my log now shows:
> 
17/05/2011 00:59:22 passing arg to libvncserver: -rfbport
17/05/2011 00:59:22 passing arg to libvncserver: 5901
17/05/2011 00:59:22 passing arg to libvncserver: -rfbauth
17/05/2011 00:59:22 passing arg to libvncserver: /home/user/.vnc/passwd
17/05/2011 00:59:22 passing arg to libvncserver: -rfbversion
17/05/2011 00:59:22 passing arg to libvncserver: 3.6
17/05/2011 00:59:22 passing arg to libvncserver: -permitfiletransfer
17/05/2011 00:59:22 x11vnc version: 0.9.10 lastmod: 2010-04-28  pid: 1385
17/05/2011 00:59:22 -auth guess: failed for display=':0'**Q.)** Oh, BTW what is there in your upstart config that makes sure x11vnc is  started AFTER the Xorg X server is started and ready to accept  connections?

**A.)** Nope, don't know how to do that.

The FAQ is not really helping me. Just confusing me more. Sad!

The reason I was trying to use a Upstart service was so that I could stop and start it using Webmin ([http://www.webmin.com/](http://www.webmin.com/)).

I now can thanks to your tip. The "-bg" option was indeed breaking it.

So now to figure out how to make the script only start after x.

**Update**: [COLOR=Red]Success! [/COLOR]:D

> [COLOR=Blue]Changed[/COLOR]:

start on local-filesystems

[COLOR=Blue]To[/COLOR]:

start on starting gdm[COLOR=Red]So Final Working Upstart Script Is[/COLOR]:

> # x11vnc
#
# This x11vnc server provides secure remote access (via SSH2) to the desktop.

description  "x11vnc server"

start on starting gdm
stop on runlevel [!2345]

respawn
respawn limit 10 5
umask 022

exec x11vnc -env FD_XDM=1 -auth guess -display :0 -rfbport 5901 -rfbauth /home/user/.vnc/passwd -forever -localhost -solid black -ncache 10 -ncache_cr -ultrafilexfer -xkb -o /media/RAID/x11vnc/x11vnc.log -shared -noxfixes -cursor arrow -arrow 3 -noxrecord

---

### Post by war59312 on 2011-05-18
OK well dang. Now copy and pasting is NOT working.

I have autocutsel installed and running but makes no difference.

Using Ultra VNC as the viewer.

Any ideas?
[B]
Update[/B]: OK figured it out. For some reason it was IN fact not starting correctly. It has to start before x11vnc it seems or wont work.

So wrote another upstart script to make it start after x11vnc. :D

---

### Post by AllGamer on 2011-05-18
it works!

the solution works :D

thx!

> **nLinked said:**
> No problem. You're right, it is more serious than a log out, it just crashes out straight.

**I think I've just fixed it!** Fingers crossed.

I saw [this]("http://ubuntuforums.org/showpost.php?p=9931688&postcount=8") post.

Which led me to "Comment 1" [here]("http://bugs.freedesktop.org/show_bug.cgi?id=30032#c1").

I just added the -noxrecord to the command in the /etc/gdm/Init/Default file. Logged out and in. x11vnc process is started. So far no crash! Am just going to restart the computer and see how it goes.

If it happens again I'll give your method above a test.

What exactly is this -noxrecord doing though?

**EDIT: After a restart, it is still working!**
Adding -noxrecord to the command in the /etc/gdm/Init/Default file has stopped X from crashing out every minute or two after logging in!

This is a relief! Finally all is good and I have a VNC server running.

Thanks for all your help! Will edit original post with solution. Hopefully the X people will fix that bug.

---

### Post by war59312 on 2012-05-02
Hey,

I decided to update to Ubuntu 12.04 Server (from 11.04) since it is a TLS release.

Sadly a few things broke in the upgrade, one of them being x11vnc. :(

Please see my log file below.

Any ideas on how to fix this?

Thanks,

Will

```
02/05/2012 22:59:01 passing arg to libvncserver: -rfbport
02/05/2012 22:59:01 passing arg to libvncserver: 5901
02/05/2012 22:59:01 passing arg to libvncserver: -rfbauth
02/05/2012 22:59:01 passing arg to libvncserver: /home/rob/.vnc/passwd
02/05/2012 22:59:01 passing arg to libvncserver: -rfbversion
02/05/2012 22:59:01 passing arg to libvncserver: 3.6
02/05/2012 22:59:01 passing arg to libvncserver: -permitfiletransfer
02/05/2012 22:59:01 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 22237
/tmp/fd.KderXT: 305: [: -a: unexpected operator
02/05/2012 22:59:02 -auth guess: failed for display=':0'
```

**Update**: Slightly modified working script:

```
# x11vnc
#
# This x11vnc server provides secure remote access (via SSH2) to the desktop.

description "x11vnc server"

start on login-session-start
stop on runlevel [!2345]

respawn
respawn limit 10 5
umask 022

exec x11vnc -env FD_XDM=1 -auth /home/rob/.Xauthority -display :0 -rfbport 5901 -rfbauth /home/rob/.vnc/passwd -forever -localhost -solid black -ncache 10 -ncache_cr -ultrafilexfer -xkb -o /media/RAID/Will/x11vnc/x11vnc.log -shared -noxfixes -cursor arrow -arrow 3 -noxrecord
```

---

