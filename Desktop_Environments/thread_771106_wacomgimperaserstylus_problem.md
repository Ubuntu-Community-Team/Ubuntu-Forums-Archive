---
title: "wacom/gimp/eraser/stylus problem"
date: 2008-04-27
forum: Desktop Environments
---

### Post by alcoholdeficit on 2008-04-27
I upgraded to 8.04 the other day and now my wacom wont work correctly in gimp.  As far as mouse tracking goes it works correctly.  im currently using my old xconf settings from 7.10 that worked perfectly well.  the extended devices appear in gimp and are on but i don't get separate eraser, stylus settings.  all my devices are recognized as core pointer inputs.  when i look at device statuses all my pointer ever is is a core pointer even though eraser, stylus, pad etc are all usable devices. any help? i've tried reinstalled the driver double checked my settings i just cant figure it out.

---

### Post by alcoholdeficit on 2008-04-27
Section "Files"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option "Buttons" "8"
	Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"	"On"		# Tabl
	Option        "PressCurve"    "0, 5, 95, 100"
	Option		"Speed"	"3.0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"	"On"		# Tabl
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"	"On"		# Tabl
EndSection
Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"pad"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"L227W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"L227W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

---

### Post by alcoholdeficit on 2008-04-27
i have an intuos3.  i tried to completely remove the wacomtools and xorg driver then restart and reinstall and still no avail.  i get the most basic tablet functionality itself but no eraser end.  I really dont get why its not working.  its like all devices are the main pointing device even though it recognizes the others.

---

### Post by alcoholdeficit on 2008-04-27
and one more note, when i do a wacdump it finds the device but nothing updates on the screen.i can still move with the stylus, just nothing on the wacdump moves.

---

### Post by alcoholdeficit on 2008-04-27
a few lines from my xorg log:


(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "8"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 12
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "On"
(**) stylus: reading USB link
(**) WACOM: PressCurve 0,5,95,100
(**) Option "BaudRate" "9600"
(**) Option "Speed" "3.0"
(**) stylus: speed = 3.000
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "On"
(**) cursor: reading USB link
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "On"
(**) eraser: reading USB link
(**) Option "BaudRate" "9600"
(**) pad: always reports core events
(**) pad device is /dev/input/wacom
(**) pad is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "On"
(**) pad: reading USB link
(**) Option "BaudRate" "9600"
(II) evaluating device (pad)
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
pad Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom USB Intuos3 tablet speed=9600 maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080  tilt=enabled
(==) Wacom device "pad" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=40640 bottom Y=30480
(II) Configured Mouse: ps2EnableDataReporting: succeeded


i see no errors anywhere here.

---

### Post by alcoholdeficit on 2008-04-28
anyone? this tablet is pretty important to me.  it's about 90% of my computer usage.

---

### Post by bigdee973 on 2008-05-18
well dude for u in particular, what i reccommend you do is first reconfigure the xorg.conf file and start from scratch again.  Open up a terminal and type sudo dpkg-reconfigure -phigh xserver-xorg this will reconfigure your xorg.conf and may resolve any issues you may have floating around your xorg.conf file im certain if u do this will help u get ur wacom to work.  just follow the instructions on the screen.   after u done that follow the instructions below... these instructions also work for anybody who hasnt installed or configured anything yet for there wacom tablets and would love to do so..should work for Gusty and Hardy if reconfiguring your xorg.conf doesnt work than im not too sure whats the problem then.  but..

_**STEP 1:**_ 
open terminal and type: 

sudo apt-get install wacom-tools

then

**_STEP 2:_**
sudo gedit /etc/X11/xorg.conf

1)  i have pasted and copied my xorg.conf down below...every xorg.conf is different in every PC but all that matters for wacom tablet to work is that u put the right code in the right SECTION. although we all have different setups in our xorg we do have the same SECTIONS" AS FOLLOW...notice [COLOR="SeaGreen"]Section "serverlayout[/COLOR]" in green...what u have to do here is copy and paste the red highlighted code  into the section just above [COLOR="SeaGreen"]identifer "default layout"[/COLOR]

2)  now scroll down and look for [COLOR="Purple"]Section "Input Device[/COLOR]". You have two of them..one is keyboard and one is mouse. Copy and paste blue hightlighted code underneath the [COLOR="SandyBrown"]endsecton[/COLOR] of the LAST [COLOR="Purple"]Section "input Device"[/COLOR] sector in the file. 

3)  now, save and close and then press CTRL+ALT+BACKSPACE to restart X, log back in and hover ur stylus over your wacom and it should work fine...

4)  MAKING GIMP WORK RIGHT!--now, go to gimp click file>preference>input Devices>configure extended input devices ...click "device" and for "eraser, cursor & stylus" choose "mode" "screen" then click "axes" tab make sure as u scroll down the numbers go from 1 and up...so the top will be 1 and the bottom would be 6 so x: 1, y: 2, pressure 3, and so on...this will clear up alot of weird behavior u'd experience in gimp.  so its very important you number them right...if u dont then u'll have some stranger behavior as ur drawing

5)  set up expresskeys (this enables the 4buttons and touch sensitive strip on the tablet) go to this site and follow the wonderful instructions [http://ubuntuforums.org/showthread.php?t=553573](http://ubuntuforums.org/showthread.php?t=553573)


IF ALL ELSE FAILS RECONFIGURE XORG -- open terminal and type sudo dpkg-reconfigure -phigh xserver-xorg this will reconfigure your xorg. use this [COLOR="Magenta"]if 1) your having problems with your X session where the behavior of gui is acting irradical (i.e. jumping screen, fuzzy lines,etc) it means u messed up editing your xorg.conf file and u should CTRL+ALT+F2 and write the command sudo dpkg-reconfigure -phigh xserver-xorg in the terminal to re-setup xorg.conf.[/COLOR]  or 2) if your xorg.conf is a mess and dont know where to start....after u reconfigure start the tutorial over from step 2.
 

[B][U][COLOR="Sienna"]
MY XORG.CONF FILE[/COLOR][/U][/B]
# xorg.conf (X.Org X Window System server configuration file)
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

[COLOR="SeaGreen"]Section "ServerLayout"[/COLOR]

    [COLOR="Red"]InputDevice     "stylus"	"SendCoreEvents"
    InputDevice     "cursor"	"SendCoreEvents"
    InputDevice     "eraser"	"SendCoreEvents"[/COLOR]    
    [COLOR="SeaGreen"]Identifier     "Default Layout[/COLOR]"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection
[COLOR="Purple"]
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"[/COLOR]
[COLOR="SandyBrown"]EndSection[/COLOR]

[COLOR="MediumTurquoise"]Section "InputDevice"
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
EndSection[/COLOR] 



Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "WDE LTV-19w3"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GS"
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
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
EndSection

---

