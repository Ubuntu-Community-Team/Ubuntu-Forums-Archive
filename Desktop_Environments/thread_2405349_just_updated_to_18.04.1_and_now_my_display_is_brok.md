---
title: "just updated to 18.04.1 and now my display is broken"
date: 2018-11-04
forum: Desktop Environments
---

### Post by pschwa363 on 2018-11-04
So i recently went through a bumpy process updating from 16.04 to 18.04. After updating, I began having problems with my display. they are as follows:

1) Upon startup, the screen goes black when i get to the screen for user sign in. Currently, I get past this by hooking up a second monitor, after which the display on my laptop screen becomes somewhat functional.

2) I have been having some troubles getting the screen to stay in landscape mode. I have an "all in one" (at least I believe that's the correct term) model of laptop. When I flip the screen all the way back to use it as a tablet, I have been having troubles with it switching between landscape and portrait configuration. Currently, I lock the autorotation via the drop down in the top right of my desktop screen.

3) My mouse behaves erratically, will leave some trails that don't go away until the page I'm on is refreshed, and i can't use right click functions on my touchpad. Currently I am using a USB mouse to get past this issue.

My knowledge of computer troubleshooting and fixing is very limited, so all I know is that it likely is some issue with the driver, but beyond that I'm clueless

---

### Post by Bashing-om on 2018-11-04
pschwa363; Hello -

What does X think ?
```

cat /var/log/Xorg.0.log

```
see if there are drivers loaded for the display card(s), mouse, and keyboard .

[INDENT][INDENT]good place to start
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-04
sorry for the incoming wall of text

