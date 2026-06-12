---
title: "Resolution limited, although xorg.conf lists plenty"
date: 2007-01-08
forum: Desktop Environments
---

### Post by kombucha on 2007-01-08
I turned on my computer today and for whatever reason it was running at a resolution of 800x600, refresh rate of 60 hz. What it should be (and was, as of yesterday) running at is 1024x768, 70 hz. Here's my xorg.conf:
> ...Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


The first thing I tried was going to ATI's site (I am using a Radeon 9000) and downloading the xorg driver - but when I run ATI Control I get "Driver does not provide the FireGL X11 extensions! Panel components will operate only partially" and then no choices within the panel.

Then I tried changing the driver in "Monitor and Display" settings, I think I tried "ATI Radeon". Rebooted, X wouldn't start (greeeeat). So restored a previous version of xorg.conf, then my wacom wouldn't work - anyways, after about an hour, found a backup of xorg.conf that let me boot into X with a working wacom.

Thirdly I tried setting the default depth as 16... and for reasons I may never understand, that alone killed my wacom, so again I restored from a backup.

I'm getting nervous, so I'll wait for help from people who actually know what they are doing. Right now, the driver listed is "ati". 800x600 is, of course, the max resolution allowed, as is 60 hz. My monitor is on its final throes, and as such is very distorted when not at 1024x768 and somewhere near 72hz, so this is very hard to work with.

I'm open to any and all ideas.

Thanks!

:)

Oh yeah, in case it matters, xrandr produces:
 > SZ:    Pixels          Physical       Refresh
*0    800 x 600    ( 271mm x 203mm )  *60   56  
 1    640 x 480    ( 271mm x 203mm )   60  
 2    400 x 300    ( 271mm x 203mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none


---

### Post by capitalistpiglet on 2007-01-08
the problem is it hasnt detected your monitors vertical refresh and horizontal sync rate.
You should be able to find these by googling around.
Once you have them just edit xorg.conf file monitor section and add these lines (obviously with your monitors rates instead of these).
[CODE]
HorizSync	30-75
VertRefresh	50-85
[CODE]

And remember to make a backup of the xorg.conf file before you edit it incase you screw up.

---

### Post by kombucha on 2007-01-08
Thanks, I found:

Horizontal: 30-70kHz 
 Vertical: 50-130Hz 

without too much trouble - I'll try that and see what happens. Any idea why it worked initially and stopped from yesterday to today? I'm just curious.

---

### Post by kombucha on 2007-01-08
Finally got a restart in, your solution worked perfectly.
Thanks for the support, glad it was a fairly simple issue.

---

