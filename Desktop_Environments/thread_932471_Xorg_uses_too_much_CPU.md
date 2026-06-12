---
title: "Xorg uses too much CPU"
date: 2008-09-28
forum: Desktop Environments
---

### Post by soleblaze on 2008-09-28
Xorg is taking a lot of CPU use.  Having just conky on the screen makes it jump to around 30-40%.  a few terminals open that are updating information every second or two brings it up to 60%.  Firefox running a youtube video takes it to 90%.  

I'm wondering if I don't have my driver running correctly or if it doesn't have DMA or something.  Has anyone experienced and solved this problem?

I'm running on an Aspire One, which uses the 945GM chipset.  I'm running XFCE with dual monitors (1024x600 and 1920x1200) but this also does it when I'm only using 1024x600.  I currently have composite enabled, but I've also had it disabled.. I've tried RenderAccel False and making Virtual 1920 1800 and putting my screens top and bottom instead of left and right.

xorg.conf: 

```

Section "ServerLayout"
   Identifier     "Default Layout"
   Screen      0  "Screen0" 0 0
   InputDevice    "Mouse0" "CorePointer"
   InputDevice    "Synaptics Mouse" "AlwaysCore"
   InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "InputDevice"
   Identifier  "Keyboard0"
   Driver      "kbd"
   Option       "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbVariant" "euro"
        Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
   Identifier "Synaptics Mouse"
        Driver     "synaptics"
        Option     "Device" "/dev/psaux"
        Option     "Protocol" "auto-dev"
   Option      "LeftEdge"  "1700"
     Option   "RightEdge"     "5300"
     Option   "TopEdge"       "1700"
     Option   "BottomEdge"    "4200"
     Option   "FingerLow"   "25"
     Option   "FingerHigh"   "30"
     Option   "MaxTapTime"   "180"
     Option   "MaxTapMove"   "220"
     Option   "VertScrollDelta" "100"
     Option   "MinSpeed"   "0.09"
     Option   "MaxSpeed"   "0.18"
     Option   "AccelFactor"   "0.0015"
     Option   "SHMConfig"   "on"
   Option  "ZAxisMapping"   "4 5 6 7"
EndSection

Section "InputDevice"
   Identifier  "Mouse0"
   Driver      "mouse"
   Option       "Protocol" "IMPS/2"
   Option       "Device" "/dev/input/mice"
   Option       "ZAxisMapping" "4 5"
   Option       "Emulate3Buttons" "no"
EndSection

Section "Monitor"
   Identifier  "Monitor0"
   DisplaySize 195 113
   Modeline  "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +VSync
   Option "DPMS"
EndSection

Section "Monitor"
   Identifier "Monitor1"
   Option   "Rightof" "Monitor0"
   Option "DPMS"
EndSection

Section "Monitor"
   Identifier "TV"
   Option   "Ignore" "True"
EndSection

Section "Device"
   Identifier  "Videocard0"
   Driver      "intel"
   Option      "monitor-LVDS" "Monitor0"
   Option       "monitor-VGA" "Monitor1"
   Option       "monitor-TV" "TV"
   Option       "AccelMethod" "EXA"
   Option       "MigrationHeuristic" "greedy"
   Option 	"CacheLines" "1980"
   VideoRam	229376
   Option  "MonitorLayout"   "LVDS,VGA"
   BusID   "PCI:0:2:0"
EndSection

Section "Screen"
   Identifier "Screen0"
   Device     "Videocard0"
   Monitor       "Monitor0"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
      Modes    "1920x1200" "1024x600" "800x600" "640x480"
      Virtual 2944 1200
   EndSubSection
EndSection 

```

