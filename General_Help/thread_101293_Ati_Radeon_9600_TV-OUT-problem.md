---
title: "Ati Radeon 9600 TV-OUT-problem"
date: 2005-12-09
forum: General Help
---

### Post by _jane_ on 2005-12-09
I have installed the drivers and they are working just fine but I get no TV-out-signal. 
Here is what fglrxinfo is saying
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

The only problem I seem to have is that I don´t really know where to turn the tv-display on. everything is plugged and the tv is on on the right channel. 
the xorg.conf-file:
# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)"
    Option "HSync2"                     "unspecified"
    Option "VRefresh2"                  "unspecified"
    Option "ScreenOverlap"              "0"
# === TV-out Management ===
    Option "OverlayOnCRTC2"
    Option "NoTv"                       "No"
    Option "TVFormat"                   "PAL-B"
    Option "TVStandard"                 "PAL-M"
    Option "TVHSizeAdj"                 "0"
    Option "TVVSizeAdj"                 "0"
    Option "TVHPosAdj"                  "0"
    Option "TVVPosAdj"                  "0"
    Option "TVHStartAdj"                "0"
    Option "TVColorAdj"                 "0"
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x06419064"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"

can anyone help me with this problem?

---

### Post by kb3hkg on 2005-12-09
I cannot help you unfortunately, however I have the same problem...sort of.  I have a ATI Radeon Mobility 9700 which is detected as a 9600. This happens to me in every distro I have tried. And in every distro the tv-out has not worked.

---

### Post by manzuk on 2005-12-09
Ok, I'm a newbie so I don't know if I can help you; all I can tell you is my story.

I've got an ATI Radeon 9600xt from MSI (using DVI and super video output for tv)
I've installed the ati drivers from the repositories (along with all the restricted modules  needed). Firstly I tried to manually change my xorg.conf to use fglrx instead of ati (as driver), but it didn't work. So I finally decided to let fglrxconfig create a new xorg.conf. I answered all the "questions" including TVout related, and the next time Xorg started, not only 3d acc worked, but also TV out!!! Kind of magic right :p ?
What's weird is that without using fglrxconfig, there wasn't 3d acc... (although I had followed almost EVERY howTo found in the web)

Well, just in case, this is what fglrxinfo says:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

Hope you find a solution. Love kubuntu! bye

---

### Post by kb3hkg on 2005-12-09
Would you mind giving us a step by step for what you did exactly. It is easier for others to follow that way.

---

### Post by manzuk on 2005-12-11
Install from repositories:
[LIST]
[*]xorg-driver-fglrx 
[*]fglrx-control 
[*]linux-restricted-modules-amd64-k8
[*]linux-image-amd64-k8
[/LIST]

Then I followed many howTos, which said I had to:

** Edit /etc/X11/xorg.conf (as root)
** Change where it says

```
Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "[COLOR="Red"]ati[/COLOR]"
```

ati to fglrx, so that it looks

```
Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "[COLOR="Red"]fglrx[/COLOR]"
```

** Restart X, and if doesnt work, reboot computer.

Well, I tried these steps MANY times, but it didn work. So I resigned to use standar ati drivers with neither 3D nor tvout.
But one day, while updating kubuntu (about 2weeks ago), i got a new kernel, dont remember its number :???: I tried then all the howtos again, without success.

So I used **[COLOR="Red"]FGLRXCONFIG[/COLOR]**, an app that comes with fglrx drivers and auto-generates a xorg.conf. I'd never used it before because all the howtos told me not to.
I anwered all the questions (even those related to TVout), restarted X, and 3D acc and TVout worked with no problem!!! So my (newbie) tip is: backup your current xorg.conf and then RUN FGLRXINFO. Hope this helps. Bye
Love kubuntu! :p

---

### Post by kb3hkg on 2005-12-14
Is it only the one xorg.conf file I need to worry about? Because there are a few on my system.

---

### Post by kb3hkg on 2005-12-14
Ok, so tv out is working, haven't tested 3d yet. The automated program didn't work, but doing it myself did but with problems. I want the tv to be a seperate desktop not a clone, and my normal monitors resolution was changed and I can't get it back. How do I fix this?

---

### Post by kb3hkg on 2005-12-15
Sorry for multiple posts in a row but I got it working, thank you very much for the help. I redid the automatic program and altered its xorg.conf file slightly to get my native resolution back. and now all seems to be working.

---

### Post by redgilda on 2005-12-17
I have a question that keeps bugging me and I can't find an answer to it anywhere... **is there a way to quickly switch between the TV out and the monitor??** I finally managed to get the tv out to work (ATI Radeon 9200). but well, I was wondering if there is a way to have it either on the pc OR on the tv.. not at the same time on both. or at least to turn the tv out off when I dont want it. on win xp I was able to do it fast with a keyboard shortcut, but I have no idea if it's possible on ubuntu... maybe it's something so obvious, but well.. I'm new to linux at all, so Id appreciate any info.....

heres my xorg.conf file in case someone is interested ;-) Id appreciate also any advice on how to modify it maybe if necessary? I have a feeling that when others post their files, they are much longer......... ;-) ```
 # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"PL"
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
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107T"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor		"PHILIPS 107T"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Ocxic on 2005-12-17
the ATI video cards also REQUIRES a restart with the video-out cable connected in order for it to properly work. otherwise the card never initializes the display, so a ctrl-alt-backspace restart of gnome won't work. just thought I;d let you now, it's what has worked for me, i have a 9600. also I have a problem of my monitor screen going super bright, like the gamma is turned way up, when the video out is connected and working.  
if anyone has the same problem/figures out how to fix it please PM me I'll alos be cheking back to this forum.

---

### Post by mirak63 on 2006-12-17
you can force tv out to be enabled or monitor 

        Option      "ForceMonitors" "crt1,tv"

---

