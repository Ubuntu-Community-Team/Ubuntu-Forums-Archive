---
title: "via openchrome driver: monitor + tv out.... help please"
date: 2009-01-21
forum: General Help
---

### Post by sloggerkhan on 2009-01-21
So I have a computer with via integrated graphics. Works fine with openchrome driver. Boot to command line and TV and LCD are active, both showing the console. Start X and suddenly only the LCD is active. xrandr shows only 1 display. 

How do I get both screens active? xrandr doesn't work (doesn't see TV output for some reason.). Xinerama doesn't seem to work either. Is there some stupid trick to this I'm missing? I need TV out with an actual xserver.

xorg.cong:
```

Section "ServerLayout"
        Identifier     "Xorg Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Keyboard0" "CoreKeyboard"
# PS/2 Mouse not detected
# Serial Mouse not detected
        InputDevice    "USB Mouse" "CorePointer"
        Option "Xinerama" "true"
EndSection

Section "ServerFlags"
        Option "AllowMouseOpenFail"  "true"
        Option "AutoAddDevices" "False"

EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/misc:unscaled"
        FontPath     "/usr/share/fonts/misc"
        FontPath     "/usr/share/fonts/75dpi:unscaled"
        FontPath     "/usr/share/fonts/75dpi"
        FontPath     "/usr/share/fonts/100dpi:unscaled"
        FontPath     "/usr/share/fonts/100dpi"
        FontPath     "/usr/share/fonts/PEX"
# Additional fonts: Locale, Gimp, TTF...
        FontPath     "/usr/share/fonts/cyrillic"
#        FontPath     "/usr/share/lib/X11/fonts/latin2/75dpi"
#        FontPath     "/usr/share/lib/X11/fonts/latin2/100dpi"
# True type and type1 fonts are also handled via xftlib, see /etc/X11/XftConfig!
#        FontPath     "/usr/share/fonts/Type1"
        FontPath     "/usr/share/fonts/ttf/western"
        FontPath     "/usr/share/fonts/ttf/decoratives"
        FontPath     "/usr/share/fonts/truetype"
        FontPath     "/usr/share/fonts/truetype/openoffice"
        FontPath     "/usr/share/fonts/truetype/ttf-bitstream-vera"
        FontPath     "/usr/share/fonts/latex-ttf-fonts"
        FontPath     "/usr/share/fonts/defoma/CID"
        FontPath     "/usr/share/fonts/defoma/TrueType"
EndSection

Section "Module"
        Load  "ddc"  # ddc probing of monitor
        Load  "dbe"
        Load  "dri"
        Load  "extmod"
        Load  "glx"
        Load  "bitmap" # bitmap-fonts
# Load  "type1"
        Load  "freetype"
# Load  "record"
        #   Load  "synaptics"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "keyboard"
        Option      "CoreKeyboard"
        Option "XkbRules" "xorg"
        Option "XkbModel" "pc105"
        Option "XkbLayout" "us"
        Option "XkbVariant" ""
EndSection

Section "InputDevice"
        Identifier  "Serial Mouse"
        Driver      "mouse"
        Option      "Protocol" "Microsoft"
        Option      "Device" "/dev/ttyS0"
        Option      "Emulate3Buttons" "true"
        Option      "Emulate3Timeout" "70"
        Option            "SendCoreEvents"  "true"
EndSection

Section "InputDevice"
        Identifier  "PS/2 Mouse"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option          "ZAxisMapping"          "4 5"
        Option      "Device" "/dev/psaux"
        Option      "Emulate3Buttons" "true"
        Option      "Emulate3Timeout" "70"
        Option            "SendCoreEvents"  "true"
EndSection

Section "InputDevice"
        Identifier      "USB Mouse"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mice"
        Option                "SendCoreEvents"        "true"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "5"
EndSection

Section "Monitor"
        Identifier "Monitor0"
                Option "DPMS" "true"
#        HorizSync    28.0 - 78.0 # Warning: This may fry very old Monitors
        HorizSync    28.0 - 96.0 # Warning: This may fry old Monitors
        VertRefresh  50.0 - 75.0 # Very conservative. May flicker.
#        VertRefresh  50.0 - 62.0 # Extreme conservative. Will flicker. TFT default.
        #  Default modes distilled from
        #      "VESA and Industry Standards and Guide for Computer Display Monitor
        #       Timing", version 1.0, revision 0.8, adopted September 17, 1998.
        #  $XFree86: xc/programs/Xserver/hw/xfree86/etc/vesamodes,v 1.4 1999/11/18 16:52:17 tsi
Exp $
        # 640x350 @ 85Hz (VESA) hsync: 37.9kHz
        ModeLine "640x350"    31.5  640  672  736  832    350  382  385  445 +hsync -vsync
        # 640x400 @ 85Hz (VESA) hsync: 37.9kHz
        ModeLine "640x400"    31.5  640  672  736  832    400  401  404  445 -hsync +vsync
        # 720x400 @ 85Hz (VESA) hsync: 37.9kHz
        ModeLine "720x400"    35.5  720  756  828  936    400  401  404  446 -hsync +vsync
        # 640x480 @ 60Hz (Industry standard) hsync: 31.5kHz
        ModeLine "640x480"    25.2  640  656  752  800    480  490  492  525 -hsync -vsync
        # 640x480 @ 72Hz (VESA) hsync: 37.9kHz
        ModeLine "640x480"    31.5  640  664  704  832    480  489  491  520 -hsync -vsync
        # 640x480 @ 75Hz (VESA) hsync: 37.5kHz
        ModeLine "640x480"    31.5  640  656  720  840    480  481  484  500 -hsync -vsync
        # 640x480 @ 85Hz (VESA) hsync: 43.3kHz
        ModeLine "640x480"    36.0  640  696  752  832    480  481  484  509 -hsync -vsync
        # 800x600 @ 56Hz (VESA) hsync: 35.2kHz
        ModeLine "800x600"    36.0  800  824  896 1024    600  601  603  625 +hsync +vsync
        # 800x600 @ 60Hz (VESA) hsync: 37.9kHz
        ModeLine "800x600"    40.0  800  840  968 1056    600  601  605  628 +hsync +vsync
        # 800x600 @ 72Hz (VESA) hsync: 48.1kHz
        ModeLine "800x600"    50.0  800  856  976 1040    600  637  643  666 +hsync +vsync
        # 800x600 @ 75Hz (VESA) hsync: 46.9kHz
        ModeLine "800x600"    49.5  800  816  896 1056    600  601  604  625 +hsync +vsync
        # 800x600 @ 85Hz (VESA) hsync: 53.7kHz
        ModeLine "800x600"    56.3  800  832  896 1048    600  601  604  631 +hsync +vsync
        # 1024x768i @ 43Hz (industry standard) hsync: 35.5kHz
        ModeLine "1024x768"   44.9 1024 1032 1208 1264    768  768  776  817 +hsync +vsync
Interlace
        # 1024x768 @ 60Hz (VESA) hsync: 48.4kHz
        ModeLine "1024x768"   65.0 1024 1048 1184 1344    768  771  777  806 -hsync -vsync
        # 1024x768 @ 70Hz (VESA) hsync: 56.5kHz
        ModeLine "1024x768"   75.0 1024 1048 1184 1328    768  771  777  806 -hsync -vsync
        # 1024x768 @ 75Hz (VESA) hsync: 60.0kHz
        ModeLine "1024x768"   78.8 1024 1040 1136 1312    768  769  772  800 +hsync +vsync
        # 1024x768 @ 85Hz (VESA) hsync: 68.7kHz
        ModeLine "1024x768"   94.5 1024 1072 1168 1376    768  769  772  808 +hsync +vsync
        # 1152x864 @ 75Hz (VESA) hsync: 67.5kHz
        ModeLine "1152x864"  108.0 1152 1216 1344 1600    864  865  868  900 +hsync +vsync
        # 1280x960 @ 60Hz (VESA) hsync: 60.0kHz
        ModeLine "1280x960"  108.0 1280 1376 1488 1800    960  961  964 1000 +hsync +vsync
        # 1280x960 @ 85Hz (VESA) hsync: 85.9kHz
        ModeLine "1280x960"  148.5 1280 1344 1504 1728    960  961  964 1011 +hsync +vsync
        # 1280x1024 @ 60Hz (VESA) hsync: 64.0kHz
        ModeLine "1280x1024" 108.0 1280 1328 1440 1688   1024 1025 1028 1066 +hsync +vsync
        # 1280x1024 @ 75Hz (VESA) hsync: 80.0kHz
        ModeLine "1280x1024" 135.0 1280 1296 1440 1688   1024 1025 1028 1066 +hsync +vsync
        # 1280x1024 @ 85Hz (VESA) hsync: 91.1kHz
        ModeLine "1280x1024" 157.5 1280 1344 1504 1728   1024 1025 1028 1072 +hsync +vsync
        # 1600x1200 @ 60Hz (VESA) hsync: 75.0kHz
        ModeLine "1600x1200" 162.0 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
        # 1600x1200 @ 65Hz (VESA) hsync: 81.3kHz
        ModeLine "1600x1200" 175.5 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
        # 1600x1200 @ 70Hz (VESA) hsync: 87.5kHz
        ModeLine "1600x1200" 189.0 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
        # 1600x1200 @ 75Hz (VESA) hsync: 93.8kHz
        ModeLine "1600x1200" 202.5 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
        # 1600x1200 @ 85Hz (VESA) hsync: 106.3kHz
        ModeLine "1600x1200" 229.5 1600 1664 1856 2160   1200 1201 1204 1250 +hsync +vsync
        # 1792x1344 @ 60Hz (VESA) hsync: 83.6kHz
        ModeLine "1792x1344" 204.8 1792 1920 2120 2448   1344 1345 1348 1394 -hsync +vsync
        # 1792x1344 @ 75Hz (VESA) hsync: 106.3kHz
        ModeLine "1792x1344" 261.0 1792 1888 2104 2456   1344 1345 1348 1417 -hsync +vsync
        # 1856x1392 @ 60Hz (VESA) hsync: 86.3kHz
        ModeLine "1856x1392" 218.3 1856 1952 2176 2528   1392 1393 1396 1439 -hsync +vsync
        # 1856x1392 @ 75Hz (VESA) hsync: 112.5kHz
        ModeLine "1856x1392" 288.0 1856 1984 2208 2560   1392 1393 1396 1500 -hsync +vsync
        # 1920x1440 @ 60Hz (VESA) hsync: 90.0kHz
        ModeLine "1920x1440" 234.0 1920 2048 2256 2600   1440 1441 1444 1500 -hsync +vsync
        # 1920x1440 @ 75Hz (VESA) hsync: 112.5kHz
        ModeLine "1920x1440" 297.0 1920 2064 2288 2640   1440 1441 1444 1500 -hsync +vsync
        # Additional modelines
        ModeLine "1800x1440"  230    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
        ModeLine "1800x1440"  250    1800 1896 2088 2392  1440 1441 1444 1490 +HSync +VSync
        # Extended modelines with GTF timings
        # 640x480 @ 100.00 Hz (GTF) hsync: 50.90 kHz; pclk: 43.16 MHz
        ModeLine "640x480"  43.16  640 680 744 848  480 481 484 509  -HSync +Vsync
        # 768x576 @ 60.00 Hz (GTF) hsync: 35.82 kHz; pclk: 34.96 MHz
        ModeLine "768x576"  34.96  768 792 872 976  576 577 580 597  -HSync +Vsync
        # 768x576 @ 72.00 Hz (GTF) hsync: 43.27 kHz; pclk: 42.93 MHz
        ModeLine "768x576"  42.93  768 800 880 992  576 577 580 601  -HSync +Vsync
        # 768x576 @ 75.00 Hz (GTF) hsync: 45.15 kHz; pclk: 45.51 MHz
        ModeLine "768x576"  45.51  768 808 888 1008  576 577 580 602  -HSync +Vsync
        # 768x576 @ 85.00 Hz (GTF) hsync: 51.42 kHz; pclk: 51.84 MHz
        ModeLine "768x576"  51.84  768 808 888 1008  576 577 580 605  -HSync +Vsync
        # 768x576 @ 100.00 Hz (GTF) hsync: 61.10 kHz; pclk: 62.57 MHz
        ModeLine "768x576"  62.57  768 816 896 1024  576 577 580 611  -HSync +Vsync
        # 800x600 @ 100.00 Hz (GTF) hsync: 63.60 kHz; pclk: 68.18 MHz
        ModeLine "800x600"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync
        # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
        ModeLine "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
        # 1152x864 @ 60.00 Hz (GTF) hsync: 53.70 kHz; pclk: 81.62 MHz
        ModeLine "1152x864"  81.62  1152 1216 1336 1520  864 865 868 895  -HSync +Vsync
        # 1152x864 @ 85.00 Hz (GTF) hsync: 77.10 kHz; pclk: 119.65 MHz
        ModeLine "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907  -HSync +Vsync
        # 1152x864 @ 100.00 Hz (GTF) hsync: 91.50 kHz; pclk: 143.47 MHz
        ModeLine "1152x864"  143.47  1152 1232 1360 1568  864 865 868 915  -HSync +Vsync
        # 1280x960 @ 72.00 Hz (GTF) hsync: 72.07 kHz; pclk: 124.54 MHz
        ModeLine "1280x960"  124.54  1280 1368 1504 1728  960 961 964 1001  -HSync +Vsync
        # 1280x960 @ 75.00 Hz (GTF) hsync: 75.15 kHz; pclk: 129.86 MHz
        ModeLine "1280x960"  129.86  1280 1368 1504 1728  960 961 964 1002  -HSync +Vsync
        # 1280x960 @ 100.00 Hz (GTF) hsync: 101.70 kHz; pclk: 178.99 MHz
        ModeLine "1280x960"  178.99  1280 1376 1520 1760  960 961 964 1017  -HSync +Vsync
        # 1280x1024 @ 100.00 Hz (GTF) hsync: 108.50 kHz; pclk: 190.96 MHz
        ModeLine "1280x1024"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync
        # 1400x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 122.61 MHz
        ModeLine "1400x1050"  122.61  1400 1488 1640 1880  1050 1051 1054 1087  -HSync +Vsync
        # 1400x1050 @ 72.00 Hz (GTF) hsync: 78.77 kHz; pclk: 149.34 MHz
        ModeLine "1400x1050"  149.34  1400 1496 1648 1896  1050 1051 1054 1094  -HSync +Vsync
        # 1400x1050 @ 75.00 Hz (GTF) hsync: 82.20 kHz; pclk: 155.85 MHz
        ModeLine "1400x1050"  155.85  1400 1496 1648 1896  1050 1051 1054 1096  -HSync +Vsync
        # 1400x1050 @ 85.00 Hz (GTF) hsync: 93.76 kHz; pclk: 179.26 MHz
        ModeLine "1400x1050"  179.26  1400 1504 1656 1912  1050 1051 1054 1103  -HSync +Vsync
        # 1400x1050 @ 100.00 Hz (GTF) hsync: 111.20 kHz; pclk: 214.39 MHz
        ModeLine "1400x1050"  214.39  1400 1512 1664 1928  1050 1051 1054 1112  -HSync +Vsync
        # 1600x1200 @ 100.00 Hz (GTF) hsync: 127.10 kHz; pclk: 280.64 MHz
        ModeLine "1600x1200"  280.64  1600 1728 1904 2208  1200 1201 1204 1271  -HSync +Vsync
EndSection

# Auto-generated by Archie mkxcfg


Section "Device"
        Identifier  "Card0"
        Driver      "openchrome"
        Option      "EnableAGPDMA" "false"
        Option      "DDCMode" "true"
        Option "MonitorLayout" "TMDS, TV"
        Screen 0
        VendorName  "All"
        BoardName   "All"
EndSection

Section "Device"
        Identifier  "Card1"
        Driver      "openchrome"
        Option      "ActiveDevice" "TV"
        Option            "TVType" "NTSC"
        Option             "TVOutput" "SC"
        Option "MonitorLayout" "TMDS, TV"
        Screen 1
        VendorName  "All"
        BoardName   "All"
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        DefaultColorDepth 24
        SubSection "Display"
                Modes "720x480" "640x480"
        EndSubSection
EndSection

Section "Monitor"
        Identifier "Monitor1"
        HorizSync 30 - 50
        VertRefresh 50.0 - 50.0
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultColorDepth 16
        SubSection "Display"
                Depth     1

                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4

                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8

                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15

                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16

                Modes "1024x768" "800x600" "720x480" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24

                Modes "1024x768" "800x600" "720x480" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     32

                Modes "1024x768" "800x600" "720x480" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

```

