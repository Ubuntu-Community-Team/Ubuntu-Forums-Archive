---
title: "CompizFusion + VirtualBox + Xinerama + Fglrx (8.42) = Crash"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by eightballd on 2007-10-25
X seems to crash with this combination of applications/drivers (and only this combination).  The crash isn't instant, but it only takes a little less than a minute or so of usage and then it kicks me back to a terminal and then back to GDM.

Does anyone else have this problem?   The backtrace in my Xorg.0.log (see below) shows info from fglrx so I suspect that is the problem but I'd like to be sure so I know when to try again (as in, when fglrx is updated).

It's not a showstopper for me because desktop effects work when dual monitors aren't enabled and this is a laptop so that is often.  And VirtualBox works fine without desktops effects and fine with them as long as two monitors aren't attached.

I haven't tried yet to see if I have any problems if I'm in clone output mode but as far as use goes, that doesn't matter since I wouldn't use that while working.

Anyhow, below are my Xorg log with the backtrace and my xorg.conf.  If anyone has any ideas, I'd really appreciate it.

Also, I have an ATI Mobility X1300 and I am not using Xgl.  I'm using Gutsy and the latest Fglrx driver from ATI (with AIGLX).   32bit CPU

(tail of Xorg.0.log)
```

(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
Receive 3D performance mode message with status: 00000001
(II) XAA: Evicting pixmaps

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/lib/dri/fglrx_dri.so(_ZN5gllMB11SurfaceLoad7subLoadERKNS_8mbRefPtrINS_10MemoryDataEEEjjjjjjPKv+0x765) [0xb5219be5]
3: /usr/lib/dri/fglrx_dri.so(_ZN5gllMB11TextureData16updateTextureSubEP22glmbStateHandleTypeRec27gllmbRealTexImageTargetEnum14gslTexUnitEnumjiiijjj+0x36f) [0xb522706f]
4: /usr/lib/dri/fglrx_dri.so(_ZN5gllMB19internalTexSubImageEP22glmbStateHandleTypeRec27gllmbRealTexImageTargetEnum14gslTexUnitEnumjiiijjj23gllmbTexImageFormatEnum21gllmbTexImageTypeEnumNS_7StoreOpEPKv+0x662) [0xb521f6c2]
5: /usr/lib/dri/fglrx_dri.so(_Z15cxmbTexSubImageP22glmbStateHandleTypeRec27gllmbRealTexImageTargetEnum14gslTexUnitEnumjiiijjj23gllmbTexImageFormatEnum21gllmbTexImageTypeEnumPKv+0x6b) [0xb5220f5b]
6: /usr/lib/dri/fglrx_dri.so(_Z17epcxTexSubImage2DP22glcxStateHandleTypeRecjiiiiijjPKv+0xff) [0xb4f0f0af]
7: /usr/lib/dri/fglrx_dri.so(_ZN5gllEP20ep_tls_TexSubImage2DEjiiiiijjPKv+0xca) [0xb50e59ba]
8: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c3b211]
9: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c00bdc]
10: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c0031a]
11: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c04b2c]
12: /usr/bin/X [0x815754e]
13: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
14: /usr/bin/X(main+0x495) [0x8076f05]
15: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d66050]
16: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 8.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch

```

my xorg.conf
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "atiX1300Mobility"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Mode2" "1440x900"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "atiX1300Mobility"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1680x1050" "1440x900" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection


