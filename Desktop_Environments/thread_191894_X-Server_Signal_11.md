---
title: "X-Server Signal 11"
date: 2006-06-08
forum: Desktop Environments
---

### Post by robinl on 2006-06-08
Hi I've enjoyed xgl+compiz for 2 days wonderfully before deciding to switch to cvs repos and fix my wacom tablet in xorg.conf. However after that when I restart whenever i start compiz the whole x-server just crashes and goes back to the initial log on screen. The log (attached) says signal 11 but not much other information is provided. I'm on NVIDIA 6600GT and installed latest driver using method 2 just in case you want to know. Thanks for helping

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux robin-desktop 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686
Build Date: 16 March 2006
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  8 20:56:17 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "AOC LM721"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "pad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.2
    X.Org Video Driver: 0.8
    X.Org XInput driver : 0.5
    X.Org Server Extension : 0.2
    X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

... (skipped because of length limitation)

(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.0.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf4004000 - 0xf4007fff (0x4000) MX[b]
    [5] -1    0    0xf4009000 - 0xf40097ff (0x800) MX[b]
    [6] -1    0    0xf4008000 - 0xf40081ff (0x200) MX[b]
    [7] -1    0    0xf4000000 - 0xf4003fff (0x4000) MX[b]
    [8] -1    0    0xf400a000 - 0xf400a0ff (0x100) MX[b]
    [9] -1    0    0xf5001000 - 0xf5001fff (0x1000) MX[b]
    [10] -1    0    0xf5005000 - 0xf50050ff (0x100) MX[b]
    [11] -1    0    0xf5004000 - 0xf5004fff (0x1000) MX[b]
    [12] -1    0    0xf5003000 - 0xf5003fff (0x1000) MX[b]
    [13] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
    [14] -1    0    0xf1000000 - 0xf1ffffff (0x1000000) MX[b](B)
    [15] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [16] -1    0    0xf0000000 - 0xf0ffffff (0x1000000) MX[b](B)
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x0000c000 - 0x0000c00f (0x10) IX[b]
    [20] -1    0    0x0000bc00 - 0x0000bc03 (0x4) IX[b]
    [21] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [22] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [23] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [24] -1    0    0x0000ac00 - 0x0000ac0f (0x10) IX[b]
    [25] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [26] -1    0    0x0000a410 - 0x0000a417 (0x8) IX[b]
    [27] -1    0    0x0000a000 - 0x0000a003 (0x4) IX[b]
    [28] -1    0    0x00009c10 - 0x00009c17 (0x8) IX[b]
    [29] -1    0    0x00009800 - 0x000098ff (0x100) IX[b]
    [30] -1    0    0x00009400 - 0x000094ff (0x100) IX[b]
    [31] -1    0    0x00009000 - 0x00009007 (0x8) IX[b]
    [32] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [33] -1    0    0x0000e000 - 0x0000e07f (0x80) IX[b]
    [34] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b]
    [35] -1    0    0x00002000 - 0x0000203f (0x40) IX[b]
    [36] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[b]
    [37] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xf4004000 - 0xf4007fff (0x4000) MX[b]
    [5] -1    0    0xf4009000 - 0xf40097ff (0x800) MX[b]
    [6] -1    0    0xf4008000 - 0xf40081ff (0x200) MX[b]
    [7] -1    0    0xf4000000 - 0xf4003fff (0x4000) MX[b]
    [8] -1    0    0xf400a000 - 0xf400a0ff (0x100) MX[b]
    [9] -1    0    0xf5001000 - 0xf5001fff (0x1000) MX[b]
    [10] -1    0    0xf5005000 - 0xf50050ff (0x100) MX[b]
    [11] -1    0    0xf5004000 - 0xf5004fff (0x1000) MX[b]
    [12] -1    0    0xf5003000 - 0xf5003fff (0x1000) MX[b]
    [13] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
    [14] -1    0    0xf1000000 - 0xf1ffffff (0x1000000) MX[b](B)
    [15] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [16] -1    0    0xf0000000 - 0xf0ffffff (0x1000000) MX[b](B)
    [17] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [18] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [19] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [22] -1    0    0x0000c000 - 0x0000c00f (0x10) IX[b]
    [23] -1    0    0x0000bc00 - 0x0000bc03 (0x4) IX[b]
    [24] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [25] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [26] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [27] -1    0    0x0000ac00 - 0x0000ac0f (0x10) IX[b]
    [28] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [29] -1    0    0x0000a410 - 0x0000a417 (0x8) IX[b]
    [30] -1    0    0x0000a000 - 0x0000a003 (0x4) IX[b]
    [31] -1    0    0x00009c10 - 0x00009c17 (0x8) IX[b]
    [32] -1    0    0x00009800 - 0x000098ff (0x100) IX[b]
    [33] -1    0    0x00009400 - 0x000094ff (0x100) IX[b]
    [34] -1    0    0x00009000 - 0x00009007 (0x8) IX[b]
    [35] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [36] -1    0    0x0000e000 - 0x0000e07f (0x80) IX[b]
    [37] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b]
    [38] -1    0    0x00002000 - 0x0000203f (0x40) IX[b]
    [39] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[b]
    [40] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [41] 0    0    0xf20003b0 - 0xf20003bb (0xc) IS[b]
    [42] 0    0    0xf20003c0 - 0xf20003df (0x20) IS[b]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.27.13
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     AOC LM720/LM720A (DFP-0)
(--) NVIDIA(0): AOC LM720/LM720A (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): AOC LM720/LM720A (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xf1000000 - 0xf1ffffff (0x1000000) MX[b]
    [1] 0    0    0xe0000000 - 0xefffffff (0x10000000) MX[b]
    [2] 0    0    0xf0000000 - 0xf0ffffff (0x1000000) MX[b]
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [7] -1    0    0xf4004000 - 0xf4007fff (0x4000) MX[b]
    [8] -1    0    0xf4009000 - 0xf40097ff (0x800) MX[b]
    [9] -1    0    0xf4008000 - 0xf40081ff (0x200) MX[b]
    [10] -1    0    0xf4000000 - 0xf4003fff (0x4000) MX[b]
    [11] -1    0    0xf400a000 - 0xf400a0ff (0x100) MX[b]
    [12] -1    0    0xf5001000 - 0xf5001fff (0x1000) MX[b]
    [13] -1    0    0xf5005000 - 0xf50050ff (0x100) MX[b]
    [14] -1    0    0xf5004000 - 0xf5004fff (0x1000) MX[b]
    [15] -1    0    0xf5003000 - 0xf5003fff (0x1000) MX[b]
    [16] -1    0    0xd0000000 - 0xcfffffff (0x0) MX[b]O
    [17] -1    0    0xf1000000 - 0xf1ffffff (0x1000000) MX[b](B)
    [18] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [19] -1    0    0xf0000000 - 0xf0ffffff (0x1000000) MX[b](B)
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [24] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [25] -1    0    0x0000c000 - 0x0000c00f (0x10) IX[b]
    [26] -1    0    0x0000bc00 - 0x0000bc03 (0x4) IX[b]
    [27] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b]
    [28] -1    0    0x0000b400 - 0x0000b403 (0x4) IX[b]
    [29] -1    0    0x0000b000 - 0x0000b007 (0x8) IX[b]
    [30] -1    0    0x0000ac00 - 0x0000ac0f (0x10) IX[b]
    [31] -1    0    0x0000a800 - 0x0000a803 (0x4) IX[b]
    [32] -1    0    0x0000a410 - 0x0000a417 (0x8) IX[b]
    [33] -1    0    0x0000a000 - 0x0000a003 (0x4) IX[b]
    [34] -1    0    0x00009c10 - 0x00009c17 (0x8) IX[b]
    [35] -1    0    0x00009800 - 0x000098ff (0x100) IX[b]
    [36] -1    0    0x00009400 - 0x000094ff (0x100) IX[b]
    [37] -1    0    0x00009000 - 0x00009007 (0x8) IX[b]
    [38] -1    0    0x0000f000 - 0x0000f00f (0x10) IX[b]
    [39] -1    0    0x0000e000 - 0x0000e07f (0x80) IX[b]
    [40] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b]
    [41] -1    0    0x00002000 - 0x0000203f (0x40) IX[b]
    [42] -1    0    0x00001c00 - 0x00001c3f (0x40) IX[b]
    [43] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [44] 0    0    0xf20003b0 - 0xf20003bb (0xc) IS[b]
    [45] 0    0    0xf20003c0 - 0xf20003df (0x20) IS[b]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "intl"
(**) Generic Keyboard: XkbLayout: "intl"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Configured Mouse: Device: "/dev/input/mouse1"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mouse1"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) stylus: reading USB link
(II) xf86WcmSetPressureCurve: setting to 50,0 100,50
(**) WACOM: PressCurve 50,0,100,50
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) cursor: reading USB link
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) eraser: reading USB link
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(**) pad device is /dev/input/wacom
(**) pad is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) pad: reading USB link
(**) Option "BaudRate" "9600"
(**) pad: serial speed 9600
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom USB Intuos3 tablet speed=9600 maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080 suppress=2 tilt=disabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(==) Wacom device "pad" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /usr/bin/X11/X [0x813e70e]
3: /usr/bin/X11/X(Dispatch+0x19e) [0x8085d26]
4: /usr/bin/X11/X(main+0x47c) [0x806e0a8]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7db1ea2]
6: /usr/bin/X11/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting

```

---

### Post by robinl on 2006-06-09
Turns out that my driver is somehow corrupted... A reinstallation of the NVIDIA driver fixed the problem.

---