Xorg.0.log can be found [here](http://pastebin.com/f4129a8df)

---

### Post by mihaiv on 2008-09-28
What application do you use to determine CPU usage? There is a known issue with gnome system monitor. Try to use the command top.

---

### Post by soleblaze on 2008-09-28
> **mihaiv said:**
> What application do you use to determine CPU usage? There is a known issue with gnome system monitor. Try to use the command top.

I use top.  Of course running top itself generates 10% Xorg use. (Right now with firefox open, pidgin, a current idle xfce4-terminal, and a rather long window running top..my Xorg is at 51%)

---

### Post by soleblaze on 2008-09-28
TOP with Conky running (this is a hyperthreaded computer):

```

top - 15:48:02 up 1 day,  3:50,  5 users,  load average: 0.53, 0.45, 0.39
Tasks: 125 total,   2 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.7%us,  1.0%sy,  0.0%ni, 83.2%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1541264k total,  1498724k used,    42540k free,   115628k buffers
Swap:  5119992k total,        8k used,  5119984k free,   754252k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                      
 9211 root      20   0  380m 101m 8944 R   24  6.8 562:27.33 Xorg                                          
 2553 soleblaz  20   0 10700 1768 1060 S    5  0.1   0:18.44 conky                                        
 2456 soleblaz  20   0 56132  28m  12m S    3  1.9   0:43.65 xchat                                        
 2558 root      20   0  2416 1144  872 R    1  0.1   0:01.74 top                                          
 9405 soleblaz  20   0 14496 5636 4680 S    1  0.4   7:30.19 xfce4-systemloa                              
25061 soleblaz  20   0  363m 204m  23m S    1 13.6  24:05.65 firefox                                      
 9357 soleblaz  20   0 21580 6348 4656 S    0  0.4   1:32.81 gnome-screensav                              
 9359 soleblaz  20   0 20932  11m 6816 S    0  0.8   3:23.38 xfwm4                                        
 9364 soleblaz  20   0 29336  15m 8124 S    0  1.0   1:39.77 xfce4-panel                                  
 9403 soleblaz  20   0 28740  13m 7708 S    0  0.9   1:05.70 xfce4-mixer-plu                              
 9438 soleblaz  20   0 42864  23m 8512 S    0  1.6 123:24.01 xfce4-terminal                             
    1 root      20   0  3056 1948  624 S    0  0.1   0:02.32 init                                         
    2 root      15  -5     0    0    0 S    0  0.0   0:00.04 kthreadd                                     
    3 root      RT  -5     0    0    0 S    0  0.0   0:02.94 migration/0   

```

Top without conky:

```

top - 15:49:54 up 1 day,  3:52,  5 users,  load average: 0.56, 0.49, 0.40
Tasks: 124 total,   1 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.0%us,  1.3%sy,  0.0%ni, 90.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1541264k total,  1485264k used,    56000k free,   115704k buffers
Swap:  5119992k total,        8k used,  5119984k free,   754276k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                      
 2456 soleblaz  20   0 56132  28m  12m S    9  1.9   0:53.65 xchat                                       
 9211 root      20   0  353m  88m 8944 S    7  5.9 562:56.97 Xorg                                         
 2558 root      20   0  2416 1144  872 R    1  0.1   0:02.52 top                                          
25061 soleblaz  20   0  363m 204m  23m S    1 13.6  24:16.02 firefox                                      
 9359 soleblaz  20   0 20932  11m 6816 S    1  0.8   3:24.53 xfwm4                                        
 4783 root      15  -5     0    0    0 S    0  0.0   0:41.46 kondemand/0                                  
 9405 soleblaz  20   0 14496 5636 4680 S    0  0.4   7:30.67 xfce4-systemloa                              
 9438 soleblaz  20   0 42864  23m 8512 S    0  1.6 123:24.54 xfce4-terminal                               
    1 root      20   0  3056 1948  624 S    0  0.1   0:02.32 init                                         
    2 root      15  -5     0    0    0 S    0  0.0   0:00.04 kthreadd                                     
    3 root      RT  -5     0    0    0 S    0  0.0   0:02.94 migration/0                                 
    4 root      15  -5     0    0    0 S    0  0.0   0:37.75 ksoftirqd/0                                  
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                   
    9 root      15  -5     0    0    0 S    0  0.0   0:04.38 events/0

```

---

### Post by kerry_s on 2008-09-28
couple of things i see.

try xaa instead of exa

in your log this is wrong and not needed:    VideoRam	229376

your running 2 screens of different sizes, combined the screen size is to large for the vid card, not enough memory, so you don't have dri, aka accelerated graphics, so it doesn't surprise me that xorg is working very hard in real time to keep up. recommend you drop down to 1 monitor or run both at a lower res and at the same size.

---

### Post by soleblaze on 2008-09-28
Ok, I have a new xorg.conf now.  It doesn't appear anything has changed in relation to Xorg CPU usage (Although now my fonts are the correct size in gdm).  I've also tried this with Virtual set to 1024x600 and just using the laptop monitor.

```

Section "ServerLayout"
   Identifier     "Default Layout"
   Screen      0  "Screen0" 0 0
   InputDevice    "Mouse0" "CorePointer"
   InputDevice    "Synaptics Mouse" "AlwaysCore"
   InputDevice    "Keyboard0" "CoreKeyboard"
   Option  "DRI2" "true"
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

Section "InputDevice"
   Identifier  "Keyboard0"
   Driver      "kbd"
   Option       "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbVariant" "euro"
        Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
   Identifier "Synaptics Mouse"
        Driver     "synaptics"
        Option     "Device" "/dev/psaux"
        Option     "Protocol" "auto-dev"
   Option      "LeftEdge"  "1700"
     Option   "RightEdge"     "5300"
     Option   "TopEdge"       "1700"
     Option   "BottomEdge"    "4200"
     Option   "FingerLow"   "25"
     Option   "FingerHigh"   "30"
     Option   "MaxTapTime"   "180"
     Option   "MaxTapMove"   "220"
     Option   "VertScrollDelta" "100"
     Option   "MinSpeed"   "0.09"
     Option   "MaxSpeed"   "0.18"
     Option   "AccelFactor"   "0.0015"
     Option   "SHMConfig"   "on"
   Option  "ZAxisMapping"   "4 5 6 7"
EndSection

Section "InputDevice"
   Identifier  "Mouse0"
   Driver      "mouse"
   Option       "Protocol" "IMPS/2"
   Option       "Device" "/dev/input/mice"
   Option       "ZAxisMapping" "4 5"
   Option       "Emulate3Buttons" "no"
EndSection

Section "Monitor"
   Identifier  "Monitor0"
EndSection

Section "Monitor"
   Identifier "Monitor1"
   Option   "Below" "Monitor0"
EndSection


Section "Device"
   Identifier  "Videocard0"
   Driver      "intel"
   Option      "monitor-LVDS" "Monitor0"
   Option       "monitor-VGA" "Monitor1"
   Option       "AccelMethod" "xaa"
   BusID   "PCI:0:2:0"
EndSection

Section "Screen"
   Identifier "Screen0"
   Device     "Videocard0"
   Monitor       "Monitor0"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
      Modes    "1920x1200" "1024x600" "800x600" "640x480"
      Virtual 2048 2048
   EndSubSection
EndSection 

```

I'm going to do a BIOS version downgrade tomorrow and see if that helps anything.

---

### Post by kerry_s on 2008-09-28
i need to see the new xorg.0.log that go's with the new xorg.conf.

you want to try and work your way down the log to get rid of as much (EE) as you can.

for example mine only has warnings that i can't do anything about.

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: UNKNOWN 
Current Operating System: Linux debian 2.6.18-6-k7 #1 SMP Mon Aug 18 09:20:26 UTC 2008 i686
Build Date: 29 May 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 27 15:41:07 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3116 card 1106,3116 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1462,7380 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1462,7380 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1462,7380 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1462,738c rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 5333,8d04 card 1462,7389 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd80fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) S3 Inc. VT8375 [ProSavage8 KM266/KL266] rev 0, Mem @ 0xd8000000/19, 0xd0000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd8101000 - 0xd81010ff (0x100) MX[B]
	[1] -1	0	0xd8100000 - 0xd81000ff (0x100) MX[B]
	[2] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[4] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[8] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd8101000 - 0xd81010ff (0x100) MX[B]
	[1] -1	0	0xd8100000 - 0xd81000ff (0x100) MX[B]
	[2] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[4] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[8] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8101000 - 0xd81010ff (0x100) MX[B]
	[5] -1	0	0xd8100000 - 0xd81000ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 2.1.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) SAVAGE: driver (version 2.1.2) for S3 Savage chipsets: Savage4,
	Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
	Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
	Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
	SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
	SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
	SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset ProSavageDDR found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8101000 - 0xd81010ff (0x100) MX[B]
	[5] -1	0	0xd8100000 - 0xd81000ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8101000 - 0xd81010ff (0x100) MX[B]
	[5] -1	0	0xd8100000 - 0xd81000ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(**) SAVAGE(0): Option "ShadowStatus" "off"
