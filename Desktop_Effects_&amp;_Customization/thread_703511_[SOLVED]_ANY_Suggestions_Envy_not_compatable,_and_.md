---
title: "[SOLVED] ANY Suggestions: Envy not compatable, and Compiz has no decorations"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by crewe on 2008-02-21
To be as detailed as possible...
I have Xubuntu 7.10 (Gutsy)
with the most recent nvidia drivers installed (169.09)

To get this xorg.conf I took the three config's from the following commands and pieced together a new one, which so far has given me no issues. I also added the common > Option "AddARGBGLXVisuals" "True" since I was seeing it everywhere in my searches.

> 
sudo nvidia-xconfig
sudo dpkg-reconfigure -phigh xserver-xorg
nvidia-settings


xorg.conf:
```

Section "Files"
	RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option	   "Xinerama" "0"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7800 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"NoLogo" "True"
	Option		"AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"AL1716"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7800 GT]"
	Monitor		"AL1716"
	DefaultDepth	24
	Option		"TwinView" "1"
	Option		"TwinViewXineramaInfoOrder" "DFP-1"
	Option		"MetaModes" "DFP-0: nvidia-auto-select +1280+0, DFP-1: nvidia-auto-select +0+0"
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

I've recovered from a the system not loading correctly to pre compiz installation.
I've done
> 
sudo apt-get install compiz-core compiz-plugins compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald compizconfig-settings-manager


and I've also enabled the GPL'd Emerald themes in the manager.
I installed evny but whenever I tried it it says my system is incompatible.

when I run
> 
compiz --replace

all my window decorations disappear, all windows are brought to my current workspace and window focus is ruled by the cursor.

I've tried changing the window decorations option in ccsm but nether emerald or xfwm4 work.

I'm running the restricted driver for my video card and I've managed to get a white screen once, but how, I am unsure. but it only resulted in me having to do hard reboot because I could not see any UI. Only when I ALT+TAB did I see the icons of the available applications I had open.

I've been going steady at this for over a week now with no progress, ANY ideas, tips, would be great.

---

### Post by overdrank on 2008-02-21
HI and you may try and add
Option "AddARGBVisuals" "True"
In the device section and this add
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
at the end of the file.

---

### Post by crewe on 2008-02-21
still no dice

new xorg.conf
```

Section "Files"
	RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option	   "Xinerama" "0"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7800 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"NoLogo" "True"
	Option		"AddARGBGLXVisuals" "True"
	Option 		"AddARGBVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"AL1716"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7800 GT]"
	Monitor		"AL1716"
	DefaultDepth	24
	Option		"TwinView" "1"
	Option		"TwinViewXineramaInfoOrder" "DFP-1"
	Option		"MetaModes" "DFP-0: nvidia-auto-select +1280+0, DFP-1: nvidia-auto-select +0+0"
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
	Option 		"Composite" "Enable"
EndSection

```

direct rendering is enabled:
> 
glxinfo | grep direct
direct rendering: Yes


running from terminal I get:
```

compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0092 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 378: /usr/bin/metacity: not found

```

---

### Post by crewe on 2008-02-21
So I just tried to install the nvidia-gls and nvthen the nvidia-glx-new and it right messed up my settings, I'm now running in "Low Graphics Mode so I have to reinstall the nvidia drivers now.

---

### Post by crewe on 2008-02-21
:KS PROGRESS! :KS

I just ran compiz --replace from terminal and I got the xfwm4 window decorations. But because it was in the term I had to close it and try from the run command box, but I can't get it to open, and since closing the terminal I lost decorations again, but at least I saw it work once. But no compiz plugins were working...

---

### Post by crewe on 2008-02-21
okay I got it working now, I set up an extra panel so that I can easily switch from compiz to xfwm4 but it seem to just say in compiz or non-working mode without decorations.
But that will come with time... I hope :P

Thanks a bunch overdrank, I think that's what did it, and also thanks to cookieofdoom in #ubuntuforums

---

