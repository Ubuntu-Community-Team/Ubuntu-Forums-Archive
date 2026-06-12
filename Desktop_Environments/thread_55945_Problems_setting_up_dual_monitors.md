---
title: "Problems setting up dual monitors"
date: 2005-08-10
forum: Desktop Environments
---

### Post by TheMikenator on 2005-08-10
Hello, I'm new here. I'm also new to Linux. I installed Ubuntu a few days ago and so far I'm loving it, however I've run into a few (many) problems while trying to set up my dual monitors.

First of all, a little about my setup: I have 2 monitors, a flatscreen (my primary) and a CRT (on the right of the flatscreen). They are both hooked up to ONE video card, a GeForce FX 5600 (one is in the regular VGA and the other is using a VGA->DVI transformer to hook into the DVI port). This worked perfectly for a very long time while using windows. 

Now, I've installed the Nvidia drivers from the website as well as the Nvidia-GLX thing. I've edited and reedited (and rereedited) my xorg.conf file many times using multiple sources, such as threads from this forum, the nvidia driver readme, a few websites and a friend that has been using Debian for a while. 

Now for the errors: Before I changed the Driver to "nvidia" (from nv) in the Device section of my xorg.conf file, it simply wouldnt work. The second monitor would just be fuzzy and screwey. Eventually I found out that I needed to change it to "nvidia" for the dual monitors to be operational. Thinking this would solve my problem I did so, but alas, it only made it worse. Now when I try to restart X, it tells me that it ran into an error and can't start. As per usual it asks if I want to see the diagnosis of the problem, I say yes and the only thing it shows me is this line: "Skipping '/user/X11R6/lib/Modules/libfb.a:fbmmx.o': no symbols found." And then, where it would usually go back to the console and I could switch back to my xorg.conf backup file, it just goes black and I can't type any commands, forcing me to ctrl alt del and reboot. Now I reboot into recovery mode so I can copy my Xorg.0.log file into my /root/ folder and change to the original xorg.conf file. Which leads me to the major issue: the log file shows no errors, it even shoes that the Nvidia drivers and the twinview and whatnot are operational. And this problem only occurs when I have "nvidia" set as my driver under the device section in xorg.conf. So I have no idea what's going on...did I install the drivers incorrectly or something?

Here is my xorg.conf file:
```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"	
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
    Identifier "GeForce FX 5600"
    VendorName "nvidia"
    Driver "nvidia"
    BusID  "PCI:1:0:0"
    Option "TwinView"
    Option "SecondMonitorHorizSync"   "31-82"
    Option "SecondMonitorVertRefresh" "55-120"
    Option "TwinViewOrientation"      "RightOf"
    Option "MetaModes"                "1280x1024,1280x1024; 1024x768,1024x768"
    Option "ConnectedMonitor"         "crt,crt"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Screen"
       Identifier   "Screen0"
       Device       "GeForce FX 5600"
       Monitor      "Monitor0"
       DefaultDepth    24
       Option "TwinView " "on"
       Option "TwinViewOrientation" "RightOf"
       Option "MetaModes" "1280x1024,1280x1024;1280x1024,1024x768;1280x1024,NULL;1280x1024,1280x1024+1200+0"
       Option "SecondMonitorHorizSync" "30 - 96.0"
       Option "SecondMonitorVertRefresh" "50 - 120"
       Subsection "Display"
               Depth       24
               Modes       "1280x1024" "1152x864" "1024x768"
       EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "ServerLayout"
    Screen      "Screen0"
    InputDevice "Configured Mouse"
    InputDevice "Generic Keyboard"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Also, here are a few lines from the log file:
```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "crt,crt"
(**) NVIDIA(0): Option "TwinView"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "31-82"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "55-120"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
(**) NVIDIA(0): ConnectedMonitor string: "crt,crt"
(**) NVIDIA(0): TwinView enabled
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xE4000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce FX 5600
(--) NVIDIA(0): VideoBIOS: 04.31.20.38.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(II) NVIDIA(0): Using ConnectedMonitor string "CRT-0, CRT-1"
(--) NVIDIA(0): CRT-0: maximum pixel clock: 400 MHz
(--) NVIDIA(0): CRT-1: maximum pixel clock: 400 MHz

```

---