(**) SAVAGE(0): Option "BusType" "AGP"
(**) SAVAGE(0): Option "DmaType" "AGP"
(**) SAVAGE(0): Option "AGPMode" "4"
(**) SAVAGE(0): Option "AGPSize" "256"
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(**) SAVAGE(0): Option: ShadowStatus disabled
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) SAVAGE(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules/libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(--) SAVAGE(0): Chip: id 8d04, "ProSavage DDR-K"
(--) SAVAGE(0): Engine: "ProSavageDDR"
(--) SAVAGE(0): AGP card detected
(**) SAVAGE(0): BusType set to AGP
(**) SAVAGE(0): Using AGP DMA
(==) SAVAGE(0): Will try command and vertex DMA mode
(**) SAVAGE(0): Using AGP 4x mode
(**) SAVAGE(0): Using 256 MB AGP aperture
(==) SAVAGE(0): Write-combining range (0xd0000000,0x8000000)
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram:  32768k
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(--) SAVAGE(0): No DDC signal
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" removed.
(II) SAVAGE(0): Manufacturer: SAM  Model: 413b  Serial#: 1346842937
(II) SAVAGE(0): Year: 2000  Week: 13
(II) SAVAGE(0): EDID Version: 1.2
(II) SAVAGE(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) SAVAGE(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) SAVAGE(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) SAVAGE(0): Gamma: 2.28
(II) SAVAGE(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) SAVAGE(0): First detailed timing is preferred mode
(II) SAVAGE(0): GTF timings supported
(II) SAVAGE(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) SAVAGE(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) SAVAGE(0): Supported VESA Video Modes:
(II) SAVAGE(0): 720x400@70Hz
(II) SAVAGE(0): 720x400@88Hz
(II) SAVAGE(0): 640x480@60Hz
(II) SAVAGE(0): 640x480@67Hz
(II) SAVAGE(0): 640x480@72Hz
(II) SAVAGE(0): 640x480@75Hz
(II) SAVAGE(0): 800x600@56Hz
(II) SAVAGE(0): 800x600@60Hz
(II) SAVAGE(0): 800x600@72Hz
(II) SAVAGE(0): 800x600@75Hz
(II) SAVAGE(0): 832x624@75Hz
(II) SAVAGE(0): 1024x768@87Hz (interlaced)
(II) SAVAGE(0): 1024x768@60Hz
(II) SAVAGE(0): 1024x768@70Hz
(II) SAVAGE(0): 1024x768@75Hz
(II) SAVAGE(0): 1280x1024@75Hz
(II) SAVAGE(0): 1152x870@75Hz
(II) SAVAGE(0): Manufacturer's mask: 0
(II) SAVAGE(0): Supported Future Video Modes:
(II) SAVAGE(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) SAVAGE(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) SAVAGE(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) SAVAGE(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) SAVAGE(0): #4: hsize: 1600  vsize 1200  refresh: 65  vid: 17833
(II) SAVAGE(0): #5: hsize: 1024  vsize 768  refresh: 100  vid: 26721
(II) SAVAGE(0): Supported additional Video Mode:
(II) SAVAGE(0): clock: 135.0 MHz   Image Size:  352 x 264 mm
(II) SAVAGE(0): h_active: 1280  h_sync: 1296  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) SAVAGE(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) SAVAGE(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 85 kHz,
(II) SAVAGE(0): Monitor name: S/M 955DF
(II) SAVAGE(0): Serial No: H3LN313779
(--) SAVAGE(0): Detected current MCLK value of 14.318 MHz
(--) SAVAGE(0): 4064x1496 TFT LCD panel detected but not active
(--) SAVAGE(0): Found 13 modes at this depth:
    [10e] 320 x 200, 70Hz
    [133] 320 x 240, 72Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [11d] 640 x 400, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz, 160Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz
    [117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 100Hz, 130Hz
    [17a] 1280 x 768, 60Hz
    [14f] 1280 x 960, 60Hz, 85Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 100Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [122] 1600 x 1200, 60Hz
(II) SAVAGE(0): Generic Monitor: Using hsync range of 30.00-85.00 kHz
(II) SAVAGE(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) SAVAGE(0): Clock range:  10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(WW) (640x400,Generic Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(WW) (320x200,Generic Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(WW) (640x480,Generic Monitor) mode clock 25.2MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(WW) (320x240,Generic Monitor) mode clock 12.6MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(WW) (640x480,Generic Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(WW) (320x240,Generic Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(WW) (640x480,Generic Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(WW) (320x240,Generic Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(WW) (640x480,Generic Monitor) mode clock 36MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(WW) (320x240,Generic Monitor) mode clock 18MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(WW) (800x600,Generic Monitor) mode clock 36MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(WW) (400x300,Generic Monitor) mode clock 18MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(WW) (800x600,Generic Monitor) mode clock 40MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(WW) (400x300,Generic Monitor) mode clock 20MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(WW) (800x600,Generic Monitor) mode clock 50MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(WW) (400x300,Generic Monitor) mode clock 25MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(WW) (800x600,Generic Monitor) mode clock 49.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(WW) (400x300,Generic Monitor) mode clock 24.75MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(WW) (800x600,Generic Monitor) mode clock 56.3MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(WW) (400x300,Generic Monitor) mode clock 28.15MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(WW) (1024x768,Generic Monitor) mode clock 44.9MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(WW) (512x384,Generic Monitor) mode clock 22.45MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(WW) (1024x768,Generic Monitor) mode clock 65MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(WW) (512x384,Generic Monitor) mode clock 32.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(WW) (1024x768,Generic Monitor) mode clock 75MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(WW) (512x384,Generic Monitor) mode clock 37.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(WW) (1024x768,Generic Monitor) mode clock 78.8MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(WW) (512x384,Generic Monitor) mode clock 39.4MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(WW) (1024x768,Generic Monitor) mode clock 94.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(WW) (512x384,Generic Monitor) mode clock 47.25MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 75Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): Chose mode 14f at 60Hz.
(WW) (1280x960,Generic Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(WW) (640x480,Generic Monitor) mode clock 54MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 14f at 85Hz.
(WW) (1280x960,Generic Monitor) mode clock 148.5MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1280x960" (hsync out of range)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(WW) (640x480,Generic Monitor) mode clock 74.25MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(WW) (1280x1024,Generic Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 75Hz.
(WW) (1280x1024,Generic Monitor) mode clock 135MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 85Hz.
(WW) (1280x1024,Generic Monitor) mode clock 157.5MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(WW) (800x600,Generic Monitor) mode clock 81MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(WW) (800x600,Generic Monitor) mode clock 87.75MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(WW) (800x600,Generic Monitor) mode clock 94.5MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(WW) (800x600,Generic Monitor) mode clock 101.25MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(WW) (800x600,Generic Monitor) mode clock 114.75MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1792x1344 60Hz.
(II) SAVAGE(0): Not using default mode "1792x1344" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1856x1392 60Hz.
(II) SAVAGE(0): Not using default mode "1856x1392" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1440 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1440" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(--) SAVAGE(0): Chose mode 17a at 60Hz.
(WW) (1280x768,Generic Monitor) mode clock 80.14MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x384 60Hz.
(II) SAVAGE(0): Not using default mode "640x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1280x800 59Hz.
(II) SAVAGE(0): Not using default mode "1280x800" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(WW) (640x400,Generic Monitor) mode clock 41.73MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 1152x768 54Hz.
(II) SAVAGE(0): Not using default mode "1152x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x384 54Hz.
(II) SAVAGE(0): Not using default mode "576x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1152x864 85Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 60Hz.
(WW) (1400x1050,Generic Monitor) mode clock 122MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(WW) (1400x1050,Generic Monitor) mode clock 151MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(WW) (1400x1050,Generic Monitor) mode clock 155.8MHz exceeds DDC maximum 0MHz
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): Chose mode 13c at 75Hz.
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1400x1050" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1440x900 60Hz.
(II) SAVAGE(0): Not using default mode "1440x900" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 60Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1600x1024 59Hz.
(II) SAVAGE(0): Not using default mode "1600x1024" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 60Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 60Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 72Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 72Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(WW) (1024x768,Generic Monitor) mode clock 133.475MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(WW) (1024x768,Generic Monitor) mode clock 170.24MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(WW) (1024x768,Generic Monitor) mode clock 194.02MHz exceeds DDC maximum 0MHz
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 11a at 75Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(--) SAVAGE(0): Chose mode 14f at 60Hz.
(--) SAVAGE(0): Chose mode 17a at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(--) SAVAGE(0): Virtual size is 1280x1024 (pitch 1280)
(**) SAVAGE(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) SAVAGE(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) SAVAGE(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) SAVAGE(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) SAVAGE(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) SAVAGE(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) SAVAGE(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) SAVAGE(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) SAVAGE(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) SAVAGE(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) SAVAGE(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SAVAGE(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) SAVAGE(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) SAVAGE(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) SAVAGE(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) SAVAGE(0): Modeline "800x600"   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "800x600"   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) SAVAGE(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) SAVAGE(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) SAVAGE(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) SAVAGE(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) SAVAGE(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) SAVAGE(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(++) SAVAGE(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MS[B]
	[1] 0	0	0xd8000000 - 0xd807ffff (0x80000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd8101000 - 0xd81010ff (0x100) MX[B]
	[7] -1	0	0xd8100000 - 0xd81000ff (0x100) MX[B]
	[8] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 3.0
(II) SAVAGE(0): VESA VBE Total Mem: 31680 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Graphics ProSavage DDR Family BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 2.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Garphics Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 3.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 0.0
(==) SAVAGE(0): Write-combining range (0xd0000000,0x8000000)
(WW) SAVAGE(0): Cannot read colourmap from VGA.  Will restore with default
(II) SAVAGE(0): 7812 kB of Videoram needed for 3D; 32768 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) SAVAGE(0): [drm] loaded kernel module for "savage" driver
(II) SAVAGE(0): [drm] DRM interface version 1.2
(II) SAVAGE(0): [drm] created "savage" driver at busid "pci:0000:01:00.0"
(II) SAVAGE(0): [drm] added 8192 byte SAREA at 0xf90b7000
(II) SAVAGE(0): [drm] mapped SAREA 0xf90b7000 to 0xa79dc000
(II) SAVAGE(0): [drm] framebuffer handle = 0xd0000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): [agp] Mode 0x1f000217 [AGP 0x1106/0x3116; Card 0x5333/0x8d04]
(II) SAVAGE(0): [agp] 262144 kB allocated with handle 0x00000001
(II) SAVAGE(0): [agp] command DMA handle = 0xc0000000
(II) SAVAGE(0): [agp] agpTextures handle = 0xc0100000
(II) SAVAGE(0): [drm] aperture handle = 0xd2000000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 11a at 75Hz.
(II) SAVAGE(0): virtualX:1280,virtualY:1024
(II) SAVAGE(0): bpp:16,tiledwidthBytes:2560,tiledBufferSize:2621440 
(II) SAVAGE(0): bpp:16,widthBytes:2560,BufferSize:2621440 
(II) SAVAGE(0): videoRambytes:0x02000000 
(II) SAVAGE(0): textureSize:0x0165f000 
(II) SAVAGE(0): textureSize:0x0165f000 
(II) SAVAGE(0): textureOffset:0x00980000 
(II) SAVAGE(0): depthOffset:0x00700000,depthPitch:2560
(II) SAVAGE(0): backOffset:0x00480000,backPitch:2560
(II) SAVAGE(0): Reserved back buffer at offset 0x480000
(II) SAVAGE(0): Reserved depth buffer at offset 0x700000
(II) SAVAGE(0): Reserved 22908 kb for textures at offset 0x980000
(II) SAVAGE(0): Using 818 lines for offscreen memory.
(**) SAVAGE(0): Option "XaaNoOffscreenPixmaps" "true"
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		7 256x256 slots
(**) SAVAGE(0): Option "BackingStore" "true"
(**) SAVAGE(0): Backing store enabled
(**) Option "dpms"
(**) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]	reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]	reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]	chipset:0x00000000
(II) SAVAGE(0): [junkers]	sgram:0x00000000
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00280000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	frontPitch:0x00000a00
(II) SAVAGE(0): [junkers]	backbufferSize:0x00280000
(II) SAVAGE(0): [junkers]	backOffset:0x00480000
(II) SAVAGE(0): [junkers]	backPitch:0x00000a00
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00280000
(II) SAVAGE(0): [junkers]	depthOffset:0x00700000
(II) SAVAGE(0): [junkers]	depthPitch:0x00000a00
(II) SAVAGE(0): [junkers]	textureOffset:0x00980000
(II) SAVAGE(0): [junkers]	textureSize:0x0165f000
(II) SAVAGE(0): [junkers]	textureSize:0x0165f000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	agp:handle:0x00000001
(II) SAVAGE(0): [junkers]	agp:offset:0x10000000
(II) SAVAGE(0): [junkers]	agp:size:0x10000000
(II) SAVAGE(0): [junkers]	agp:map:0x00000000
(II) SAVAGE(0): [junkers]	registers:handle:0xd8000000
(II) SAVAGE(0): [junkers]	registers:offset:0x00000000
(II) SAVAGE(0): [junkers]	registers:size:0x00080000
(II) SAVAGE(0): [junkers]	registers:map:0x00000000
(II) SAVAGE(0): [junkers]	status:handle:0x00000000
(II) SAVAGE(0): [junkers]	status:offset:0x00000000
(II) SAVAGE(0): [junkers]	status:size:0x00000000
(II) SAVAGE(0): [junkers]	status:map:0x00000000
(II) SAVAGE(0): [junkers]	agpTextures:handle:0xc0100000
(II) SAVAGE(0): [junkers]	agpTextures:offset:0x00100000
(II) SAVAGE(0): [junkers]	agpTextures:size:0x0ff00000
(II) SAVAGE(0): [junkers]	apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:handle:0xc0000000
(II) SAVAGE(0): [junkers]	cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]	cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]	cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]	chipset:0x00000006
(II) SAVAGE(0): [junkers]	width:0x00000500
(II) SAVAGE(0): [junkers]	height:0x00000400
(II) SAVAGE(0): [junkers]	mem:0x02000000
(II) SAVAGE(0): [junkers]	cpp:2
(II) SAVAGE(0): [junkers]	zpp:2
(II) SAVAGE(0): [junkers]	agpMode:4
(II) SAVAGE(0): [junkers]	bufferSize:65536
(II) SAVAGE(0): [junkers]	frontbufferSize:0x00280000
(II) SAVAGE(0): [junkers]	frontOffset:0x00000000
(II) SAVAGE(0): [junkers]	backbufferSize:0x00280000
(II) SAVAGE(0): [junkers]	backOffset:0x00480000
(II) SAVAGE(0): [junkers]	depthbufferSize:0x00280000
(II) SAVAGE(0): [junkers]	depthOffset:0x00700000
(II) SAVAGE(0): [junkers]	textureOffset:0x00980000
(II) SAVAGE(0): [junkers]	textureSize:0x01600000
(II) SAVAGE(0): [junkers]	logTextureGranularity:0x00000015
(II) SAVAGE(0): [junkers]	agpTextureHandle:0xc0100000
(II) SAVAGE(0): [junkers]	agpTextureSize:0x0f000000
(II) SAVAGE(0): [junkers]	logAgpTextureGranularity:0x00000018
(II) SAVAGE(0): [junkers]	apertureHandle:0xd2000000
(II) SAVAGE(0): [junkers]	apertureSize:0x05000000
(II) SAVAGE(0): [junkers]	aperturePitch:0x00001000
(II) SAVAGE(0): [junkers]	statusHandle:0x00000000
(II) SAVAGE(0): [junkers]	statusSize:0x00000000
(II) SAVAGE(0): [junkers]	sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
(==) RandR enabled
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
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "IMPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "IMPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc104)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) Open ACPI successful (/var/run/acpid.socket)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by soleblaze on 2008-09-28
Here's the Xorg.0.log file:

