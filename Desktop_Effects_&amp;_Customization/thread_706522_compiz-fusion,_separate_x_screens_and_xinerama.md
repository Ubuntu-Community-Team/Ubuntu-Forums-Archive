---
title: "compiz-fusion, separate x screens and xinerama"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by Woody1987 on 2008-02-24
Hi, i want to enable compiz-fusion effects with xinerama and after searchng the internet i have found nothing. what i currently have is:

[LIST]
[*]Ubuntu gutsy 64
[*]Nvidia driver 169.09
[*]dual monitors, 1680x1050 and 1280x1024
[*]xinerama enabled with seperate x-screens
[/LIST]

Currently i have what i want but without compiz-fusion, hence the reason for the thread.

I do not want to use twinview as i play games with wine and they stretch across both monitors. I have tried messing with the meta-modes so that one monitor switches off when a full screen application runs but i dont want this, i want to be able to see both screens when playing a full screen game, just like in windows.

when i run compiz--replace or simply compiz i get the following error

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0191 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2960x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/home/matthew/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matthew/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matthew/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/bin/compiz.real (core) - Fatal: No valid GL extensions string found.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/matthew/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/matthew/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/matthew/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

I assume the problem is not having Xgl installed (whatever that is).

Included is my xorg.conf

---

### Post by aden_87 on 2008-03-07
I have the same problem, but i'm runnig nvidia 169.12 in gutzy...

XGL is some typ of opengl thingy that runns under gnome.. and makes al things on the screen render in 3d..

I've installed it via the package manager. but when restart of x server i get only whote screens... 

Don't know what to do... 

PM me if you find a solution..

Have a nice day

---

### Post by tchiseen on 2008-03-15
I'm having the same problem

I've installed 8.04 Alpha 6
I've got 2 x 1280x1024 monitors on a nvid 7900gs with the nvid drivers. I have xinerama on, two x screens, and this is what I get from trying to run 'compiz'

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0292 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Let us know if there's a fix!

---

### Post by sgfaulkner on 2008-03-18
I am having the exact same issues.  I have been working through all different combinations the last few days and can't get anything to work with compiz.  If I Install xserver-xgl then compiz works, but then xinerama stops working correctly, the windows don't respect their monitors and compiz thinks its just one HUGE screen

---

