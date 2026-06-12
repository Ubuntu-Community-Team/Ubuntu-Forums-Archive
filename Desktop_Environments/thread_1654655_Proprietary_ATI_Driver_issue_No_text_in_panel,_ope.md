---
title: "Proprietary ATI Driver issue: No text in panel, openoffice freeze"
date: 2010-12-28
forum: Desktop Environments
---

### Post by shipp on 2010-12-28
Hello all.  Hoping someone knows what the hell to do in this instance.  I've just upgraded to Maverick Meerkat on a new Dell system and everything was working just peachy until today.  I've spent the last couple days tweaking my ubuntu so something I did made it so that open office only allows me to click inside it and write text some of the time, and very slowly.  And then my panel doesn't show the text of the main menu headers.  If i click on them though, the menu shows up with text inside it totally in tact.

The problem disappears when I disable the additional driver (preferences-additional drivers-remove).  And recurs when I activate it.  

So, suspect its a conflict with xorg and the proprietary driver.  I'm running emerald with window decorations (theme is neon glow)  - changing the emerald theme doesn't affect the problem.  Im also running compiz-fusion.  

My graphics card is an ATI Radeon HD 545 (also known as the Cedar Pro) and the proprietary driver to add 3D effects (that i suspect is the culprit) is the FGLRX.  I don't know much about drivers and graphics cards because im not a gamer, so bear with me.

I read somewhere that 