```
(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
X.Org X Server 1.5.1
Release Date: 23 September 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server i686 Ubuntu
Current Operating System: Linux shodan 2.6.27-4-generic #1 SMP Wed Sep 24 01:30:51 UTC 2008 i686
Build Date: 24 September 2008  06:28:32PM
xorg-server 2:1.5.1-1ubuntu1 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 28 19:42:33 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Synaptics Mouse"
(**) |-->Input Device "Keyboard0"
(**) Option "DRI2" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d8a40
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
        X.Org Server Extension : 1.1
        X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0x78480000/0, 0x60000000/0, 0x78500000/0, I/O @ 0x000060c0/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0x78400000/0
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.0.0
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.5.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.5.0, module version = 2.4.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.4.99.905, module version = 1.3.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.5.0, module version = 0.15.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.4.99.905, module version = 1.3.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile Intel® GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 4.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "xaa"
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(--) intel(0): Linear framebuffer at 0x60000000
(--) intel(0): IO registers at addr 0x78480000
(II) intel(0): 2 display pipes available.
(**) intel(0): Using XAA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Monitor1
(**) intel(0): Option "Below" "Monitor0"
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS using monitor section Monitor0
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "DEL", prod id 41005
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -(II) intel(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kHz)
(II) intel(0): EDID vendor "DEL", prod id 41005
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Output VGA connected
(II) intel(0): Output LVDS connected
(II) intel(0): Using user preference for initial modes
(II) intel(0): Output VGA using initial mode 1920x1200
(II) intel(0): Output LVDS using initial mode 1024x600
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (520, 320) mm
(**) intel(0): DPI set to (100, 162)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.5.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 363520 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1454076 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0hsync +vsync (67.7 kHz)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Allocating 6144 scanlines for pixmap cache
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0x78480000
(II) intel(0): [drm] ring buffer = 0x60000000
(II) intel(0): [drm] mapped front buffer at 0x64000000, handle = 0x64000000
(II) intel(0): [drm] mapped back buffer at 0x61000000, handle = 0x61000000
(II) intel(0): [drm] mapped depth buffer at 0x62000000, handle = 0x62000000
(II) intel(0): [drm] mapped classic textures at 0x68000000, handle = 0x68000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x08000000 (pgoffset 32768)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000005f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000005fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000005fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000005fe33000 physical
)
(II) intel(0): 0x00634000-0x00643fff: xaa scratch (64 kB)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: back buffer (16384 kB) X tiled
(II) intel(0): 0x02000000-0x02ffffff: depth buffer (16384 kB) X tiled
(II) intel(0): 0x04000000-0x07ffffff: front buffer (65536 kB) X tiled
(II) intel(0): 0x08000000-0x09ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): using SSC reference clock of 96 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 365 x 339
(**) Option "Protocol" "IMPS/2"
(**) Mouse0: Device: "/dev/input/mice"
(**) Mouse0: Protocol: "IMPS/2"
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) Synaptics touchpad driver version 0.15.2
(--) Synaptics Mouse auto-dev sets device to /dev/input/event11
(II) Synaptics Mouse: x-axis range 1472 - 5472
(II) Synaptics Mouse: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event11"
(**) Option "SHMConfig" "on"
(**) Option "LeftEdge" "1700"
(**) Option "RightEdge" "5300"
(**) Option "TopEdge" "1700"
(**) Option "BottomEdge" "4200"
(**) Option "FingerLow" "25"
(**) Option "FingerHigh" "30"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "220"
(**) Option "VertScrollDelta" "100"
(--) Synaptics Mouse touchpad found
(**) Option "AlwaysCore"
(**) Synaptics Mouse: always reports core events
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
(**) Option "XkbVariant" "euro"
(**) Keyboard0: XkbVariant: "euro"
(**) Option "XkbOptions" "grp:alt_shift_toggle"
(**) Keyboard0: XkbOptions: "grp:alt_shift_toggle"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(II) evaluating device (Mouse0)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) evaluating device (Synaptics Mouse)
(II) XINPUT: Adding extended input device "Synaptics Mouse" (type: TOUCHPAD)
(II) evaluating device (Keyboard0)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) Synaptics Mouse: x-axis range 1472 - 5472
(II) Synaptics Mouse: y-axis range 1408 - 4448
(--) Synaptics Mouse touchpad found
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.5.0, module version = 2.0.99
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Apple, Inc Apple Keyboard
(**) Apple, Inc Apple Keyboard: always reports core events
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event3"
(II) Apple, Inc Apple Keyboard: Found keys
(II) Apple, Inc Apple Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Apple, Inc Apple Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Apple, Inc Apple Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Apple, Inc Apple Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Apple, Inc Apple Keyboard
(**) Apple, Inc Apple Keyboard: always reports core events
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event2"
(II) Apple, Inc Apple Keyboard: Found keys
(II) Apple, Inc Apple Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Apple, Inc Apple Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Apple, Inc Apple Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Apple, Inc Apple Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event11"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(WW) SynPS/2 Synaptics TouchPad can't grab event device, errno=16
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) intel(0): EDID vendor "DEL", prod id 41005
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
AUDIT: Sun Sep 28 19:42:47 2008: 6374 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6436 )
AUDIT: Sun Sep 28 19:42:47 2008: 6374 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6437 )
AUDIT: Sun Sep 28 19:42:47 2008: 6374 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6438 )
(II) intel(0): EDID vendor "DEL", prod id 41005
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): EDID vendor "DEL", prod id 41005
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): EDID vendor "DEL", prod id 41005
(II) intel(0): EDID vendor "AUO", prod id 4546
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
(II) intel(0): EDID vendor "AUO", prod id 4546

```