log:
```



X.Org X Server 1.5.3
Release Date: 5 November 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.27-ARCH i686
Current Operating System: Linux embedV 2.6.27-ARCH #1 SMP PREEMPT Sun Dec 21 09:31:10 UTC
2008 i686
Build Date: 17 December 2008  08:20:05PM

        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 21 07:09:54 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Xorg Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "USB Mouse"
(**) Option "AllowMouseOpenFail" "true"
(**) Option "Xinerama" "true"
(**) Option "AutoAddDevices" "False"
(**) Not automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/fonts/PEX" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/cyrillic".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/usr/share/fonts/cyrillic").
(WW) The directory "/usr/share/fonts/ttf/western" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/ttf/decoratives" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype/openoffice" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/truetype/ttf-bitstream-vera" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/latex-ttf-fonts" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/defoma/CID" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/defoma/TrueType" does not exist.
        Entry deleted from font path.
(==) Including the default font path
/usr/share/fonts/misc,/usr/share/fonts/100dpi:unscaled,/usr/share/fonts/75dpi:unscaled,/usr/share/fonts/TTF,/usr/share/fonts/Type1.
(**) FontPath set to:
        /usr/share/fonts/misc:unscaled,
        /usr/share/fonts/misc,
        /usr/share/fonts/75dpi:unscaled,
        /usr/share/fonts/75dpi,
        /usr/share/fonts/100dpi:unscaled,
        /usr/share/fonts/100dpi,
        /usr/share/fonts/misc,
        /usr/share/fonts/100dpi:unscaled,
        /usr/share/fonts/75dpi:unscaled,
        /usr/share/fonts/TTF,
        /usr/share/fonts/Type1
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81d5fe0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
        X.Org Server Extension : 1.1
        X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome
Pro] rev 1, Mem @ 0xf4000000/0, 0xfb000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
        [0] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [25] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [26] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [27] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [28] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [29] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [30] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [31] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [32] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [33] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [34] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [35] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the
config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config
file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config
file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the
config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config
file.
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.5.3, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.5.3, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.5.3, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.5.3, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.5.3, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "openchrome"

(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
        compiled for 1.4.99.906, module version = 0.2.903
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.4.2, module version = 1.3.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.4.2, module version = 1.3.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
        K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
        K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890
(II) Primary Device is: PCI 01@00:00:0
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to http://www.openchrome.org/.
(!!) (openchrome 0.2.903 release)
Requested Entity already in use!
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to http://www.openchrome.org/.
(!!) (openchrome 0.2.903 release)
(EE) Screen 1 deleted because of no matching config section.
(II) CHROME(1): VIAFreeScreen
(II) CHROME(1): VIAFreeRec
(II) UnloadModule: "openchrome"
(II) resource ranges after probing:
        [0] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [25] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [26] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [27] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [28] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [29] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [30] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [31] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [32] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [33] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [34] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [35] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.5.3, module version = 0.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) CHROME(0): VIAGetRec
(**) CHROME(0): Depth 16, (--) framebuffer bpp 16
(==) CHROME(0): RGB weight 565
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: P4M800Pro/VN800/CN700
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options.
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Reading config file...
(**) CHROME(0): Option "EnableAGPDMA" "false"
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): Shadow framebuffer is disabled.
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
(**) CHROME(0): AGP DMA will be disabled if DRI is enabled.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
        if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfb000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfb200000 with size 0x20000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(WW) CHROME(0): Manufacturer plainly copied main PCI IDs to subsystem/card IDs.
(--) CHROME(0): Detected VIA VT3344 (VM800) - EPIA EN.
(II) CHROME(0): Detected MemClk 7
(II) CHROME(0): ViaGetMemoryBandwidth
(II) CHROME(0): Detected TV standard: NTSC.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): Manufacturer: ACR  Model: 56ad  Serial#: 16843009
(II) CHROME(0): Year: 2006  Week: 20
(II) CHROME(0): EDID Version: 1.3
(II) CHROME(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) CHROME(0): Sync:  Separate
(II) CHROME(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) CHROME(0): Gamma: 2.20
(II) CHROME(0): DPMS capabilities: Off; RGB/Color Display
(II) CHROME(0): First detailed timing is preferred mode
(II) CHROME(0): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) CHROME(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) CHROME(0): Supported VESA Video Modes:
(II) CHROME(0): 720x400@70Hz
(II) CHROME(0): 640x480@60Hz
(II) CHROME(0): 640x480@67Hz
(II) CHROME(0): 640x480@72Hz
(II) CHROME(0): 640x480@75Hz
(II) CHROME(0): 800x600@56Hz
(II) CHROME(0): 800x600@60Hz
(II) CHROME(0): 800x600@72Hz
(II) CHROME(0): 800x600@75Hz
(II) CHROME(0): 832x624@75Hz
(II) CHROME(0): 1024x768@60Hz
(II) CHROME(0): 1024x768@70Hz
(II) CHROME(0): 1024x768@75Hz
(II) CHROME(0): 1280x1024@75Hz
(II) CHROME(0): Manufacturer's mask: 0
(II) CHROME(0): Supported Future Video Modes:
(II) CHROME(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) CHROME(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) CHROME(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) CHROME(0): Supported additional Video Mode:
(II) CHROME(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) CHROME(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) CHROME(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) CHROME(0): Serial No: 620004934300
(II) CHROME(0): Monitor name: AL1717
(II) CHROME(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140
MHz
(II) CHROME(0): EDID (in hex):
(II) CHROME(0):         00ffffffffffff000472ad5601010101
(II) CHROME(0):         1410010368221b782aaea5a6544c9926
(II) CHROME(0):         145054bfef0081808140714f01010101
(II) CHROME(0):         010101010101302a009851002a403070
(II) CHROME(0):         1300520e1100001e000000ff00363230
(II) CHROME(0):         3030343933343330300a000000fc0041
(II) CHROME(0):         4c313731370a202020202020000000fd
(II) CHROME(0):         00384c1e510e000a202020202020008e
(II) CHROME(0): EDID vendor "ACR", prod id 22189
(II) CHROME(0): Using hsync ranges from config file
(II) CHROME(0): Using vrefresh ranges from config file
(II) CHROME(0): Printing DDC gathered Modelines:
(II) CHROME(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028
1066 +hsync +vsync (64.0 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync
+vsync (37.9 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync
+vsync (35.2 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync
-vsync (37.5 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync
-vsync (37.9 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync
-vsync (35.0 kHz)
(II) CHROME(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync
-vsync (31.5 kHz)
(II) CHROME(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync
+vsync (31.5 kHz)
(II) CHROME(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028
1066 +hsync +vsync (80.0 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800
+hsync +vsync (60.1 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806
-hsync -vsync (56.5 kHz)
(II) CHROME(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806
-hsync -vsync (48.4 kHz)
(II) CHROME(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync
-vsync (49.7 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync
+vsync (46.9 kHz)
(II) CHROME(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync
+vsync (48.1 kHz)
(II) CHROME(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028
1060 -hsync +vsync (63.6 kHz)
(II) CHROME(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994
-hsync +vsync (59.6 kHz)
(II) CHROME(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902
-hsync +vsync (67.7 kHz)
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaVT162xDetect
(II) CHROME(0): I2C device "I2C bus 2:VT162x" registered at address 0x40.
(--) CHROME(0): Detected VIA Technologies VT1625 TV Encoder
(II) CHROME(0): ViaTVInit
(II) CHROME(0): ViaVT162xInit
(II) CHROME(0): VT162xSave
(II) CHROME(0): VT1625DACSense
(WW) CHROME(0): VT1625: Unknown cable combination: 0x030.
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x07
(II) CHROME(0): ViaOutputsSelect: CRT.
(II) CHROME(0): ViaModesAttach
(II) CHROME(0): Monitor0: Using hsync range of 28.00-96.00 kHz
(II) CHROME(0): Monitor0: Using vrefresh range of 50.00-75.00 Hz
(II) CHROME(0): Monitor0: Using maximum pixel clock of 140.00 MHz
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "640x350" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "640x400" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "720x400" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25200)

(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "640x480" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "800x600" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
(II) CHROME(0): Not using mode "1024x768" (interlace mode not supported)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1024x768" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x960 (148500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1280x960" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (157500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1280x1024" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (162000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1600x1200" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (175500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1600x1200" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (189000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1600x1200" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (202500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1600x1200" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (229500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1600x1200" (hsync out of range)
(II) CHROME(0): ViaValidMode: Validating 1792x1344 (204800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1792x1344" (mode clock too high)
(II) CHROME(0): Not using mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1856x1392 (218300)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1856x1392" (mode clock too high)
(II) CHROME(0): Not using mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1800x1440 (230000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1800x1440" (mode clock too high)
(II) CHROME(0): Not using mode "1800x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (43160)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "640x480" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 768x576 (34960)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 768x576 (42930)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 768x576 (45510)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 768x576 (51840)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "768x576" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 768x576 (62570)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "768x576" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 800x600 (68180)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "800x600" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (113310)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1024x768" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (119650)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1152x864" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (143470)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1152x864" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (124540)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x960 (129860)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x960 (178990)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1280x960" (hsync out of range)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (190960)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1280x1024" (hsync out of range)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (122610)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (149340)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1400x1050" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (155850)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1400x1050" (mode clock too high)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (179260)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1400x1050" (vrefresh out of range)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (214390)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "1400x1050" (hsync out of range)
(II) CHROME(0): Not using mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (72000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1360x768" (monitor doesn't support reduced
blanking)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (84750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (106500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1024 (103125)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (119000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (monitor doesn't support reduced
blanking)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (146250)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (mode clock too high)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (174000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (mode clock too high)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (187000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (mode clock too high)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (214750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1080 (138500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1920x1080" (monitor doesn't support reduced
blanking)
(II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1200 (154000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1920x1200" (monitor doesn't support reduced
blanking)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (30240)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25200)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 720x400 (28320)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108883)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1280x960 (102103)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104992)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using mode "720x480" (no mode of this name)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(--) CHROME(0): Virtual size is 1024x768 (pitch 1024)
(**) CHROME(0): *Driver mode "1024x768": 78.8 MHz (scaled from -1937560.4 MHz), 60.1 kHz,
75.1 Hz
(II) CHROME(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800
+hsync +vsync (60.1 kHz)
(**) CHROME(0): *Driver mode "800x600": 49.5 MHz (scaled from -405002.9 MHz), 46.9 kHz,
75.0 Hz
(II) CHROME(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync
+vsync (46.9 kHz)
(**) CHROME(0): *Driver mode "640x480": 31.5 MHz (scaled from 1694528.7 MHz), 37.5 kHz,
75.0 Hz
(II) CHROME(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync
-vsync (37.5 kHz)
(**) CHROME(0): Display dimensions: (340, 270) mm
(**) CHROME(0): DPI set to (76, 72)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.5.3, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.5.3, module version = 1.2.1
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1        0        0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1        0        0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1        0        0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1        0        0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [25] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [26] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [27] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [28] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [29] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [30] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [31] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [32] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [33] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
        [34] -1        0        0x0000ffff - 0x0000ffff (0x1) IX[B]
        [35] -1        0        0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xf4000000 with size 0x4000000
(--) CHROME(0): Frame buffer start: 0xb3a1c000, free start: 0x180000 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xfb000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xfb200000 with size 0x20000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VT162xSave
(II) CHROME(0): VIAWriteMode
(II) CHROME(0): ViaModePrimary
(II) CHROME(0): ViaModePrimaryVGA
(II) CHROME(0): ViaModePrimaryVGA: Setting up 1024x768
(II) CHROME(0): CrtcHTotal: 0x520
(II) CHROME(0): CrtcHDisplay: 0x400
(II) CHROME(0): CrtcHBlankStart: 0x400
(II) CHROME(0): CrtcHBlankEnd: 0x520
(II) CHROME(0): CrtcHSyncStart: 0x410
(II) CHROME(0): CrtcHSyncEnd: 0x470
(II) CHROME(0): CrtcVTotal: 0x320
(II) CHROME(0): CrtcVDisplay: 0x300
(II) CHROME(0): CrtcVSyncStart: 0x301
(II) CHROME(0): CrtcVSyncEnd: 0x304
(II) CHROME(0): CrtcVBlankStart: 0x300
(II) CHROME(0): CrtcVBlankEnd: 0x320
(II) CHROME(0): Offset: 0x100
(II) CHROME(0): Fetch Count: 0x100
(II) CHROME(0): ViaTVPower: Off.
(II) CHROME(0): VT1625Power
(II) CHROME(0): ViaSetPrimaryFIFO
(II) CHROME(0): ViaSetPrimaryDotclock to 0x2a8800
(II) CHROME(0): ViaSetUseExternalClock
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): - Blanked
(WW) CHROME(0): Direct rendering is not supported when Xinerama is enabled
(EE) CHROME(0): [dri] DRIScreenInit failed.  Disabling DRI.
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): Using 2304 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        8x8 color pattern filled rectangles
        Solid Lines
        Dashed Lines
        Image Writes
        Setting up tile and stipple cache:
                31 128x128 slots
                12 256x256 slots
                4 512x512 slots
                32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): - Palette loaded
(**) Option "dpms" "true"
(**) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): direct rendering disabled
(II) CHROME(0): Benchmarking video copy.  Less time is better.
(--) CHROME(0): Timed   libc YUV420 copy... 10603509. Throughput: 44.6 MiB/s.
(--) CHROME(0): Timed kernel YUV420 copy... 10596406. Throughput: 44.7 MiB/s.
(--) CHROME(0): Timed    SSE YUV420 copy... 5826614. Throughput: 81.3 MiB/s.
(--) CHROME(0): Timed    MMX YUV420 copy... 5874891. Throughput: 80.6 MiB/s.
(--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
(--) CHROME(0): Timed   MMX2 YUV420 copy... 5850536. Throughput: 80.9 MiB/s.
Freed 6293504 (pool 1)
(--) CHROME(0): Using SSE YUV42X copy for video.
(WW) CHROME(0): [XvMC] Cannot use XvMC without DRI!
(WW) CHROME(0): Option "DDCMode" is not used
(WW) CHROME(0): Option "MonitorLayout" is not used
(II) CHROME(0): - Done
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/xorg/modules/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Keyboard0: always reports core events
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(WW) Option "XkbVariant" requires an string value
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "IMPS/2"
(**) USB Mouse: Device: "/dev/input/mice"
(**) USB Mouse: Protocol: "IMPS/2"
(**) Option "SendCoreEvents" "true"
(**) Option "CorePointer"
(**) USB Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "5"
(==) USB Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) USB Mouse: ZAxisMapping: buttons 4 and 5
(**) USB Mouse: Buttons: 9
(**) USB Mouse: Sensitivity: 1
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) evaluating device (USB Mouse)
(II) XINPUT: Adding extended input device "USB Mouse" (type: MOUSE)
(II) USB Mouse: ps2EnableDataReporting: succeeded
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut

```

Anyway, help very much appreciated.

---