"fglrx (the proprietary AMD/ATI linux driver) no longer supports any card older than the [[COLOR=#05408f][COLOR=#05408F ! important][FONT=Arial][COLOR=#05408F ! important][FONT=Arial]HD[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.techspot.com/vb/topic157756.html#")  series (so that's all the early 7xxx/8xxx/9xxx Radeons and X series  Radeons out).  Earlier versions of fglrx that do support those chips  don't support the latest xorg - so in a nutshell fglrx is not an option  for you.

You will have to use the xorg radeon driver, which is normally very good  in fact - which makes me suspect that it may not be in use on your  system for some reason."  

Which makes me think that my ubuntu might think I have an older graphics card and is using the older driver instead of one that is more compatible.  So, I did what person above suggested and entered some command lines, then i got the following returned in my terminal, but i have no idea what it means.  Could someone tell me if i'm on the right path here.  Is it a compatibility problem.  If so, can i update?   Also had problems running cairo dock so i uninstalled it (it worked but was all flashy and sketch looking)

[    15.693] (II) Loading extension ATIFGLRXDRI
[    15.693] (II) fglrx(0): doing swlDriScreenInit
[    15.693] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    15.693] ukiDynamicMajor: found major device number 249
[    15.693] ukiDynamicMajor: found major device number 249
[    15.693] ukiDynamicMajor: found major device number 249
[    15.693] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.693] ukiOpenDevice: node name is /dev/ati/card0
[    15.693] ukiOpenDevice: open result is 17, (OK)
[    15.693] ukiOpenByBusid: ukiOpenMinor returns 17
[    15.693] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.693] (II) fglrx(0): [uki] DRM interface version 1.0
[    15.693] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    15.694] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    15.694] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb688c000
[    15.694] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    15.694] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    15.694] (II) fglrx(0): swlDriScreenInit done
[    15.694] (II) fglrx(0): Kernel Module Version Information:
[    15.694] (II) fglrx(0):     Name: fglrx
[    15.694] (II) fglrx(0):     Version: 8.78.30
[    15.694] (II) fglrx(0):     Date: Sep 20 2010
[    15.694] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    15.694] (II) fglrx(0): Kernel Module version matches driver.
[    15.694] (II) fglrx(0): Kernel Module Build Time Information:
[    15.694] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.35-24-generic-pae
[    15.694] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    15.694] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    15.694] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    15.694] (II) fglrx(0): [uki] register handle = 0x00004000
[    15.714] (II) fglrx(0): DRI initialization successfull
[    15.714] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    15.742] (II) fglrx(0): FBMM initialized for area (0,0)-(1920,2304)
[    15.742] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
[    15.742] (II) fglrx(0): Largest offscreen area available: 1920 x 384
[    15.759] (==) fglrx(0): Backing store disabled
[    15.759] (II) Loading extension FGLRXEXTENSION
[    15.759] (==) fglrx(0): DPMS enabled
[    15.759] (II) fglrx(0): Initialized in-driver Xinerama extension
[    15.759] (**) fglrx(0): Textured Video is enabled.
[    15.759] (II) LoadModule: "glesx"
[    15.759] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    16.090] (II) Module glesx: vendor="X.Org Foundation"
[    16.090]     compiled for 1.8.99.905, module version = 1.0.0
[    16.090] (II) Loading extension GLESX
[    16.090] (II) fglrx(0): GLESX enableFlags = 592
[    16.090] (II) fglrx(0): GLESX is enabled
[    16.090] (II) fglrx(0): Acceleration enabled
[    16.090] (II) LoadModule: "amdxmm"
[    16.090] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    16.104] (II) Module amdxmm: vendor="X.Org Foundation"
[    16.104]     compiled for 1.8.99.905, module version = 1.0.0
[    16.122] (II) Loading extension AMDXVOPL
[    16.158] (II) fglrx(0): UVD2 feature is available
[    16.229] (II) fglrx(0): Enable composite support successfully
[    16.229] (II) fglrx(0): X context handle = 0x1
[    16.229] (II) fglrx(0): [DRI] installation complete
[    16.229] (==) fglrx(0): Silken mouse enabled
[    16.231] (==) fglrx(0): Using HW cursor of display infrastructure!
[    16.231] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    17.373] (--) RandR disabled
[    17.373] (II) Initializing built-in extension Generic Event Extension
[    17.373] (II) Initializing built-in extension SHAPE
[    17.373] (II) Initializing built-in extension MIT-SHM
[    17.373] (II) Initializing built-in extension XInputExtension
[    17.373] (II) Initializing built-in extension XTEST
[    17.373] (II) Initializing built-in extension BIG-REQUESTS
[    17.373] (II) Initializing built-in extension SYNC
[    17.373] (II) Initializing built-in extension XKEYBOARD
[    17.373] (II) Initializing built-in extension XC-MISC
[    17.373] (II) Initializing built-in extension SECURITY
[    17.373] (II) Initializing built-in extension XINERAMA
[    17.373] (II) Initializing built-in extension XFIXES
[    17.373] (II) Initializing built-in extension RENDER
[    17.373] (II) Initializing built-in extension RANDR
[    17.373] (II) Initializing built-in extension COMPOSITE
[    17.373] (II) Initializing built-in extension DAMAGE
[    17.373] (II) Initializing built-in extension GESTURE
[    17.454] ukiDynamicMajor: found major device number 249
[    17.454] ukiDynamicMajor: found major device number 249
[    17.454] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    17.454] ukiOpenDevice: node name is /dev/ati/card0
[    17.454] ukiOpenDevice: open result is 18, (OK)
[    17.454] ukiOpenByBusid: ukiOpenMinor returns 18
[    17.454] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    18.609] (II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
[    18.609] (II) GLX: Initialized DRI GL provider for screen 0
[    18.609] (II) fglrx(0): Enable the clock gating!
[    18.609] (II) fglrx(0): Setting screen physical size to 507 x 285
[    18.759] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.771] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.771] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.771] (II) LoadModule: "evdev"
[    18.771] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.801] (II) Module evdev: vendor="X.Org Foundation"
[    18.801]     compiled for 1.9.0, module version = 2.3.2
[    18.801]     Module class: X.Org XInput Driver
[    18.801]     ABI class: X.Org XInput driver, version 11.0
[    18.801] (**) Power Button: always reports core events
[    18.801] (**) Power Button: Device: "/dev/input/event1"
[    18.820] (II) Power Button: Found keys
[    18.820] (II) Power Button: Configuring as keyboard
[    18.820] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.820] (**) Option "xkb_rules" "evdev"
[    18.820] (**) Option "xkb_model" "pc105"
[    18.820] (**) Option "xkb_layout" "us"
[    18.821] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.821] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.821] (**) Power Button: always reports core events
[    18.821] (**) Power Button: Device: "/dev/input/event0"
[    18.832] (II) Power Button: Found keys
[    18.832] (II) Power Button: Configuring as keyboard
[    18.832] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.832] (**) Option "xkb_rules" "evdev"
[    18.832] (**) Option "xkb_model" "pc105"
[    18.832] (**) Option "xkb_layout" "us"
[    18.834] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event2)
[    18.834] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
[    18.834] (**) Logitech 2.4GHz Cordless Desktop: always reports core events
[    18.834] (**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event2"
[    18.844] (II) Logitech 2.4GHz Cordless Desktop: Found keys
[    18.844] (II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
[    18.844] (II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
[    18.844] (**) Option "xkb_rules" "evdev"
[    18.844] (**) Option "xkb_model" "pc105"
[    18.844] (**) Option "xkb_layout" "us"
[    18.845] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event3)
[    18.845] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev pointer catchall"
[    18.845] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
[    18.845] (**) Logitech 2.4GHz Cordless Desktop: always reports core events
[    18.845] (**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event3"
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Found 12 mouse buttons
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Found scroll wheel(s)
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Found relative axes
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Found x and y relative axes
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Found absolute axes
[    18.864] (II) evdev-grail: failed to open grail, no gesture support
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Found keys
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Configuring as mouse
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
[    18.864] (**) Logitech 2.4GHz Cordless Desktop: YAxisMapping: buttons 4 and 5
[    18.864] (**) Logitech 2.4GHz Cordless Desktop: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.864] (II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
[    18.864] (**) Option "xkb_rules" "evdev"
[    18.864] (**) Option "xkb_model" "pc105"
[    18.864] (**) Option "xkb_layout" "us"
[    18.864] (II) Logitech 2.4GHz Cordless Desktop: initialized for relative axes.
[    18.865] (WW) Logitech 2.4GHz Cordless Desktop: ignoring absolute axes.
[    18.865] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/mouse0)
[    18.865] (II) No input driver/identifier specified (ignoring)
[    18.874] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    19.970] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[    19.970] (II) fglrx(0): Using EDID range info for horizontal sync
[    19.970] (II) fglrx(0): Using EDID range info for vertical refresh
[    19.970] (II) fglrx(0): Printing DDC gathered Modelines:
[    19.970] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    19.970] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.970] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    19.970] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.970] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    19.970] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    19.970] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    19.970] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.970] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    19.970] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    19.970] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.970] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    19.985] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[    19.985] (II) fglrx(0): Using hsync ranges from config file
[    19.985] (II) fglrx(0): Using vrefresh ranges from config file
[    19.985] (II) fglrx(0): Printing DDC gathered Modelines:
[    19.985] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    19.985] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.985] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    19.985] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.985] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    19.985] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    19.985] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    19.985] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.985] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    19.985] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    19.985] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.985] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    20.008] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[    20.008] (II) fglrx(0): Using hsync ranges from config file
[    20.008] (II) fglrx(0): Using vrefresh ranges from config file
[    20.008] (II) fglrx(0): Printing DDC gathered Modelines:
[    20.008] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    20.008] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.008] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.008] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.008] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.008] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.008] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.008] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.008] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.008] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.008] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.008] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    20.021] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[    20.021] (II) fglrx(0): Using hsync ranges from config file
[    20.021] (II) fglrx(0): Using vrefresh ranges from config file
[    20.021] (II) fglrx(0): Printing DDC gathered Modelines:
[    20.021] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    20.021] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.021] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.021] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.021] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.021] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.021] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.021] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.021] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.021] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.021] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.021] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[   705.614] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[   705.614] (II) fglrx(0): Using hsync ranges from config file
[   705.614] (II) fglrx(0): Using vrefresh ranges from config file
[   705.614] (II) fglrx(0): Printing DDC gathered Modelines:
[   705.614] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   705.614] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   705.614] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   705.614] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   705.614] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   705.614] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   705.614] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   705.614] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   705.614] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   705.614] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   705.614] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   705.614] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[   705.631] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[   705.631] (II) fglrx(0): Using hsync ranges from config file
[   705.631] (II) fglrx(0): Using vrefresh ranges from config file
[   705.631] (II) fglrx(0): Printing DDC gathered Modelines:
[   705.631] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   705.631] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   705.631] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   705.631] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   705.631] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   705.631] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   705.631] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   705.631] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   705.631] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   705.631] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   705.631] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   705.631] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[   705.646] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[   705.646] (II) fglrx(0): Using hsync ranges from config file
[   705.646] (II) fglrx(0): Using vrefresh ranges from config file
[   705.646] (II) fglrx(0): Printing DDC gathered Modelines:
[   705.646] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   705.646] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   705.646] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   705.646] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   705.646] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   705.646] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   705.646] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   705.646] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   705.646] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   705.646] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   705.646] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   705.646] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[   705.661] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[   705.661] (II) fglrx(0): Using hsync ranges from config file
[   705.662] (II) fglrx(0): Using vrefresh ranges from config file
[   705.662] (II) fglrx(0): Printing DDC gathered Modelines:
[   705.662] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   705.662] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   705.662] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   705.662] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   705.662] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   705.662] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   705.662] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   705.662] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   705.662] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   705.662] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   705.662] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   705.662] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[   711.996] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[   711.996] (II) fglrx(0): Using hsync ranges from config file
[   711.996] (II) fglrx(0): Using vrefresh ranges from config file
[   711.996] (II) fglrx(0): Printing DDC gathered Modelines:
[   711.996] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   711.996] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   711.996] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   711.996] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   711.996] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   711.996] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   711.996] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   711.996] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   711.996] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   711.996] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   711.996] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   711.996] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[   716.714] (II) fglrx(0): EDID vendor "DEL", prod id 41062
[   716.714] (II) fglrx(0): Using hsync ranges from config file
[   716.714] (II) fglrx(0): Using vrefresh ranges from config file
[   716.714] (II) fglrx(0): Printing DDC gathered Modelines:
[   716.714] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   716.714] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   716.714] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   716.714] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   716.714] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   716.714] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   716.714] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   716.714] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   716.714] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   716.714] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   716.714] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   716.714] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)

~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

~$ glxinfo | grep direct
direct rendering: Yes
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access,

---

### Post by shipp on 2011-01-13
Never mind, I reinstalled all of 10.10 and it fixed the problem.  I think it may have been a compatibility issue with kdenlive, but i dont need it anymore, so we'll never know.  Peace.

---