### Post by dokdoom on 2008-03-18
I'm having the same problem too. I've followed all the guides and nothing seems to work. Here's the output from compiz --replace

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:040c (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (3840x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
Segmentation fault (core dumped)
exec: 378: /usr/bin/metacity: not found

I've seen this out all night and no matter how I search or where I search I come up with nothing.

---

### Post by IsawSp4rks on 2008-03-18
Compiz and Nvidia's Xinerama 3D are not compatible because Xinerama disables DRI, which Compiz needs.

That's what I've worked out so far.

---

### Post by aden_87 on 2008-03-19
Some how i manage to get my xorg to work as if it was in xinerama configuration. But it is in twinvie. I dont know how, and for me the only probelm with twinview is that xorg mange the screens as one screen but not now.

this is how my xorg.conf looks like now.

If some one could point out what makes xorg manage the screens like two screens and not one this may help some users.

[HTML]# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:53 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL P1110"
    HorizSync       30.0 - 121.0
    VertRefresh     48.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL P1110"
    HorizSync       30.0 - 121.0
    VertRefresh     48.0 - 160.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8500 GT]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8500 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
# Removed Option "metamodes" "CRT: 1600x1200 +0+0, DFP: nvidia-auto-select +1600+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: nvidia-auto-select +1280+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection
[/HTML]

here is two links  to printscreens of compiz on two sperate screens. The last one is a pic of the cube. 

[http://cadeen.byethost13.com/wp-content/uploads/2008/03/skarmbild-1.png]("http://cadeen.byethost13.com/wp-content/uploads/2008/03/skarmbild-1.png")
[http://cadeen.byethost13.com/wp-content/uploads/2008/03/skarmbild.png]("http://cadeen.byethost13.com/wp-content/uploads/2008/03/skarmbild.png")

If I have not missunderstod the whole xinerama thing this will hopefully help some of you

---

### Post by surfed on 2008-03-21
> **IsawSp4rks said:**
> Compiz and Nvidia's Xinerama 3D are not compatible because Xinerama disables DRI, which Compiz needs.

That's what I've worked out so far.


not according to my xorg log:


X.Org XInput driver : 2.0
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so

Xinerama is enabled and working but Compiz complains about composite not being available but in my logs i see that is is loaded:

(**) Extension "Composite" is enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is....


so I have Composite, DRI, Xinerama RenderAccel but NO Compiz on Hardy.

---

### Post by boluc91 on 2008-03-21
Hi all

EDIT : missed earlier post that suggested twinview....

I have a dual screen (1440x900 + 1600x1200) on a nvidia card with compiz enabled.
However i dont use xinerama i use twinview.
Twinview only works with nvidia cards and the monitors have to be on  the same card.
But its way faster than xinerama and i found it easier to get compiz to work with twinview.

video part of my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "TwinviewScreen" 0 0

    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "CRTMonitor"
    VendorName     "Unknown"
    ModelName      "MED"
    HorizSync       30.0 - 98.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
EndSection

Section "Screen"
    Identifier     "TwinviewScreen"
    Device         "Videocard0"
    Monitor        "CRTMonitor"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"#whats the first screen
  Option         "metamodes" "CRT: 1280x960 +1440+0, DFP: 1440x900 +0+0;DFP: 1440x900;CRT: 1600x1200 +0+0;CRT: 1152x864 +1440+18,DFP: 1440x900 +0+0; CRT: 1024x768 +1440+66,DFP: 1440x900 +0+0" #specifies all the possible resolutions
#just google for an explanation of the syntax
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
	Option "Composite" #compiz needs this
EndSection




```


Hope this helps : )

Good luck, greetings Bob


EDIT2:
Woody i tried fixing your xorg it uses twinview instead of xinerama now:
Everything i changed is commented in caps.

I hope it works

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:27:25 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    #Screen      1  "Screen1" RightOf "Screen0"#REMOVED
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option         "AIGLX" "true"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dbe"
    Load 	   "Xgl
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0" # SET TO 0
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "uk"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hitachi X220W D-sub"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP vs19"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-1: 1680x1050 +0+0"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option	   "DRI" "True"
    Option         "XAANoOffscreenPixmaps" "true"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"#TWINVIEW ON
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1680x1050 +0+0, CRT-1: nvidia-auto-select +1680+0"#ADDED SECOND SCREEN
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option	   "DRI" "True"
    Option         "XAANoOffscreenPixmaps" "true"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by IntuitiveNipple on 2008-03-28
> **aden_87 said:**
> Some how i manage to get my xorg to work as if it was in xinerama configuration. But it is in twinview. I dont know how, and for me the only probelm with twinview is that xorg mange the screens as one screen but not now.

Aden, thanks!

I was having the same issue as everyone else and I think I found the key to your configuration. I've not tested all permutations of the options I identified so some might be unnecessary, but here's what I noticed.

It does start two separate X sessions so although you can move the mouse between them, you can't drag windows from one to the other. Also, the secondary screen has its own set of menus.

[LIST]
[*]Device sections don't both have "screen X" parameter
[*]Screen 1 has TwinView enabled, Screen 0 doesn't
[/LIST]

This is the xorg.conf I'm using. I'll experiment with the options and report back if I make any more progress (like the 2nd screen not having its own menus).
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was hand-crafted by TJ

Section "ServerLayout"
	Identifier	"Dual-screen Layout"
	screen 0 "Default Screen" 0 0
	screen 1 "Second Screen" leftof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"false"
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection

Section "Files"
	Rgbpath		"/usr/lib/X11/rgb"
EndSection

Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"	"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia G70 [GeForce Go 7600] 0"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce Go 7600"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"NvAGP"	"1"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"AllowGLXWithComposite" "True"
	Option		"NoLogo"	"True"
#	Screen	0
EndSection

Section "Device"
	Identifier	"nVidia G70 [GeForce Go 7600] 1"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce Go 7600"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"NvAGP"	"1"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"AllowGLXWithComposite" "True"
	Screen	1
EndSection

Section "Monitor"
	Identifier	"Internal-DFP"
	Vendorname	"Sony Vaio VGN-FE41Z DFP"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5	-	50.0
	Vertrefresh	56.0	-	65.0
	Gamma	1
	Option		"DPMS"
  modeline  "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Monitor"
	Identifier	"External-Analogue-VGA"
	Vendorname	"Samsung XIOD 19"
	Modelname	"XIOD-19"
	Horizsync	31.5	-	64.0
	Vertrefresh	56.0	-	65.0
	Gamma	1
	Option		"DPMS"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia G70 [GeForce Go 7600] 0"
	Monitor		"Internal-DFP"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"nvidia-auto-select +0+0"
	Option		"metamodes" "DFP: 1280x800 +0+0, CRT: 1280x1024 +1280+0"
	SubSection "Display"
		Depth	24
		Modes		"1280x800@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"nVidia G70 [GeForce Go 7600] 1"
	Monitor		"External-Analogue-VGA"
	Defaultdepth	24
	Option		"TwinView"	"1"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

```

---

### Post by surfed on 2008-03-28
i got mine working with nvidia-settings, two x screens no xinerama, one set of taskbars and i can drag windows across the screens and compiz works fine:

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
    Load           "dbe"
    Load           "extmod"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "freetype"
    Load           "bitmap"
    Load           "dri"
    Load           "Xgl"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "vmmouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL E228WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "false"
EndSection
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5900 Ultra"
    Option         "RenderAccel" "true"
    Option         "CursorShadow" "true"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5900 Ultra"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "Xinerama" "1"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DRI" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DRI" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "true"
EndSection




---

### Post by CrazyC on 2008-03-28
My experiences with dual screens and compiz say that you can make everything work if both monitors are plugged into the same card.
You can use either Twinview for nvidia's custom xinerama like display (it's not really xinerama but works the same way) or you can have 2 separate xsessions (can't drag windows and apps between displays, but you can move the mouse between them).

I have yet to get compiz to work on 2 monitors on 2 separate display cards.  Twinview in not an option across 2 cards, as it only works for 2 monitors on 1 card.  Xinerama does definitely disable xgl and/or aiglx which does not allow compiz to run.
And for whatever reason, I have been unable to get compiz to run even with a separate xsession set for each monitor on separate cards.


For any of the setups that I have gotten working, I have only had to use nvidia-settings program to configure my xorg.conf file.
I have tried every custom option possible by manually editing xorg.conf though and have not gotten any different results.

My current xorg.conf looks almost identical to what surfed posted, but I removed the unused sections for the default config.  Unfortunately, I have gotten so used to use compiz and kxdocker that I have resorted to leaving one card just sitting idle in my machine until this stuff gets worked out so that I can use xinerama or a similar display with compiz.

---

### Post by mattchew on 2008-03-30
Please keep up with this!

/watches thread

I've got an 8600GT running compiz, but I am unable to separate as you are seeking. If someone can point me to what directory my xorg config is in I will test this stuff and report back as well.

Currently viewing where it's sharing the screens as a single display which i not what I want.

---

### Post by surfed on 2008-03-30
> **mattchew said:**
> Please keep up with this!

/watches thread

I've got an 8600GT running compiz, but I am unable to separate as you are seeking. If someone can point me to what directory my xorg config is in I will test this stuff and report back as well.

Currently viewing where it's sharing the screens i not what I want.

config is:

/etc/X11/xorg.conf

also try playing with nvidia-settings as this if run as root can merge changes to your config.

---

### Post by mattchew on 2008-03-30
When I run Nvidia settings, I get the following message:
```

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

I installed the XGL stuff and restarted with compiz--replace and this is where I am at right now.

Both screens are merged....so if I maximize a window it goes cross both displays at the moment.

Attaching Xorg.config (since its a lot of text)...also there was an xorg 1 and xorg 2, which I don't know if they were significant or not so I attached em.

---

### Post by surfed on 2008-03-30
Ok, you have to restart X for changes in xorg.conf to take effect (log out and press ctrl+alt+backspace)
Make sure nvidia-glx is installed.

---

### Post by mattchew on 2008-03-30
I've done that a ton but the screens are treated as one big screen. Is there some kind of output thing I should have that will help in figuring it out?

edit: I can be found on aim/yahoo if you wish to discuss (or shoot me an IRC server to go to)

---

### Post by CrazyC on 2008-03-30
mattchew, are you running 32bit or 64bit ubuntu?  And which release of (K)Ubuntu are you running?

I ask because it looks to me like you need to get the nvidia drivers working correctly first, based on that error message you got when trying to run nvidia-settings.

Also, you do NOT want XGL installed.  The nvidia drivers take care of that automatically by including aiglx if using any of the 169.xx series of drivers.

---

### Post by mattchew on 2008-03-30
> **CrazyC said:**
> mattchew, are you running 32bit or 64bit ubuntu?  And which release of (K)Ubuntu are you running?

I ask because it looks to me like you need to get the nvidia drivers working correctly first, based on that error message you got when trying to run nvidia-settings.

Also, you do NOT want XGL installed.  The nvidia drivers take care of that automatically by including aiglx if using any of the 169.xx series of drivers.



Ubuntu 32 bit on 7.10 gutsy

I couldn't get compiz to run without XGL, I'd get an error if I tried to run compiz like that...some kind of display error...let me copy from another thread. I was using the latest binary, I presumed.

The error was 'RenderBadPicture (invalid Picture parameter)'.

---

### Post by CrazyC on 2008-03-30
So did you use the restricted driver manager to install the binary nvidia drivers or did you download the latest driver installer from nvidia and install that way?

I haven't used the restricted driver manager in probably 6 months, so I don't know which version of the drivers are installed via that method.  Installing with the nvidia installer is REALLY simple these days and is probably the better choice as you will get all the latest bug fixes by using the latest release direct from nvidia.

First, you need to get your system cleaned up a bit though, which means you need to undo the xgl installation that you did.

Then, I would recommend following this howto:  [NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

That will get you up and running with the latest 169.12 driver.

From there, we can work on your xorg.conf configuration so that compiz will work for separate xssesions.

[edit]I'll be around tonight for another hour or two, so I will watch this thread if you need help with any steps.  I can try to walk you through problems, but can't guarantee that I'll have an answer for everything. ;)  [/edit]

---

### Post by mattchew on 2008-03-30
how do I kill XServer to replace the nvidia drivers?

---

### Post by CrazyC on 2008-03-30
Logout of X.

When you get back to the splash/login screen, press ctrl-alt-F1 to get to a terminal.

Login with your username and password.

Then type:  sudo /etc/init.d/gdm stop

At that point, then navigate to the folder where you downloaded the nvidia installer and continue the steps on the guide.  Be sure to either print the guide, make notes or steps or have another computer available so you can still read the steps in the guide.

---

### Post by mattchew on 2008-03-30
So, step one done. Did what you suggested, it compiled a new x server, etc it seems. I think it actually set me up on X again! When I try to run that twinview settings thing it says: 
```

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

```

Of course I've done that a million times, but it still does it.

Restricted device manager shows enabled, and here's some of the info screenshots I can gather.

The display is currently set lower, looks like I have to get display drivers right or something? (currently showing 1024x768 cloned on both displays, not anywhere near what I want) 

Where do we begin with the Xorg editing? :P

---

### Post by CrazyC on 2008-03-31
Did you specifically follow this step of the howto?

> Disable Conflicting Software

Using Synaptic or Apt, uninstall nvidia-glx, nvidia-glx-legacy, nvidia-glx-new and nvidia-settings if they are installed.

Open the the /etc/default/linux-restricted-modules-common file with an editor, in Ubuntu use

```

gksudo gedit /etc/default/linux-restricted-modules-common
```



If you did definitely do that..

If you press:  alt-F2    and then run    nvidia-settings
What happens?
You should get the nvidia setings app.  It is also available in your menu somewhere, probably under System, if that's what the menu section is in gnome.

I'm not very familiar with gnome as I haven't used in a long time, I run KDE.

If nvidia settings actually opens, click on the first item on the left, which is "X Server Information".

It should tell you what driver version you are running.

---

### Post by mattchew on 2008-03-31
Update:

Through some manner of toggling, printing crap out, etc, I was able to boot and login.

Restricted Devices manager shows the nvidia driver Enabled but not in use.

When I try to open the twinview thing it says xserver not installed.

I was only able to do this by going through DISABLED_MODULES="nv" and adding in nv. Only at that point would the option of "nvidia" come up with the display manager...if I choose NV and go to test - it shows both displays in the test example. If I choose Nvidia and go to test...it doesn't end well...either way if I hit apply settings are not saved.

This is only with Nvidia-glx-New installed and no nvidia-glx or legacy, and with nvidia-settings installed as well.

When I try to run that package off Nvidia's website it now says I have the latest version.

So where do I go from here to enable the split screens and set up so that the bars are on separate screens (along with compiz)?

---

### Post by CrazyC on 2008-03-31
ok... first step would be to use nvidia-settings to get your displays configured the way you want them arranged.  The last thing will be compiz.

so press alt-f2 and enter gksudo nvidia-settings

 Then use the "X Server Display Configuration" to setup your displays with the right resolution and layout.

When you click on one of the boxes at the top, the dropdown list below should display the current monitor (if properly detected), the current port (dfp or crt)  and the current gpu.

Click the configure button and set each to be a separate X screen.
Set the resolution for each montor
I recommend leaving the frequency on auto unless you know how to set it right for your monitor(s)
Set the position for 1 monitor as absolute and then set the other to either left or or right of.
save x config

also while in the nvidia-settings, got to "X Server XVideo Settings" and "OpenGL Settings" and uncheck the boxes for "Sync to Vblank".  I have read a bunch of messages stating that people have had better success with those unchecked.  If after getting things working and you want to play, then go back and check those one at a time to see how it affects compiz.

When finished with nvidia-settings, click on Quit, select yes to really quite.
Now restart X, by logging out and then pressing ctrl-alt-backspace

log back in and see what your displays look like.  They SHOULD be set the way you want them for layout with separate X sessions on each screen, including each have it's own panel.

If the layout is not correct go back to nvidia-settings and adjust until you get them in the right place.  Depending on how your cards are installed and how the driver detects them, you may get them backwards at first.  Nothing a little testing and adjusting can't correct.

VERY IMPORTANT!  (at least from my experience)  Do NOT use any of the gnome (or kde for kubuntu) settings for configuring displays with the 169.xx nvidia series drivers.  At least not in gutsy.  ONLY use nvidia-settings.

---

### Post by CrazyC on 2008-03-31
Once you get that far, post your xorg.conf file so I (or anyone else on here) can direct you in the right path to get it setup for compiz to work with the separate x-sessions.

2 people on the first page of this thread have it working and have posted their xorg.conf files, but yours MAY NOT be identical, based on your hardware.  So you can't just copy everything from the other files.  And the nvidia-xconfig program will not set twinview on one display, but not the other like they have setup, so you have to do it manually.

---

### Post by mattchew on 2008-03-31
Update

Ran Envy thing, dual monitors are working properly again but as to be expected, compiz is not. So lets start from here.

1: Latest nvidia driver

Twinview (nvidia-settings) shows: Xinerama enabled, and configures each display device with the option "Separate X Screen"

2: Compiz gives me this error with xine running(as well on --replace)  
```

designerfx@designerfx-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3120x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 342 error_code 178 request_code 156 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
/usr/bin/compiz.real (core) - Fatal: No valid GL extensions string found.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

WITH TWINVIEW/NO XINE = compiz runs fine (cept that I lose my window bar for maximize/minimize for some reason)


Current Xorg.conf is as follows:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "Screen0" rightof "Screen1"
  screen 1 "Screen1" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	
	# Removed Option "Xinerama" "1"
	# Removed Option "Xinerama" "0"
	Option		"Xinerama"	"1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	84.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Vendorname	"Unknown"
	Modelname	"Niko-1906W"
	Horizsync	30.0	-	83.0
	Vertrefresh	50.0	-	76.0
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"CMO"
	Horizsync	30.0	-	75.0
	Vertrefresh	60.0
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 8600M GT"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection

Section "Device"
	Identifier	"Videocard1"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 8600M GT"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1680"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Screen"
	
	# Removed Option "metamodes" "DFP-1: 1440x900 +0+0"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"DFP-1: nvidia-auto-select +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"DFP-0: nvidia-auto-select +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by CrazyC on 2008-04-02
As I posted originally (my first post in this thread)...

Compiz will NOT work if Xinerama is turned on/enabled.  Xinerama DISABLES the composite extension and therefore compiz won't run.
So to begin with, you need to change the xinerama setting to 0 instead of the 1 that you currently have.

From reading your messages, I'm to understand that you DO want 2 SEPERATE x sessions on your screens and that you do NOT want one large screen, right?

If so, the only way that it appears to work is if you set the twinview option for VIDEOCARD0 to:
Option		"TwinView"	"1"

And then set VIDEOCARD1 to:
Option		"TwinView"	"0"

Hopefully that's going to work for you.  If by chance it doesn't go the the first page in this thread and compare your videocard options to the 2 people that did get it working.  And see what you come up with.

If I mis-interpreted what you want and you really do want 1 large desktop between both screens, then you need to set twinview to 1 for BOTH cards.

For either layout, if your screen positions are not the way you want, run nvidia-settings as root and use the X Server Configuration to adjust the screen locations.

Compiz will DEFINITELY work with twinview enabled on both cards.  There are a lot of people that have that working correctly.  Running 2 separate xsessions has been hit or miss for a lot of people.  I do not have my xorg.conf file from when I did have that working, so the only thing I can go by there is what was posted in this thread and it appears to be working for a couple of people, so that should be a good guide for your xorg.conf file.

I'm glad to hear that you have the nvidia driver working and with any luck you'll get compiz to work correctly for you now too.

---

### Post by mattchew on 2008-04-02
> **CrazyC said:**
> As I posted originally (my first post in this thread)...

Compiz will NOT work if Xinerama is turned on/enabled.  Xinerama DISABLES the composite extension and therefore compiz won't run.
So to begin with, you need to change the xinerama setting to 0 instead of the 1 that you currently have.

From reading your messages, I'm to understand that you DO want 2 SEPERATE x sessions on your screens and that you do NOT want one large screen, right?

If so, the only way that it appears to work is if you set the twinview option for VIDEOCARD0 to:
Option		"TwinView"	"1"

And then set VIDEOCARD1 to:
Option		"TwinView"	"0"

Hopefully that's going to work for you.  If by chance it doesn't go the the first page in this thread and compare your videocard options to the 2 people that did get it working.  And see what you come up with.

If I mis-interpreted what you want and you really do want 1 large desktop between both screens, then you need to set twinview to 1 for BOTH cards.

For either layout, if your screen positions are not the way you want, run nvidia-settings as root and use the X Server Configuration to adjust the screen locations.

Compiz will DEFINITELY work with twinview enabled on both cards.  There are a lot of people that have that working correctly.  Running 2 separate xsessions has been hit or miss for a lot of people.  I do not have my xorg.conf file from when I did have that working, so the only thing I can go by there is what was posted in this thread and it appears to be working for a couple of people, so that should be a good guide for your xorg.conf file.

I'm glad to hear that you have the nvidia driver working and with any luck you'll get compiz to work correctly for you now too.

I'm good now.

Twinview + Compiz + Emerald. Simpler night than anything I've seen so far.

Also discovered filelight. Quite an impressive little program, reminds me of spacemonger, which I discovered from Hiren's BootCD.

So thank you, maybe the OP wants to mark the thread solved.


edit: all I have left is to figure up a smooth recording program to get one of my screens for showcasing (or both)...but definitely seems like 3100x900 is not easy for any processor, even an E6700 with an 8600M GT for sure.

---

### Post by chacham23 on 2008-05-05
> **CrazyC said:**
> ok... first step would be to use nvidia-settings to get your displays configured the way you want them arranged.  The last thing will be compiz.

so press alt-f2 and enter gksudo nvidia-settings

 Then use the "X Server Display Configuration" to setup your displays with the right resolution and layout.

When you click on one of the boxes at the top, the dropdown list below should display the current monitor (if properly detected), the current port (dfp or crt)  and the current gpu.

Click the configure button and set each to be a separate X screen.
Set the resolution for each montor
I recommend leaving the frequency on auto unless you know how to set it right for your monitor(s)
Set the position for 1 monitor as absolute and then set the other to either left or or right of.
save x config

also while in the nvidia-settings, got to "X Server XVideo Settings" and "OpenGL Settings" and uncheck the boxes for "Sync to Vblank".  I have read a bunch of messages stating that people have had better success with those unchecked.  If after getting things working and you want to play, then go back and check those one at a time to see how it affects compiz.

When finished with nvidia-settings, click on Quit, select yes to really quite.
Now restart X, by logging out and then pressing ctrl-alt-backspace

log back in and see what your displays look like.  They SHOULD be set the way you want them for layout with separate X sessions on each screen, including each have it's own panel.

If the layout is not correct go back to nvidia-settings and adjust until you get them in the right place.  Depending on how your cards are installed and how the driver detects them, you may get them backwards at first.  Nothing a little testing and adjusting can't correct.

VERY IMPORTANT!  (at least from my experience)  Do NOT use any of the gnome (or kde for kubuntu) settings for configuring displays with the 169.xx nvidia series drivers.  At least not in gutsy.  ONLY use nvidia-settings.

thanks worked for me :)

---