---

### Post by kerry_s on 2008-09-29
that looks good to me.
you can remove:    Option  "DRI2" "true"

in your log it says "(II) AIGLX: Screen 0 is not DRI2 capable"

have you tried disabling aiglx?

```
Section "ServerFlags"
Option  "AIGLX" "off"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection
```

---

### Post by soleblaze on 2008-09-29
Ok, I gave disabling AIGLX a try.  Still giving me the same performance hit.  It might just be normal with this machine and nothing I can do about it.  Who knows.  Do you have any other ideas what might help?

---

### Post by kerry_s on 2008-09-29
na, i'm out of ideas. try googling around, you may find something. what kind of apple laptop do you have?
[http://www.linux-on-laptops.com/apple.html](http://www.linux-on-laptops.com/apple.html)

---

### Post by soleblaze on 2008-09-30
> **kerry_s said:**
> na, i'm out of ideas. try googling around, you may find something. what kind of apple laptop do you have?
[http://www.linux-on-laptops.com/apple.html](http://www.linux-on-laptops.com/apple.html)

It's an Acer Aspire One, a netbook.  It might just not have the horsepower, although I've ran this stuff on an eee pc 701 without seeing this kind of spike.  Might be something with the hardware and bios.

---

### Post by kerry_s on 2008-09-30
> **soleblaze said:**
> It's an Acer Aspire One, a netbook.  It might just not have the horsepower, although I've ran this stuff on an eee pc 701 without seeing this kind of spike.  Might be something with the hardware and bios.

wow,it has a apple keyboard and mackintosh mouse, according to the xorg log.

hey i just noticed your top read out:

 9211 root      20   0  353m  88m 8944 S    7  5.9 562:56.97 Xorg  

looks pretty normal to me, mine is about the same, see pic, so i don't think it's high at all.
the higher one with conky, try adjusting your conky timing for a longer interval.

---

### Post by soleblaze on 2008-09-30
> **kerry_s said:**
> wow,it has a apple keyboard and mackintosh mouse, according to the xorg log.

hey i just noticed your top read out:

 9211 root      20   0  353m  88m 8944 S    7  5.9 562:56.97 Xorg  

looks pretty normal to me, mine is about the same, see pic, so i don't think it's high at all.
the higher one with conky, try adjusting your conky timing for a longer interval.

Well, I did have an apple keyboard plugged into it, but it was a Logitech MX mouse.. Who knows.  I'm gonna use it for awhile and see what happens.  I don't mind not using conky, but it was spiking rather high and causing lag when I had 3 terminals open.  Maybe all these changes helped out with that.  I guess I'll find out.

Thanks for all the suggestions.

---

### Post by thefunnyman on 2008-10-11
Hello,

I am experiencing similar issues to the OP when running conky.  When not running conky, cpu usage for Xorg hovers between 1% and 3%.  After starting conky, Xorg cpu usage hovers around 14%.  I'm running an Asus Eee PC with Xubuntu Intrepid Beta and a custom kernel developed by an eeeuser forum member. 

My Xorg.0.log
```

(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
X.Org X Server 1.5.1
Release Date: 23 September 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux mini 2.6.27-6-eeepc-lean #1 SMP Wed Oct 8 01:37:27 MDT 2008 i686
Build Date: 10 October 2008  11:01:44AM
xorg-server 2:1.5.1-1ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 11 17:56:37 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d8a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 4, Mem @ 0xf7f00000/0, 0xd0000000/0, 0xf7ec0000/0, I/O @ 0x0000ec00/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 4, Mem @ 0xf7f80000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) intel(0): Chipset: "915GM"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xF7F00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): found backlight control method /sys/class/backlight/eeepc
(II) intel(0): Output TV has no monitor section
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS using initial mode 1024x600
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000202 to 0x80000202
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 489216 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1956860 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xf7f00000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] mapped front buffer at 0xd0800000, handle = 0xd0800000
(II) intel(0): [drm] mapped back buffer at 0xd1800000, handle = 0xd1800000
(II) intel(0): [drm] mapped depth buffer at 0xd1c00000, handle = 0xd1c00000
(II) intel(0): [drm] mapped classic textures at 0xd2000000, handle = 0xd2000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 12582912 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00800000 (pgoffset 2048)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00c00000 (pgoffset 3072)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01c00000 (pgoffset 7168)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x02000000 (pgoffset 8192)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000007f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000007fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000007fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000007fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x00c00000-0x017fffff: exa offscreen (12288 kB)
(II) intel(0): 0x01800000-0x01bfffff: back buffer (4096 kB) X tiled
(II) intel(0): 0x01c00000-0x01ffffff: depth buffer (4096 kB) X tiled
(II) intel(0): 0x02000000-0x03ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 158
(II) config/hal: Adding input device Asus EeePC extra buttons
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Asus EeePC extra buttons: always reports core events
(**) Asus EeePC extra buttons: Device: "/dev/input/event6"
(II) Asus EeePC extra buttons: Found keys
(II) Asus EeePC extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Asus EeePC extra buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Asus EeePC extra buttons: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Asus EeePC extra buttons: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Asus EeePC extra buttons: xkb_layout: "us"
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event9"
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event4"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(EE) intel(0): Mode 1280x1024 does not fit virtual size 1024x1024 - internal error
AUDIT: Sat Oct 11 17:56:49 2008: 9011 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=9036 )
AUDIT: Sat Oct 11 17:56:49 2008: 9011 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=9037 )
AUDIT: Sat Oct 11 17:56:49 2008: 9011 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=9038 )
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(EE) intel(0): Mode 1280x1024 does not fit virtual size 1024x1024 - internal error
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(EE) intel(0): Mode 1280x1024 does not fit virtual size 1024x1024 - internal error
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(EE) intel(0): Mode 1280x1024 does not fit virtual size 1024x1024 - internal error
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(EE) intel(0): Mode 1280x1024 does not fit virtual size 1024x1024 - internal error

```

It's not a BIG deal as I can get most of the information I need via panel applets in xfce, but I don't recall having this problem with ubuntu hardy.

Anyone have any ideas?

---

