---
title: "Xorg crashes only after boot in Ubuntu 9.04"
date: 2010-08-26
forum: Desktop Environments
---

### Post by wpy1505 on 2010-08-26
Hi,

I have a small issue of Xorg. Every time I boot the ubuntu 9.04, the X will crash immediately after it started. Then, it will start again and shows the login interface. It went well after the second login. I don't know what caused this since there is no error message in /var/log/Xorg.0.log and /var/log/gdm/*. 

Does anyone knows how should I inspect the issue, or know what was going on. Thanks in advance.

---

### Post by wpy1505 on 2010-08-26
I'm using nvidia graphic driver. More detail related to this issue is that at the time that X was suppose to start after a bunch of booting process message, the screen was black and jumped back to the booting messages. Then there is a big nvidia logo showed up on the screen, then the gdm login interface showed up which runs fine after I type the username and password.

The Xorg.0.log and Xorg.0.log.old shows that the Xorg was run twice and the first run crashed at some point. This is quite confusing since I cannot see any error messages from the log. 

The Xorg.0.log.old is here:
[HTML]
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux zigtestdevice 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 26 15:26:14 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) Option "NoTrapSignals" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@3:0:0) nVidia Corporation unknown chipset (0x087d) rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.44  Thu Jul 29 01:55:11 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.44  Thu Jul 29 01:32:42 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseCompositeWrapper" "True"
(**) Aug 26 15:26:24 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 26 15:26:24 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 26 15:26:24 NVIDIA(0):     enabled.
(II) Aug 26 15:26:26 NVIDIA(0): NVIDIA GPU ION (C79) at PCI:3:0:0 (GPU-0)
(--) Aug 26 15:26:26 NVIDIA(0): Memory: 524288 kBytes
(--) Aug 26 15:26:26 NVIDIA(0): VideoBIOS: 62.79.65.00.00
(--) Aug 26 15:26:26 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 26 15:26:26 NVIDIA(0): Connected display device(s) on ION at PCI:3:0:0:
(--) Aug 26 15:26:26 NVIDIA(0):     NEC M40 (DFP-0)
(--) Aug 26 15:26:26 NVIDIA(0): NEC M40 (DFP-0): 330.0 MHz maximum pixel clock
(--) Aug 26 15:26:26 NVIDIA(0): NEC M40 (DFP-0): Internal Dual Link TMDS
(WW) Aug 26 15:26:26 NVIDIA(0): The EDID for NEC M40 (DFP-0) contradicts itself: mode
(WW) Aug 26 15:26:26 NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) Aug 26 15:26:26 NVIDIA(0):     valid HorizSync range (28.000-92.000 kHz) would exclude
(WW) Aug 26 15:26:26 NVIDIA(0):     this mode's HorizSync (27.0 kHz); ignoring HorizSync check
(WW) Aug 26 15:26:26 NVIDIA(0):     for mode "1920x1080".
(WW) Aug 26 15:26:26 NVIDIA(0): The EDID for NEC M40 (DFP-0) contradicts itself: mode
(WW) Aug 26 15:26:26 NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) Aug 26 15:26:26 NVIDIA(0):     valid VertRefresh range (48.000-85.000 Hz) would exclude
(WW) Aug 26 15:26:26 NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) Aug 26 15:26:26 NVIDIA(0):     check for mode "1920x1080".
(WW) Aug 26 15:26:26 NVIDIA(0): The EDID for NEC M40 (DFP-0) contradicts itself: mode
(WW) Aug 26 15:26:26 NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) Aug 26 15:26:26 NVIDIA(0):     valid HorizSync range (28.000-92.000 kHz) would exclude
(WW) Aug 26 15:26:26 NVIDIA(0):     this mode's HorizSync (27.0 kHz); ignoring HorizSync check
(WW) Aug 26 15:26:26 NVIDIA(0):     for mode "1920x1080".
(WW) Aug 26 15:26:26 NVIDIA(0): The EDID for NEC M40 (DFP-0) contradicts itself: mode
(WW) Aug 26 15:26:26 NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) Aug 26 15:26:26 NVIDIA(0):     valid VertRefresh range (48.000-85.000 Hz) would exclude
(WW) Aug 26 15:26:26 NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) Aug 26 15:26:26 NVIDIA(0):     check for mode "1920x1080".
(II) Aug 26 15:26:26 NVIDIA(0): Assigned Display Device: DFP-0
(WW) Aug 26 15:26:26 NVIDIA(0): No valid modes for "1280x800"; removing.
(WW) Aug 26 15:26:26 NVIDIA(0): 
(WW) Aug 26 15:26:26 NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) Aug 26 15:26:26 NVIDIA(0):     "nvidia-auto-select".
(WW) Aug 26 15:26:26 NVIDIA(0): 
(II) Aug 26 15:26:26 NVIDIA(0): Validated modes:
(II) Aug 26 15:26:26 NVIDIA(0):     "nvidia-auto-select"
(II) Aug 26 15:26:26 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Aug 26 15:26:26 NVIDIA(0): DPI set to (54, 54); computed from "UseEdidDpi" X config
(--) Aug 26 15:26:26 NVIDIA(0):     option
(==) Aug 26 15:26:26 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX
(II) Aug 26 15:26:26 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Aug 26 15:26:26 NVIDIA(0): Initialized GPU GART.
(II) Aug 26 15:26:26 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Aug 26 15:26:26 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 26 15:26:26 NVIDIA(0): Initialized X Rendering Acceleration
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
 ddxSigGiveUp: Closing log[/HTML]