```
[    47.119] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[    47.119] X Protocol Version 11, Revision 0
[    47.119] Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
[    47.119] Current Operating System: Linux prestons-laptop 4.15.0-38-generic #41~16.04.1-Ubuntu SMP Wed Oct 10 20:16:04 UTC 2018 x86_64
[    47.119] Kernel command line: BOOT_IMAGE=/vmlinuz-4.15.0-38-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    47.119] Build Date: 25 October 2018  04:13:49PM
[    47.119] xorg-server 2:1.19.6-1ubuntu4.1~16.04.2 (For technical support please see http://www.ubuntu.com/support) 
[    47.119] Current version of pixman: 0.33.6
[    47.119]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    47.119] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    47.120] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  3 22:24:40 2018
[    47.121] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    47.127] (==) No Layout section.  Using the first Screen section.
[    47.127] (==) No screen section available. Using defaults.
[    47.127] (**) |-->Screen "Default Screen Section" (0)
[    47.127] (**) |   |-->Monitor "<default monitor>"
[    47.129] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    47.129] (==) Automatically adding devices
[    47.129] (==) Automatically enabling devices
[    47.129] (==) Automatically adding GPU devices
[    47.129] (==) Automatically binding GPU devices
[    47.129] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    47.136] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    47.136]     Entry deleted from font path.
[    47.137] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    47.137]     Entry deleted from font path.
[    47.137] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    47.137]     Entry deleted from font path.
[    47.137] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    47.137]     Entry deleted from font path.
[    47.137] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    47.137]     Entry deleted from font path.
[    47.137] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    47.137] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    47.137] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    47.141] (II) Loader magic: 0x55fa54f76e00
[    47.141] (II) Module ABI versions:
[    47.141]     X.Org ANSI C Emulation: 0.4
[    47.141]     X.Org Video Driver: 23.0
[    47.141]     X.Org XInput driver : 24.1
[    47.141]     X.Org Server Extension : 10.0
[    47.146] (++) using VT number 7

[    47.146] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    47.151] (II) xfree86: Adding drm device (/dev/dri/card0)
[    47.161] (--) PCI:*(0:0:2:0) 8086:22b1:1043:1c4d rev 33, Mem @ 0x80000000/16777216, 0x90000000/268435456, I/O @ 0x0000f000/64, BIOS @ 0x????????/131072
[    47.162] (II) LoadModule: "glx"
[    47.186] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    47.242] (II) Module glx: vendor="X.Org Foundation"
[    47.242]     compiled for 1.19.6, module version = 1.0.0
[    47.242]     ABI class: X.Org Server Extension, version 10.0
[    47.242] (==) Matched modesetting as autoconfigured driver 0
[    47.242] (==) Matched fbdev as autoconfigured driver 1
[    47.242] (==) Matched vesa as autoconfigured driver 2
[    47.242] (==) Assigned the driver to the xf86ConfigLayout
[    47.242] (II) LoadModule: "modesetting"
[    47.243] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    47.250] (II) Module modesetting: vendor="X.Org Foundation"
[    47.250]     compiled for 1.19.6, module version = 1.19.6
[    47.250]     Module class: X.Org Video Driver
[    47.250]     ABI class: X.Org Video Driver, version 23.0
[    47.250] (II) LoadModule: "fbdev"
[    47.251] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    47.256] (II) Module fbdev: vendor="X.Org Foundation"
[    47.256]     compiled for 1.19.3, module version = 0.4.4
[    47.256]     Module class: X.Org Video Driver
[    47.256]     ABI class: X.Org Video Driver, version 23.0
[    47.256] (II) LoadModule: "vesa"
[    47.256] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    47.258] (II) Module vesa: vendor="X.Org Foundation"
[    47.258]     compiled for 1.19.3, module version = 2.3.4
[    47.258]     Module class: X.Org Video Driver
[    47.258]     ABI class: X.Org Video Driver, version 23.0
[    47.258] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    47.258] (II) FBDEV: driver for framebuffer: fbdev
[    47.258] (II) VESA: driver for VESA chipsets: vesa
[    47.259] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[    47.275] (II) modeset(0): using drv /dev/dri/card0
[    47.275] (WW) Falling back to old probe method for fbdev
[    47.276] (II) Loading sub module "fbdevhw"
[    47.276] (II) LoadModule: "fbdevhw"
[    47.276] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    47.277] (II) Module fbdevhw: vendor="X.Org Foundation"
[    47.277]     compiled for 1.19.6, module version = 0.0.2
[    47.277]     ABI class: X.Org Video Driver, version 23.0
[    47.277] (WW) Falling back to old probe method for vesa
[    47.278] (II) modeset(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    47.278] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[    47.278] (==) modeset(0): RGB weight 888
[    47.278] (==) modeset(0): Default visual is TrueColor
[    47.278] (II) Loading sub module "glamoregl"
[    47.278] (II) LoadModule: "glamoregl"
[    47.278] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    47.299] (II) Module glamoregl: vendor="X.Org Foundation"
[    47.299]     compiled for 1.19.6, module version = 1.0.0
[    47.299]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.299] (II) glamor: OpenGL accelerated X.org driver based.
[    47.416] (II) glamor: EGL version 1.4 (DRI2):
[    47.488] (II) modeset(0): glamor initialized
[    47.490] (II) modeset(0): Output eDP-1 has no monitor section
[    47.803] (II) modeset(0): Output DP-1 has no monitor section
[    48.068] (II) modeset(0): Output HDMI-1 has no monitor section
[    48.072] (II) modeset(0): Output DP-2 has no monitor section
[    48.081] (II) modeset(0): Output HDMI-2 has no monitor section
[    48.082] (II) modeset(0): EDID for output eDP-1
[    48.082] (II) modeset(0): Manufacturer: IVO  Model: 48c  Serial#: 0
[    48.082] (II) modeset(0): Year: 2015  Week: 10
[    48.082] (II) modeset(0): EDID Version: 1.4
[    48.082] (II) modeset(0): Digital Display Input
[    48.082] (II) modeset(0): 6 bits per channel
[    48.083] (II) modeset(0): Digital interface is DisplayPort
[    48.083] (II) modeset(0): Max Image Size [cm]: horiz.: 26  vert.: 14
[    48.083] (II) modeset(0): Gamma: 2.20
[    48.083] (II) modeset(0): No DPMS capabilities specified
[    48.083] (II) modeset(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    48.083] (II) modeset(0): First detailed timing is preferred mode
[    48.083] (II) modeset(0): Preferred mode is native pixel format and refresh rate
[    48.083] (II) modeset(0): redX: 0.588 redY: 0.329   greenX: 0.302 greenY: 0.557
[    48.083] (II) modeset(0): blueX: 0.176 blueY: 0.103   whiteX: 0.312 whiteY: 0.328
[    48.083] (II) modeset(0): Manufacturer's mask: 0
[    48.083] (II) modeset(0): Supported detailed timing:
[    48.083] (II) modeset(0): clock: 70.5 MHz   Image Size:  256 x 144 mm
[    48.083] (II) modeset(0): h_active: 1366  h_sync: 1406  h_sync_end 1438 h_blank_end 1502 h_border: 0
[    48.083] (II) modeset(0): v_active: 768  v_sync: 773  v_sync_end 778 v_blanking: 782 v_border: 0
[    48.083] (II) modeset(0):  InfoVision
[    48.083] (II) modeset(0):  M116NWR4 R1
[    48.083] (II) modeset(0): EDID (in hex):
[    48.083] (II) modeset(0):     00ffffffffffff0026cf8c0400000000
[    48.083] (II) modeset(0):     0a190104951a0e780a961096544d8e2d
[    48.083] (II) modeset(0):     1a505400000001010101010101010101
[    48.083] (II) modeset(0):     010101010101871b568850000e302820
[    48.083] (II) modeset(0):     55000090100000190000000000000000
[    48.083] (II) modeset(0):     00000000000000000000000000fe0049
[    48.083] (II) modeset(0):     6e666f566973696f6e0a2020000000fe
[    48.083] (II) modeset(0):     004d3131364e575234205231200a0029
[    48.084] (II) modeset(0): Printing probed modes for output eDP-1
[    48.084] (II) modeset(0): Modeline "1366x768"x60.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    48.084] (II) modeset(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    48.084] (II) modeset(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    48.084] (II) modeset(0): Modeline "1280x720"x120.0  156.12  1280 1376 1512 1744  720 721 724 746 doublescan -hsync +vsync (89.5 kHz d)
[    48.084] (II) modeset(0): Modeline "1280x720"x120.0  120.75  1280 1304 1320 1360  720 721 724 740 doublescan +hsync -vsync (88.8 kHz d)
[    48.084] (II) modeset(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz d)
[    48.084] (II) modeset(0): Modeline "1280x720"x59.7   63.75  1280 1328 1360 1440  720 723 728 741 +hsync -vsync (44.3 kHz d)
[    48.084] (II) modeset(0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    48.084] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    48.084] (II) modeset(0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    48.084] (II) modeset(0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    48.084] (II) modeset(0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    48.084] (II) modeset(0): Modeline "1024x576"x119.9   98.50  1024 1092 1200 1376  576 577 580 597 doublescan -hsync +vsync (71.6 kHz d)
[    48.084] (II) modeset(0): Modeline "1024x576"x119.9   78.38  1024 1048 1064 1104  576 577 580 592 doublescan +hsync -vsync (71.0 kHz d)
[    48.084] (II) modeset(0): Modeline "1024x576"x59.9   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync (35.9 kHz d)
[    48.084] (II) modeset(0): Modeline "1024x576"x59.8   42.00  1024 1072 1104 1184  576 579 584 593 +hsync -vsync (35.5 kHz d)
[    48.084] (II) modeset(0): Modeline "960x600"x119.9   96.62  960 1028 1128 1296  600 601 604 622 doublescan -hsync +vsync (74.6 kHz d)
[    48.084] (II) modeset(0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    48.084] (II) modeset(0): Modeline "960x540"x119.9   86.50  960 1024 1124 1288  540 541 544 560 doublescan -hsync +vsync (67.2 kHz d)
[    48.084] (II) modeset(0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    48.084] (II) modeset(0): Modeline "960x540"x59.6   40.75  960 992 1088 1216  540 543 548 562 -hsync +vsync (33.5 kHz d)
[    48.084] (II) modeset(0): Modeline "960x540"x59.8   37.25  960 1008 1040 1120  540 543 548 556 +hsync -vsync (33.3 kHz d)
[    48.084] (II) modeset(0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    48.084] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    48.084] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    48.084] (II) modeset(0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    48.084] (II) modeset(0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    48.085] (II) modeset(0): Modeline "864x486"x59.9   32.50  864 888 968 1072  486 489 494 506 -hsync +vsync (30.3 kHz d)
[    48.085] (II) modeset(0): Modeline "864x486"x59.6   30.50  864 912 944 1024  486 489 494 500 +hsync -vsync (29.8 kHz d)
[    48.085] (II) modeset(0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    48.085] (II) modeset(0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    48.085] (II) modeset(0): Modeline "800x450"x119.9   59.12  800 848 928 1056  450 451 454 467 doublescan -hsync +vsync (56.0 kHz d)
[    48.085] (II) modeset(0): Modeline "800x450"x119.6   48.75  800 824 840 880  450 451 454 463 doublescan +hsync -vsync (55.4 kHz d)
[    48.085] (II) modeset(0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    48.085] (II) modeset(0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    48.085] (II) modeset(0): Modeline "700x450"x119.9   51.75  700 740 812 924  450 451 456 467 doublescan -hsync +vsync (56.0 kHz d)
[    48.085] (II) modeset(0): Modeline "700x450"x119.8   43.25  700 724 740 780  450 451 456 463 doublescan +hsync -vsync (55.4 kHz d)
[    48.085] (II) modeset(0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    48.085] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    48.085] (II) modeset(0): Modeline "720x405"x59.5   22.50  720 744 808 896  405 408 413 422 -hsync +vsync (25.1 kHz d)
[    48.085] (II) modeset(0): Modeline "720x405"x59.0   21.75  720 768 800 880  405 408 413 419 +hsync -vsync (24.7 kHz d)
[    48.085] (II) modeset(0): Modeline "684x384"x119.8   42.62  684 720 788 892  384 385 390 399 doublescan -hsync +vsync (47.8 kHz d)
[    48.085] (II) modeset(0): Modeline "684x384"x119.7   36.12  684 708 724 764  384 385 390 395 doublescan +hsync -vsync (47.3 kHz d)
[    48.085] (II) modeset(0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    48.085] (II) modeset(0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    48.085] (II) modeset(0): Modeline "640x400"x119.8   41.75  640 676 740 840  400 401 404 415 doublescan -hsync +vsync (49.7 kHz d)
[    48.085] (II) modeset(0): Modeline "640x400"x120.0   35.50  640 664 680 720  400 401 404 411 doublescan +hsync -vsync (49.3 kHz d)
[    48.085] (II) modeset(0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    48.085] (II) modeset(0): Modeline "640x360"x119.7   37.25  640 672 736 832  360 361 364 374 doublescan -hsync +vsync (44.8 kHz d)
[    48.085] (II) modeset(0): Modeline "640x360"x119.7   31.88  640 664 680 720  360 361 364 370 doublescan +hsync -vsync (44.3 kHz d)
[    48.085] (II) modeset(0): Modeline "640x360"x59.8   18.00  640 664 720 800  360 363 368 376 -hsync +vsync (22.5 kHz d)
[    48.085] (II) modeset(0): Modeline "640x360"x59.3   17.75  640 688 720 800  360 363 368 374 +hsync -vsync (22.2 kHz d)
[    48.085] (II) modeset(0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    48.085] (II) modeset(0): Modeline "512x288"x120.0   23.25  512 532 580 648  288 289 292 299 doublescan -hsync +vsync (35.9 kHz d)
[    48.085] (II) modeset(0): Modeline "512x288"x119.8   21.00  512 536 552 592  288 289 292 296 doublescan +hsync -vsync (35.5 kHz d)
[    48.085] (II) modeset(0): Modeline "480x270"x119.3   20.38  480 496 544 608  270 271 274 281 doublescan -hsync +vsync (33.5 kHz d)
[    48.085] (II) modeset(0): Modeline "480x270"x119.6   18.62  480 504 520 560  270 271 274 278 doublescan +hsync -vsync (33.3 kHz d)
[    48.085] (II) modeset(0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    48.085] (II) modeset(0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    48.085] (II) modeset(0): Modeline "432x243"x119.8   16.25  432 444 484 536  243 244 247 253 doublescan -hsync +vsync (30.3 kHz d)
[    48.085] (II) modeset(0): Modeline "432x243"x119.1   15.25  432 456 472 512  243 244 247 250 doublescan +hsync -vsync (29.8 kHz d)
[    48.086] (II) modeset(0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    48.086] (II) modeset(0): Modeline "360x202"x119.0   11.25  360 372 404 448  202 204 206 211 doublescan -hsync +vsync (25.1 kHz d)
[    48.086] (II) modeset(0): Modeline "360x202"x118.3   10.88  360 384 400 440  202 204 206 209 doublescan +hsync -vsync (24.7 kHz d)
[    48.086] (II) modeset(0): Modeline "320x180"x119.7    9.00  320 332 360 400  180 181 184 188 doublescan -hsync +vsync (22.5 kHz d)
[    48.086] (II) modeset(0): Modeline "320x180"x118.6    8.88  320 344 360 400  180 181 184 187 doublescan +hsync -vsync (22.2 kHz d)
[    48.172] (II) modeset(0): EDID for output DP-1
[    48.388] (II) modeset(0): EDID for output HDMI-1
[    48.395] (II) modeset(0): EDID for output DP-2
[    48.405] (II) modeset(0): EDID for output HDMI-2
[    48.405] (II) modeset(0): Output eDP-1 connected
[    48.405] (II) modeset(0): Output DP-1 disconnected
[    48.405] (II) modeset(0): Output HDMI-1 disconnected
[    48.405] (II) modeset(0): Output DP-2 disconnected
[    48.405] (II) modeset(0): Output HDMI-2 disconnected
[    48.405] (II) modeset(0): Using exact sizes for initial modes
[    48.405] (II) modeset(0): Output eDP-1 using initial mode 1366x768 +0+0
[    48.405] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[    48.405] (==) modeset(0): DPI set to (96, 96)
[    48.405] (II) Loading sub module "fb"
[    48.405] (II) LoadModule: "fb"
[    48.406] (II) Loading /usr/lib/xorg/modules/libfb.so
[    48.425] (II) Module fb: vendor="X.Org Foundation"
[    48.425]     compiled for 1.19.6, module version = 1.0.0
[    48.425]     ABI class: X.Org ANSI C Emulation, version 0.4
[    48.425] (II) UnloadModule: "fbdev"
[    48.425] (II) Unloading fbdev
[    48.425] (II) UnloadSubModule: "fbdevhw"
[    48.425] (II) Unloading fbdevhw
[    48.426] (II) UnloadModule: "vesa"
[    48.426] (II) Unloading vesa
[    48.426] (==) Depth 24 pixmap format is 32 bpp
[    48.625] (==) modeset(0): Backing store enabled
[    48.625] (==) modeset(0): Silken mouse enabled
[    48.646] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    48.729] (==) modeset(0): DPMS enabled
[    48.729] (II) modeset(0): [DRI2] Setup complete
[    48.729] (II) modeset(0): [DRI2]   DRI driver: i965
[    48.729] (II) modeset(0): [DRI2]   VDPAU driver: i965
[    48.729] (--) RandR disabled
[    48.738] (II) SELinux: Disabled on system
[    48.749] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    48.749] (II) AIGLX: enabled GLX_ARB_create_context
[    48.749] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    48.749] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    48.749] (II) AIGLX: enabled GLX_INTEL_swap_event
[    48.749] (II) AIGLX: enabled GLX_SGI_swap_control
[    48.749] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    48.749] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    48.749] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    48.749] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    48.749] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    48.749] (II) AIGLX: Loaded and initialized i965
[    48.749] (II) GLX: Initialized DRI2 GL provider for screen 0
[    48.758] (II) modeset(0): Damage tracking initialized
[    48.758] (II) modeset(0): Setting screen physical size to 361 x 203
[    48.865] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    48.865] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    48.865] (II) LoadModule: "evdev"
[    48.865] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.870] (II) Module evdev: vendor="X.Org Foundation"
[    48.870]     compiled for 1.19.3, module version = 2.10.5
[    48.870]     Module class: X.Org XInput Driver
[    48.870]     ABI class: X.Org XInput driver, version 24.1
[    48.870] (II) Using input driver 'evdev' for 'Power Button'
[    48.870] (**) Power Button: always reports core events
[    48.870] (**) evdev: Power Button: Device: "/dev/input/event2"
[    48.870] (--) evdev: Power Button: Vendor 0 Product 0x1
[    48.870] (--) evdev: Power Button: Found keys
[    48.870] (II) evdev: Power Button: Configuring as keyboard
[    48.870] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    48.870] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    48.870] (**) Option "xkb_rules" "evdev"
[    48.870] (**) Option "xkb_model" "pc105"
[    48.870] (**) Option "xkb_layout" "us"
[    48.872] (II) config/udev: Adding input device Asus Wireless Radio Control (/dev/input/event5)
[    48.872] (**) Asus Wireless Radio Control: Applying InputClass "evdev keyboard catchall"
[    48.872] (II) Using input driver 'evdev' for 'Asus Wireless Radio Control'
[    48.872] (**) Asus Wireless Radio Control: always reports core events
[    48.872] (**) evdev: Asus Wireless Radio Control: Device: "/dev/input/event5"
[    48.872] (--) evdev: Asus Wireless Radio Control: Vendor 0x1043 Product 0
[    48.872] (--) evdev: Asus Wireless Radio Control: Found keys
[    48.872] (II) evdev: Asus Wireless Radio Control: Configuring as keyboard
[    48.872] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/ATK4002:00/input/input5/event5"
[    48.872] (II) XINPUT: Adding extended input device "Asus Wireless Radio Control" (type: KEYBOARD, id 7)
[    48.872] (**) Option "xkb_rules" "evdev"
[    48.872] (**) Option "xkb_model" "pc105"
[    48.872] (**) Option "xkb_layout" "us"
[    48.874] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    48.874] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    48.874] (II) Using input driver 'evdev' for 'Video Bus'
[    48.874] (**) Video Bus: always reports core events
[    48.874] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    48.874] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    48.874] (--) evdev: Video Bus: Found keys
[    48.874] (II) evdev: Video Bus: Configuring as keyboard
[    48.874] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    48.874] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    48.874] (**) Option "xkb_rules" "evdev"
[    48.874] (**) Option "xkb_model" "pc105"
[    48.874] (**) Option "xkb_layout" "us"
[    48.875] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    48.875] (II) No input driver specified, ignoring this device.
[    48.875] (II) This device may have been added with another device file.
[    48.876] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    48.876] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    48.876] (II) Using input driver 'evdev' for 'Sleep Button'
[    48.876] (**) Sleep Button: always reports core events
[    48.876] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    48.877] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    48.877] (--) evdev: Sleep Button: Found keys
[    48.877] (II) evdev: Sleep Button: Configuring as keyboard
[    48.877] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    48.877] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    48.877] (**) Option "xkb_rules" "evdev"
[    48.877] (**) Option "xkb_model" "pc105"
[    48.877] (**) Option "xkb_layout" "us"
[    48.879] (II) config/udev: Adding input device USB2.0 VGA UVC WebCam: USB2.0 V (/dev/input/event8)
[    48.879] (**) USB2.0 VGA UVC WebCam: USB2.0 V: Applying InputClass "evdev keyboard catchall"
[    48.879] (II) Using input driver 'evdev' for 'USB2.0 VGA UVC WebCam: USB2.0 V'
[    48.879] (**) USB2.0 VGA UVC WebCam: USB2.0 V: always reports core events
[    48.879] (**) evdev: USB2.0 VGA UVC WebCam: USB2.0 V: Device: "/dev/input/event8"
[    48.879] (--) evdev: USB2.0 VGA UVC WebCam: USB2.0 V: Vendor 0xbda Product 0x57e6
[    48.879] (--) evdev: USB2.0 VGA UVC WebCam: USB2.0 V: Found keys
[    48.879] (II) evdev: USB2.0 VGA UVC WebCam: USB2.0 V: Configuring as keyboard
[    48.879] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input10/event8"
[    48.879] (II) XINPUT: Adding extended input device "USB2.0 VGA UVC WebCam: USB2.0 V" (type: KEYBOARD, id 10)
[    48.879] (**) Option "xkb_rules" "evdev"
[    48.879] (**) Option "xkb_model" "pc105"
[    48.879] (**) Option "xkb_layout" "us"
[    48.881] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    48.881] (II) No input driver specified, ignoring this device.
[    48.881] (II) This device may have been added with another device file.
[    48.881] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[    48.881] (II) No input driver specified, ignoring this device.
[    48.881] (II) This device may have been added with another device file.
[    48.882] (II) config/udev: Adding input device Elan Touchpad (/dev/input/event6)
[    48.882] (**) Elan Touchpad: Applying InputClass "evdev touchpad catchall"
[    48.882] (**) Elan Touchpad: Applying InputClass "evdev touchscreen catchall"
[    48.882] (**) Elan Touchpad: Applying InputClass "touchpad catchall"
[    48.882] (**) Elan Touchpad: Applying InputClass "Default clickpad buttons"
[    48.882] (II) LoadModule: "synaptics"
[    48.883] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    48.884] (II) Module synaptics: vendor="X.Org Foundation"
[    48.884]     compiled for 1.19.3, module version = 1.9.0
[    48.884]     Module class: X.Org XInput Driver
[    48.885]     ABI class: X.Org XInput driver, version 24.1
[    48.885] (II) Using input driver 'synaptics' for 'Elan Touchpad'
[    48.885] (**) Elan Touchpad: always reports core events
[    48.885] (**) Option "Device" "/dev/input/event6"
[    48.912] (II) synaptics: Elan Touchpad: found clickpad property
[    48.912] (--) synaptics: Elan Touchpad: x-axis range 0 - 3120 (res 32)
[    48.912] (--) synaptics: Elan Touchpad: y-axis range 0 - 1716 (res 32)
[    48.912] (--) synaptics: Elan Touchpad: pressure range 0 - 255
[    48.912] (--) synaptics: Elan Touchpad: finger width range 0 - 15
[    48.912] (--) synaptics: Elan Touchpad: buttons: left double triple
[    48.912] (--) synaptics: Elan Touchpad: Vendor 0x4f3 Product 0x9
[    48.913] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    48.913] (--) synaptics: Elan Touchpad: touchpad found
[    48.913] (**) Elan Touchpad: always reports core events
[    48.936] (**) Option "config_info" "udev:/sys/devices/pci0000:00/808622C1:03/i2c-3/i2c-ELAN1000:00/input/input6/event6"
[    48.936] (II) XINPUT: Adding extended input device "Elan Touchpad" (type: TOUCHPAD, id 11)
[    48.936] (**) synaptics: Elan Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    48.936] (**) synaptics: Elan Touchpad: (accel) MaxSpeed is now 1.75
[    48.936] (**) synaptics: Elan Touchpad: (accel) AccelFactor is now 0.056
[    48.937] (**) Elan Touchpad: (accel) keeping acceleration scheme 1
[    48.937] (**) Elan Touchpad: (accel) acceleration profile 1
[    48.937] (**) Elan Touchpad: (accel) acceleration factor: 2.000
[    48.937] (**) Elan Touchpad: (accel) acceleration threshold: 4
[    48.937] (--) synaptics: Elan Touchpad: touchpad found
[    48.938] (II) config/udev: Adding input device Elan Touchpad (/dev/input/mouse0)
[    48.938] (**) Elan Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    48.939] (II) config/udev: Adding input device SIS0457:00 0457:1136 (/dev/input/event7)
[    48.939] (**) SIS0457:00 0457:1136: Applying InputClass "evdev touchscreen catchall"
[    48.939] (II) Using input driver 'evdev' for 'SIS0457:00 0457:1136'
[    48.939] (**) SIS0457:00 0457:1136: always reports core events
[    48.939] (**) evdev: SIS0457:00 0457:1136: Device: "/dev/input/event7"
[    48.945] (--) evdev: SIS0457:00 0457:1136: Vendor 0x457 Product 0x1136
[    48.945] (--) evdev: SIS0457:00 0457:1136: Found absolute axes
[    48.945] (--) evdev: SIS0457:00 0457:1136: Found absolute multitouch axes
[    48.945] (II) evdev: SIS0457:00 0457:1136: No buttons found, faking one.
[    48.945] (--) evdev: SIS0457:00 0457:1136: Found x and y absolute axes
[    48.945] (--) evdev: SIS0457:00 0457:1136: Found absolute touchscreen
[    48.945] (II) evdev: SIS0457:00 0457:1136: Configuring as touchscreen
[    48.945] (**) evdev: SIS0457:00 0457:1136: YAxisMapping: buttons 4 and 5
[    48.945] (**) evdev: SIS0457:00 0457:1136: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.945] (**) Option "config_info" "udev:/sys/devices/pci0000:00/808622C1:05/i2c-4/i2c-SIS0457:00/0018:0457:1136.0001/input/input7/event7"
[    48.945] (II) XINPUT: Adding extended input device "SIS0457:00 0457:1136" (type: TOUCHSCREEN, id 12)
[    48.945] (II) evdev: SIS0457:00 0457:1136: initialized for absolute axes.
[    48.946] (**) SIS0457:00 0457:1136: (accel) keeping acceleration scheme 1
[    48.946] (**) SIS0457:00 0457:1136: (accel) acceleration profile 0
[    48.946] (**) SIS0457:00 0457:1136: (accel) acceleration factor: 2.000
[    48.946] (**) SIS0457:00 0457:1136: (accel) acceleration threshold: 4
[    48.947] (II) config/udev: Adding input device SIS0457:00 0457:1136 (/dev/input/mouse1)
[    48.947] (II) No input driver specified, ignoring this device.
[    48.947] (II) This device may have been added with another device file.
[    48.948] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event9)
[    48.948] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    48.948] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    48.948] (**) Asus WMI hotkeys: always reports core events
[    48.948] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event9"
[    48.948] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    48.948] (--) evdev: Asus WMI hotkeys: Found keys
[    48.948] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    48.948] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input11/event9"
[    48.948] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 13)
[    48.948] (**) Option "xkb_rules" "evdev"
[    48.948] (**) Option "xkb_model" "pc105"
[    48.948] (**) Option "xkb_layout" "us"
[    48.949] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    48.950] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    48.950] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    48.950] (**) AT Translated Set 2 keyboard: always reports core events
[    48.950] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    48.950] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    48.950] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    48.950] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    48.950] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    48.950] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[    48.950] (**) Option "xkb_rules" "evdev"
[    48.950] (**) Option "xkb_model" "pc105"
[    48.950] (**) Option "xkb_layout" "us"
[    52.078] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    52.078] (II) modeset(0): Printing DDC gathered Modelines:
[    52.078] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    53.102] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    53.102] (II) modeset(0): Printing DDC gathered Modelines:
[    53.102] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    53.503] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    53.503] (II) modeset(0): Printing DDC gathered Modelines:
[    53.503] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    53.854] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    53.854] (II) modeset(0): Printing DDC gathered Modelines:
[    53.854] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    55.051] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    55.051] (II) modeset(0): Printing DDC gathered Modelines:
[    55.051] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    70.143] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    70.143] (II) modeset(0): Printing DDC gathered Modelines:
[    70.143] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    70.851] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    70.851] (II) modeset(0): Printing DDC gathered Modelines:
[    70.851] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    71.360] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    71.360] (II) modeset(0): Printing DDC gathered Modelines:
[    71.360] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    71.713] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    71.713] (II) modeset(0): Printing DDC gathered Modelines:
[    71.713] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    72.894] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    72.894] (II) modeset(0): Printing DDC gathered Modelines:
[    72.894] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    73.376] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    73.376] (II) modeset(0): Printing DDC gathered Modelines:
[    73.376] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[    73.856] (II) modeset(0): EDID vendor "IVO", prod id 1164
[    73.856] (II) modeset(0): Printing DDC gathered Modelines:
[    73.856] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[ 18123.849] (II) modeset(0): EDID vendor "IVO", prod id 1164
[ 18123.852] (II) modeset(0): Printing DDC gathered Modelines:
[ 18123.853] (II) modeset(0): Modeline "1366x768"x0.0   70.47  1366 1406 1438 1502  768 773 778 782 -hsync -vsync (46.9 kHz eP)
[ 18272.968] (II) evdev: AT Translated Set 2 keyboard: Close
[ 18272.969] (II) UnloadModule: "evdev"
[ 18272.969] (II) evdev: Asus WMI hotkeys: Close
[ 18272.969] (II) UnloadModule: "evdev"
[ 18272.969] (II) evdev: SIS0457:00 0457:1136: Close
[ 18272.972] (II) UnloadModule: "evdev"
[ 18272.972] (II) UnloadModule: "synaptics"
[ 18272.972] (II) evdev: USB2.0 VGA UVC WebCam: USB2.0 V: Close
[ 18272.999] (II) UnloadModule: "evdev"
[ 18272.999] (II) evdev: Sleep Button: Close
[ 18272.999] (II) UnloadModule: "evdev"
[ 18272.999] (II) evdev: Video Bus: Close
[ 18272.999] (II) UnloadModule: "evdev"
[ 18272.999] (II) evdev: Asus Wireless Radio Control: Close
[ 18272.999] (II) UnloadModule: "evdev"
[ 18272.999] (II) evdev: Power Button: Close
[ 18272.999] (II) UnloadModule: "evdev"
[ 18274.617] (II) Server terminated successfully (0). Closing log file

```

---

### Post by PRafael on 2018-11-06
Hi. I had the same problem after upgrading to kernel [LEFT][COLOR=#000000][FONT="Ubuntu Mono"]4.15.0-38-generic so I went back to the previous kernel and all Works.

Greetings

Paulo
[/FONT][/COLOR][/LEFT]

---

### Post by Autodave on 2018-11-06
Hopefully someone will be able to get your PC working correctly.

My 2 cents: I have very rarely had any luck upgrading one release to another.  My best advice for the future is to backup everything and do a clean install.

---

### Post by QIII on 2018-11-06
+1 to clean install.

But let's see if we can sort you out from here.

The hardware specs of your machine would be helpful.  Did you have a proprietary graphics driver installed?

---

### Post by pschwa363 on 2018-11-07
i'm not sure what drivers were previously installed. not really sure how to find that information. what hardware info do you need?

also, if it would be much easier to wipe and clean install, that's a possibility. i only have a few files on here that i would need to back up in order to be good there

---