```

---

### Post by justmoon on 2008-02-14
Exact same problem here. Latest fglrx (Catalyst 8.2)

I've narrowed it down though. It has nothing to with VirtualBox (have been able to reproduce the crash with Eclipse, Wine and other programs) and I'm not using Xinerama... But! It has to do with high resolutions: For me, X crashes every time when three conditions are fulfilled:

1. AIGLX/Compiz is running
2. Screen resolution is high (crash happens all the time at 2560x1600, rock solid stable at 1920x1200 and everything below)
3. Something on the screen is redrawn / changed.

I also experience screen corruption (memory leaks), but also only on the same (higher) resolutions where I get the crash.

I had no problems with XGL and older versions of fglrx, so I'm pretty confident it's a bug in the new fglrx branch.

Here is my Xorg.0.log.old: (tail)
```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]
2: /usr/lib/dri/fglrx_dri.so [0xb4f638a3]
3: /usr/lib/dri/fglrx_dri.so [0xb4f659e2]
4: /usr/lib/dri/fglrx_dri.so [0xb4f73e08]
5: /usr/lib/dri/fglrx_dri.so [0xb4f7452d]
6: /usr/lib/dri/fglrx_dri.so [0xb4a4a8c8]
7: /usr/lib/dri/fglrx_dri.so [0xb4d278a5]
8: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c78211]
9: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c3dbdc]
10: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c3d31a]
11: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c41b2c]
12: /usr/bin/X [0x815765e]
13: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
14: /usr/bin/X(main+0x495) [0x8076f05]
15: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7da3050]
16: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 8.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch
```

And my xorg.conf
```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
	Option		"SendCoreEvents"	"true" 
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
	Identifier	"ATI Radeon X1900XTX"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 3007WFP"
	Option		"DPMS"
	HorizSync	28-128
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"DELL 3007WFP Screen"
	Device		"ATI Radeon X1900XTX"
	Monitor		"DELL 3007WFP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"2560x1600" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"

	Screen		"DELL 3007WFP Screen"

	InputDevice	"Generic Keyboard"
	InputDevice	"Logitech MX1000" "CorePointer"
	InputDevice     "Configured Mouse"
EndSection

```

---

### Post by monstrfolk on 2008-03-03
Same here. I have no idea how to fix it, but am looking for a solution. I will post here if i find one.

Xorg.0.log

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6d) [0x48672d]
1: /lib/libc.so.6 [0x2b6dd40fd7d0]
2: /usr/bin/X [0x53389c]
3: /usr/bin/X [0x533a96]
4: /usr/bin/X [0x52fee9]
5: /usr/bin/X [0x51d6ef]
6: /usr/bin/X(Dispatch+0x1db) [0x4514eb]
7: /usr/bin/X(main+0x45d) [0x439f4d]
8: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b6dd40e9b44]
9: /usr/bin/X(FontFileCompleteXLFD+0x231) [0x439249]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch



Relevent Sections of 
Xorg.conf

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "vbe"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
	Load  "dri"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	VendorName   "Samsung"
	ModelName    "Samsung SyncMaster 205BW (Digital)"
	HorizSync    31.4 - 80.0
	VertRefresh  56.0 - 75.0
	Gamma        1
	ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
EndSection

Section "Device"
	#Driver	    "vesa"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BoardName   "ati"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "TexturedVideoSync" "on"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "DesktopSetup" "horizontal"
	Option	    "HSync2" "30-121"
	Option	    "VRefresh2" "50-185"
	Option	    "PairModes" "1680x1050+1280x1024,1680x1050+1680x1050"
	Option	    "Mode2" "1800x1440"
	Option	    "EnableMonitor" "tmds1,crt2"
	Option	    "Capabilities" "0x00000800"
	Option	    "Textured2D" "on"
	Option	    "TexturedXrender" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
	#Option	    "MaxGARTSize" "512"
	BusID       "PCI:6:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "TexturedVideoSync" "on"
	Option	    "DAMAGE" "Enable"
	Option	    "RENDER" "Enable"
	Option	    "Composite" "Enable"
	Option	    "XVideo" "Enable"
EndSection

---

### Post by vaxius on 2008-03-05
I'm having almost the same problem with ATI's newest 8.45 driver with an x1400, but instead of crashing I just get a black desktop and black windows.  Restarting the machine fixes the problem temporarily, but it recurs after some random amount of time anywhere from half an hour to half a day when I'm lucky.  More info linked below (let's cut down on the ginormous posts).

[Here's my X log]("http://pastebin.vaxius.net/pastebin.php?show=5").

[Picture of blank desktop]("http://www.quickfilepost.com/download.do?get=0828c9704d9f6128a3eb5ac18499f781").

[Picture of blank window (Firefox)]("http://www.quickfilepost.com/download.do?get=fb823dd598909db2e32fdb49dd03d115").

[My xorg.conf]("http://pastebin.vaxius.net/pastebin.php?show=6").

---