---

### Post by wpy1505 on 2010-08-27
I think what the log file shows is that Xorg stopped after the record of "Initializing extension GLX". That's where it should crashed. My system has automatic login setup. But when it crashed, it jumped to timed login. I'm assuming that the only Xorg crashed but gdm worked fine which rebrought up Xorg. Does anyone has any idea?;)

---

### Post by rtimai on 2010-08-27
Wpy1505,

Do you find X running in tty8 instead of the normal tty7? This is happening at random on my system, and when I search for discussions about it, I've been seeing it often connected with X restarts. I too have an nVIDIA card, running the nouveau driver, but I don't think the X restarts is nVIDIA-specific. So far all I find is just obscure developer talk. They're working on it, I guess.

---

### Post by wpy1505 on 2010-08-27
> **rtimai said:**
> Wpy1505,

Do you find X running in tty8 instead of the normal tty7? This is happening at random on my system, and when I search for discussions about it, I've been seeing it often connected with X restarts. I too have an nVIDIA card, running the nouveau driver, but I don't think the X restarts is nVIDIA-specific. So far all I find is just obscure developer talk. They're working on it, I guess.

Hi rtimai,

I don't think my X is running at tty8. It crashed even before it shows up. I feel that it was due to some process which runs at the booting process that somehow killed the xorg because that only happens at the booting.

---

### Post by rtimai on 2010-08-27
On my system, X has been restarting in tty8 instead of the standard tty7 after it crashed during login. I think this is the case with you also, but you didn't answer the question.

You can easily find out where your X desktop is running by pressing Ctrl-Alt-F1 through Ctrl-Alt-F7. You don't need to enter anything at the login prompts you encounter -- just switch screens with the Ctrl-Alt combinations. Ctr-Alt-F7 should put you back at the desktop -- unless it's moved, as I said. Then, you'll probably find it in tty8 (Ctrl-Alt-F8,) which is not normal.

If your desktop is not in tty7, then you have the X restart problem for which developers are already discussing various strategies to deal with this misbehavior. IOW, you don't need to do anything. If not, then maybe you have a different problem.

ADDED: It seems in my case X running in tty8 or tty9 does not occur due to X crashing at login. Rather, it appears to happen if I should logoff, and tty7 is not deallocated to make it available once again. If I simply log off, then log back on. Successive logoff/on moves X to tty8 and then tty9. I haven't seen an occasion when it was moved to tty10 or higher.

A web search for "tty8" yields other inconclusive discussions that mention an irreproducible bug about a running process that prevents tty7 from being deallocated. The bug has been closed and re-opened several times without solution. 

[http://osdir.com/ml/debian-user-debian/2010-02/threads.html#00662](http://osdir.com/ml/debian-user-debian/2010-02/threads.html#00662)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=348033](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=348033)
[http://comments.gmane.org/gmane.linux.debian.user/374025](http://comments.gmane.org/gmane.linux.debian.user/374025)

---

