---
title: "Ati Mobility Radeon x1400 + Beryl?"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by Ub1476 on 2007-05-12
Just one question, does Ati x1400 work with Beryl? Im currently using fglrx drivers, if of any help..

---

### Post by strumluff on 2007-05-12
Yes it will, you're already using the correct drivers but will have to run it with an XGL session but with a specific version of Beryl as the one in the universe repo doesn't have XGL support (not sure if the status of this has changed)

Here's a pretty good guide: [Linky]("http://ubuntuforums.org/showpost.php?p=2564461&postcount=13")

---

### Post by Ub1476 on 2007-05-12
Okay, thank you very much:)

---

### Post by Ub1476 on 2007-05-12
I used the guide, and under sessions I now have the Xgl-Beryl-Gnome option. I choose it, write username and password and log in.  I get as far as watching a brown screen, until it logs out and changes session back to gnome. Is the guide not working, or is it just me..?

---

### Post by Ub1476 on 2007-05-12
Eventually it's on the last part:

**All we have to do now is add Beryl-Manager to startup, so you don't have to load it when you login.**

After clicking "add" there are to fields: Name, and command. I wrote beryl-manager in the name field (as the guide says), but i'm not sure what to write in the command field... Can anyone help me here?

---

### Post by strumluff on 2007-05-12
Name: Beryl
Command: beryl-manager


:D

---

### Post by Ub1476 on 2007-05-12
Still doesn't work. After log in  get a brown screen (ubuntu default) + i can see my mouse. It stays there for bout 10secunds, then it automatically log out..

---

### Post by strumluff on 2007-05-12
Well if you followed the guide properly then it's possibly the way your fglrx drivers are set up.

Uninstall the current set of drivers you are using.

Then download the Envy script from here: [Linky]("http://www.albertomilone.com/nvidia_scripts1.html")

When you install it you can install the ATI drivers automatically and it does a nice job of setting up your xorg.conf as it should be. Then you can try logging in to XGL again. If that doesn't work then you will need to recheck your XGL session setup.

---

### Post by eks on 2007-05-12
Where do I check my XGL Session setup?? :D 

I have installed Beryl, but when I run it I get the following:

```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

I can't login with GNOME+XGL, I get a "session lasted for 10 seconds, see ~/.xsession-errors" which has also the XFRee86-DRI, and have to logout.

```

alaXlib:  extension "XFree86-DRI" missing on display ":0.0".

```

What could this problem be?

(I'm on a 64bit installation (AMD64) with a Radeon X1600, xorg.conf is working sweet with dual monitors).


eks

---

### Post by strumluff on 2007-05-12
Works fine on my 64bit installation, its clearly using AIGLX here but thats because you can't login in XGL.

What does your startxgl.sh script look like?

It should look like this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -dpi 96 -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

### Post by Ub1476 on 2007-05-13
I uninstall my drivers, installed Envy, and on startup i get the X error message. I had this when I started Ubuntu from live cd. I installed succesfuly with this commands: 

```

sudo apt-get update

sudo X  -configure
sudo cp /home/ubuntu/xorg.conf.new /etc/X11/xorg.conf

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

```

When ubuntu had installed I had to install fglrx on startup again. So, currently it's how my video drivers are set up (+ i enable ati in restricted drivers).

When typing fglrxinfo in the terminal, I get up this info:

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Which is wrong I think...

I guess Envy installation work okay, except that it change my xorg.conf file so it doesn't work with my system. Any solution to this?

Also I installed XGL, and when I log into it  (Ubuntu with XGL), the screen is all odd. Blurry enough that the only reason I were enable to log out were that I remembered were the log out button where by default.

---

### Post by strumluff on 2007-05-13
Um, after you installed Envy did you actually run the program? From the sounds of your post it sounds like you just installed the .deb and didn't run the application I can't be sure but it would make a big difference :P 
If you did run it do you select Install ATI drivers automatically or Install ATI drivers manually?

---

### Post by Ub1476 on 2007-05-13
Yes, I ran it in textual interface:wink: I chose 3 - Install the Ati driver (not manually). On restart Ubuntu couldn't stor cause my graphical server interface (or something) was missing. I fixed the problem my uninstalling envy and installing fglrx the way mention above.  Should I install Envy manually?

---

### Post by strumluff on 2007-05-13
Alright well it's a shame about Envy not setting it up for you, but the method you used to install the ATI drivers should be fine so I do not understand why you get an error with fglrxinfo. 
My only idea now is that your xorg.conf file is missing something. If you post your xorg.conf below I could compare it with mine to see if its not loading any specific modules or something. 
If its not the xorg.conf file then I'll be all out of ideas and hopefully somebody else can come to the rescue :)

---

### Post by Ub1476 on 2007-05-13
My xorg.conf file:

[B]Section "ServerLayout"
	Identifier	"X.org Configured"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Mouse0"	"CorePointer"
	Inputdevice	"Keyboard0"	"CoreKeyboard"
EndSection

Section "Files"
	Rgbpath		"/etc/X11/rgb"
	Modulepath	"/usr/lib/xorg/modules"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/X11R6/lib/X11/fonts/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/X11R6/lib/X11/fonts/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"record"
	Load		"glx"
	Load		"extmod"
	Load		"GLcore"
	Load		"xtrap"
	Load		"dri"
	Load		"dbe"
	Load		"type1"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/input/mice"
	Option		"ZAxisMapping"	"4 5 6 7"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Monitor Vendor"
	Modelname	"Monitor Model"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	
	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "DefaultRefresh"     	# [<bool>]
	#Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier	"Card0"
	Driver		"fglrx"
	Vendorname	"ATI Technologies Inc"
	Boardname	"Radeon Mobility X1400"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"Monitor0"
	SubSection "Display"
		Viewport	0	0
		Depth	1
	EndSubSection
	SubSection "Display"
		Viewport	0	0
		Depth	4
	EndSubSection
	SubSection "Display"
		Viewport	0	0
		Depth	8
	EndSubSection
	SubSection "Display"
		Viewport	0	0
		Depth	15
	EndSubSection
	SubSection "Display"
		Viewport	0	0
		Depth	16
	EndSubSection
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection[/B]

---

### Post by strumluff on 2007-05-13
Hm, well I'm confused as to why there are 2 Screen sections, the 1st screen section seems to be unnecessary. You also have 2 Device sections for your graphics card and 2 monitors so it looks pretty messy. Do you have 2 monitors connected? I can't advise what to change though as I simply don't know :s

I know that you need to include this for Beryl but again I don't know how significant a change it will make:

```
Section "DRI"
	Mode	0666
EndSection
```

I suppose the options you have now are to reconfigure this config and start over or find someone who can advise you better as to what needs changing.

---

### Post by Ub1476 on 2007-05-13
Okay, thanks for your help. I'm only using one monitor, but dual booting with vista. I guess that has nothing to do with it, but...

Also I have 2 input device sections..:confused: 
I don't know if it matters, but I have two more xorg.conf files:
xorg.conf.fglrx-0
xorg.conf.original-0

---

### Post by strumluff on 2007-05-13
The 2 input device sections are fine, 1 is for your keyboard, the other for your mouse. It appears what has happened is that with removal of drivers and enabling of envy and the restricted drivers manager it has written different things to the xorg.conf

Ah well those other 2 files are previous xorg.conf files that you had but your system has renamed them as it doesnt use them anymore and they are there as backups, it will be interesting to see what is in the xorg.conf.fglrx-0 file. If it looks right then you can use it by renaming it back to xorg.conf

The .original file is probably the xorg.conf file when you installed ubuntu fresh.

---

### Post by Ub1476 on 2007-05-13
Well, when I first installed Ubuntu I couldn't start it cause as I said, the fglrx driver were missing. So I kinda fail to see how the xorg.conf.originial-0 can work.. Anyways here it is:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "record"
	Load  "glx"
	Load  "extmod"
	Load  "GLcore"
	Load  "xtrap"
	Load  "dri"
	Load  "dbe"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility X1400"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by strumluff on 2007-05-13
I wanted to see the one ending with fglrx-0 not this one :)

But as you can see only 1 Screen and Device Section :)

---

### Post by Ub1476 on 2007-05-13
Oh well, sorry. Here it is: 

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "record"
	Load  "glx"
	Load  "extmod"
	Load  "GLcore"
	Load  "xtrap"
	Load  "dri"
	Load  "dbe"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility X1400"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by strumluff on 2007-05-13
Well that one truely does look messed up which would have carried over to the current conf file your system is using now. 

The easiest way you can clean this up and start fresh is to uninstall the fglrx drivers (once again I'm afraid). Then from your main system console that is Ctrl + Alt + F1.

Run this:

```
sudo dpkg-reconfigure xserver-xorg
```

This will reset your xorg.conf and give you a basic, but working setup allowing you to log back in to X without using any dodgy driver setups like the one you posted earlier. 
With a new xorg.conf you can now simply run the Restricted Drivers Manager to install the drivers for you and deal with your xorg.conf. This is the cleanest possible method to get it all setup correctly. 

Test this in a **normal** gnome session (no XGL) with fglrxinfo. Hopefully this time no errors.

From here you can then concentrate on trying it in XGL. I hope this works man :)

---

### Post by Ub1476 on 2007-05-13
Wow, that was a lot of questions..:confused: Any idea where I can find answers to all this? Like, what is bus ID?? I guess my driver for x-.. is ati?

---

### Post by strumluff on 2007-05-13
Yes you want the ati driver, most stuff it asks you should know about your monitor or find it in your monitor specification, others are best kept with the default or recommended settings, if you read the descriptions for each question you can usually find the best thing for you. 

Like for the resolutions if your monitor can handle 1280x1024 then select it with space bar.

Remember this is just to get X working so you can log in again with a clean slate (no additional drivers). Once thats done and you log in make sure things like resolution and refresh rate are set to your preference before you enable the ATI drivers from Restricted Drivers Manager.

---

### Post by Ub1476 on 2007-05-13
Alright, I've been trough it. I think i answered correctly on the questions, but still it doesn't work.. Is there some way to create a clean new xorg.conf file from desktop? Can't I just modify it by hand? Also I think I'll try Envy once more, choosing manual install.

---

### Post by strumluff on 2007-05-13
Yeah you can modify it by hand, as long as everything works to start with you can make modifications to it, remember to include at the bottom above the Composite section:

```
Section "DRI"
	Mode	0666
EndSection
```

Remember to disable the drivers from Restricted Drivers Manager before running Envy.

Hopefully someone else can voice their opinion on your problem, I'm sure there must be somebody who has had the same issue as you and found a way to fix it.

---

### Post by Ub1476 on 2007-05-13
Just look at this thread:

[http://ubuntuforums.org/showthread.php?t=413713&page=1](http://ubuntuforums.org/showthread.php?t=413713&page=1)

I'm not alone:)

Btw, can you paste your xorg.conf file in here so I can see how it's supposed to look?

I tried to follow this guide: [http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon") but at the reboot part, I got the X server error message (of course). Now as he said in the guide, the monitor and screen section should be fine, but now I have like 5 screen sections after messing with the xorg.conf file so much (not to mention i have even more xorg.conf files).

---

### Post by strumluff on 2007-05-14
Oh dear man, you're going to want to clean that up :)

Well here's mine for my laptop and it's ATI card, similar series its an X1100 but shouldn't make a difference to the  drivers amongst other things.

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
	Load		"synaptics"
EndSection

Section "InputDevice"
	Driver		"synaptics"
	Identifier	"touchpad"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"1700"
	Option		"RightEdge"	"5300"
	Option		"TopEdge"	"1700"
	Option		"BottomEdge"	"4200"
	Option		"FingerLow"	"25"
	Option		"FingerHigh"	"30"
	Option		"MaxTapTime"	"180"
	Option		"MaxTapMove"	"220"
	Option		"VertScrollDelta"	"100"
	Option		"MinSpeed"	"0.09"
	Option		"MaxSpeed"	"0.18"
	Option		"AccelFactor"	"0.015"
	Option		"SHMConfig"	"on"
	Option		"Emulate3Buttons"	"on"
	#always usefull
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
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
	DisplaySize	339	212	# 1280x800 96dpi
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"touchpad"	"AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by Ub1476 on 2007-05-14
I looked throug both the xorg.conf files and they are the same  until I came to the Device secion (or Monitor as it starts in with mine).

Here is mine:
```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

As you see there are just lots of aticonfig's ...

Your's:

```
Section "Device"
        Identifier      "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-64
        Vertrefresh     43-60
        DisplaySize     339     212     # 1280x800 96dpi
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x800"
        EndSubSection
EndSection

```

With the right options..

Obviously changing the aticonfig option to eks: Mobility Radeon X1400, will cause the X server to not work at all. Which is very odd..:confused: So what can it be? I can't understand that my graphical interface has to run on lots of aticonfigs to work, and does not work with the correct option??

---

### Post by strumluff on 2007-05-14
It's not that it is running lots of ati-configs, it is just the automated name that it has given as an identifier for your screen, monitor and device.

By the looks of it, the only thing I think is out of place are the following two things:

in the Device section you have "Option "OpenGLOverlay" "Off"" and "Option "VideoOverlay" "On"
I'm not sure what these do but I remember seeing an OpenGL error before, but they are not specified in my device section. All mine has is the device identifier, driver and the busid. You can try seeing what happens with these 2 lines removed or set to the alternate values.

The other thing is in your screen section I don't think you need the viewport line but you should add a line below Depth 24, with Modes and then specify the resolution that you want to use, for example i use "1280x800"

---

### Post by Ub1476 on 2007-05-14
Oh well:-D 

Anyways, I added my resolution + removed both of the two unknown parts. I restarted without any error messages.

I guess my xorg.conf file looks like it should then.. Also my video drivers should be installed correctly now? Oh, and ehh, in "Restricted Drivers" the ATI driver is gone now.. I couldn't have removed it by accident, could I? Maybe i just should try to reinstall Feisty Fawn..

---

### Post by strumluff on 2007-05-14
Heheh man I've never come across someone with such a problem with his graphics setup :)

Well good news that you now have no error messages, if you type this

```
glxinfo | grep direct
```

and it returns something like:

```
direct rendering: yes
```

Then we can safely say that your 3D acceleration is enabled :)

---

### Post by Ub1476 on 2007-05-14
Bad news..

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

---

### Post by strumluff on 2007-05-14
Aww! Well, if you have the time for a Feisty re-install then the first thing you should do is enable the ATI driver from the Restricted Drivers Manager, don't touch the xorg.conf :P and don't use Envy.

Run that command afterwards and it should say yes!! Then you can go back to the beginning of this thread where I posted a nice Beryl + XGL guide and follow that one :)

---

### Post by Ub1476 on 2007-05-14
So it doesn't matters if I install fglrx drivers during startup (since i can't start without)?

---

### Post by strumluff on 2007-05-14
No what will happen on a clean install is that Feisty will automatically configure your machine to run with the default ati drivers (no 3D support). You will be able to log in and work without any difficulty, take this opportunity to adjust your resolution and refresh rate as desired from System -> Preferences, no need to be editting the xorg.conf.

Once this is done then you can enable the ATI driver from the Restricted Drivers Manager (these basically are the fglrx drivers). This will take care of everything for you and should work because you haven't editted any configs or installed any previous drivers.

---

### Post by Ub1476 on 2007-05-14
I did a clean install last time. Still I had to install the fglrx drivers, even when i started Feisty from live cd. Although when i installed Edgy I could install with no problems.. Just look at this thread: [http://ubuntuforums.org/showthread.php?t=413713&page=1](http://ubuntuforums.org/showthread.php?t=413713&page=1)

Here's the bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

I tried the "solution".
```
The solution is editing xorg.conf and adding "HorizSync 36-52" and "VertRefresh 36-60" in "Section Monitor". Giving a startx, the desktop appears with normal resolution for the vesa driver (cannot use radeon driver on this machine).
Also, a sudo dpkg-reconfigure xserver-xorg, even accepting all default choices, solves the problem
```

It didn't work. I think.. Cause I edided the sync and refresh thrught..
```
dpkg-reconfigure xserver-xorg
```
..that command. I don't know if i can edit it by some other way, without touching the other stuff.

I found a new guide which seems to work for everyone!
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1)

But well, I don't know how to remove the other resolutions:biggrin:, so I'm stuck right there at the moment. I thought I just had to click Ok when the red thing were next to 640x480, but that didn't work (got the X error).. Do you know how i remove the others?

---

### Post by strumluff on 2007-05-14
If you want to edit the sync and refresh rates you need to add the following two lines in the Monitor Section of the xorg.conf. You will need to set the range to the range of your monitor though.
```

        Horizsync       28-64
        Vertrefresh     43-60
```

Removing other resolutions can also be done within the xorg.conf by removing the unwanted resolutions from the Display subsections within the Screen section. Good luck with the new solution :)

---

### Post by Ub1476 on 2007-05-14
Volalala! It worked!!!!!!! At least from the live cd:D Just gotta follow the rest of the guide now and I hope I'll soon be running beryl:)

---

### Post by strumluff on 2007-05-14
Excellent we're getting there, good luck :)

---

### Post by bro on 2007-05-14
Oh.. rejoice rejoice.. how hard it can be.. I'm looking at your conversations here.. but all I (with the proper ati-driver installed) is 

```

~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

why? what is that aiglx? I never installed it? where is xgl? I installed that! :confused:

---

### Post by Ub1476 on 2007-05-14
After the installation has finished you can install the fglrx through "Restricted Drivers Manager". (I think you need to have the internet connection active).
Then in a console
$ sudo dpkg-reconfigure xserver-xorg
Make sure you choose the 1280x800 resolution.
CTRL+ALT+BackSpac

One more problem *sigh*.. I open Restricted Drivers Manager.. And see: ATI accelerated graphics driver, staus: Not in use.

I click enable, enable again, the windows goes grey for a second, then nothing has happened. ATI is still unchecked..??? What's the problem now?

---

### Post by Ub1476 on 2007-05-14
bro:

From the error message you get, I think you just have to add this:

```
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

in your xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by strumluff on 2007-05-14
> **bro said:**
> Oh.. rejoice rejoice.. how hard it can be.. I'm looking at your conversations here.. but all I (with the proper ati-driver installed) is 

```

~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension 

```

why? what is that aiglx? I never installed it? where is xgl? I installed that! :confused:

Hehe bro, what you've done is try to run beryl in a standard gnome session with which AIGLX is standard, however you need to run it in an XGL session. If you followed the guide I posted earlier in this thread then you would have set up an xgl session already. In that case what you do is before you login to Ubuntu you select "Sessions" and select the session name that you created for XGL and then login. That should run the XGL server if you set it up correctly.

Ubi, why did you say that you need to select 1280x800 as a resolution?

As for the Restricted Drivers issue, I don't know ubi, remember we can test if they are actually in use, with glxinfo | grep direct and fglrxinfo

---

### Post by Ub1476 on 2007-05-14
1) Fglrx is not installed. I checked fglrxinfo.

2) I didn't say that, the guide did. Anyways it's my default resolution so I would prefer that..

3) If I were so lucky to be the first to encounter this bug (I guess), can I then install it thru terminal, downloading the same file as ubuntu do automatic when I enable ati restricted driver? I enabled it when using live cd (don't ask why) and i think the file name starts on ati 7 .... and ends on .deb

---

### Post by Ub1476 on 2007-05-14
Oh, wait.. Now it works! I don't know what the prob where, Maybe it just had to take some time to recognize I had internet:) 

Okay, one more step to go...

---

### Post by Ub1476 on 2007-05-14
```
 glxinfo | grep direct
direct rendering: Yes

```
Yup, it works!:KS 

I screw my xorg.conf file when I went through ```
$ sudo dpkg-reconfigure xserver-xorg
```, so I simply ended up adding the resolutions by hand.:)

My xorg.conf file:
 ```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	36-52
	Vertrefresh	36-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

Previous (not working):
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Mobility Radeon X1400"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standard skjerm"
	Option		"DPMS"
	HorizSync	36-52
	VertRefresh	36-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Mobility Radeon X1400"
	Monitor		"Standard skjerm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

If you look in section "Module" i2c were not loaded in the not working xorg.conf. Maybe that's the bug? Anyways, thank you so much for helping a noob/newb like me!:) Would've been stuck here forever without you:p 

Now I'm just going to follow that guide you posted, which will probably work perfect this time!

---

### Post by Ub1476 on 2007-05-14
Alright, I ca't login with xgl/beryl.. I enter username and password get the ubuntu background screen + I can see my mouse/cursor then it automatic logs out. Direct Rendering: Yes. Maybe i just should try another guide?

I swear I followed this as correct as possible (odd way to say it, due to my situation:mrgreen: )

---

### Post by strumluff on 2007-05-15
Ubi I don't think the i2c module has anything to do with graphics so it probably wasn't the bug.

Right now we've sorting the graphics (finally), the next stage is getting you to successfully log in to XGL, no need to worry about running Beryl yet as thats a last stage and we can test if Beryl will work by running the Desktop Effects from System -> Preferences once you get in to XGL.

Unusual that XGL logs you out, what you'll have to do is start fresh with XGL so remove it and the current Beryl version with:

```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

Here is an alternate guide for you that should work. Note that the first half of the guide is for installing on AIGLX which will not work for you so you will have to start at the part that says "Alternate method: Using closed source FGLRX drivers from ATI." DO NOT follow all of it. Follow from the first step of the alternate method down to making the xgl.desktop script executable. Do not carry on to disable the universe repo as this is the start of installing Beryl, and we want to test XGL first.

[New Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

---

### Post by strumluff on 2007-05-15
Oh one more thing, If you added beryl-manager to your startup programs remove it as it's best we test XGL works without Beryl first. :)

---

### Post by Ub1476 on 2007-05-15
Yup it works!:) One step at a time, hehe.. Shall I just try to install Beryl then (continue on the guide)?

---

### Post by Ub1476 on 2007-05-15
I installed Beyl too, and it works!

---

### Post by strumluff on 2007-05-15
Wayhay, well done, enjoy :)

---

### Post by Ub1476 on 2007-05-15
Just a few questions..:mrgreen: 

How do I change theme using Emerald? I see the list of themes, but no option like "use/enable" or something?

How do I install plugins for Beryl? I just find plugins description on ber-project.org

---

### Post by strumluff on 2007-05-15
No all you do is click on the theme and it should load it. If it doesn't load it then right-click on the beryl ruby and select Reload Window Decorator.

As for plugins, not sure, I don't use any ! I'm waiting until compiz and beryl merge together so we can get more stable software :)

---

### Post by Ub1476 on 2007-05-15
Alright. Well, the reload thing worked. Thanks:)

---

### Post by bro on 2007-05-18
haah.. i see i mist a bit of your discussion the last 2 days.. but it works! after following the installation guide & logging in with the xgl session I had to 'enable desktop effects' again.. duhu.. I do not feel ubersmart now... but I'm happy...

@ ahum.. did I just say it worked... it works sort of... But my windows have no borders if I start beryl-manager and I somehow lost 'the cube'. Besides that it won't accept that I have 4 desktops and returns to one desktop every time I re-log in. :(

---

### Post by strumluff on 2007-05-18
Alright bro, you can't have desktop effects enables AND use beryl at the same time. They are different programs, desktop effects uses compiz, so you can only have 1 or the other.

Fixing window borders is easy, in your device section of your xorg.conf add this line:

```
Option		"AddARGBVisuals"	"True"
```

As for the cube, that issue should be fixed if you use only 1 of the programs. Give it a go

---

### Post by bro on 2007-05-18
Hi, I gave it a go... but unfortunately.. when I log in and disable the desktop effects.. nothing is left but a 'normal' Gnome session. If I type 'beryl' I get this response: 
```

$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0


```
After which my window decorations disappear again. 
Also I have two device sections in my xorg.conf. I added it first only to the one that mentioned 'ati' but then to both.. neither worked. 

You say I cannot use both (beryl/compiz) and I used the guide mentioned above to install Beryl. I can only activate 'desktop effects' (compiz) when I log in using the Beryl-xgl session...

---

### Post by strumluff on 2007-05-18
Thats right, with this ATI card you must log in to XGL to use either desktop effects OR beryl. Now if desktop effects work properly in XGL without you starting beryl, or beryl-manager then that at least means your graphics are set up properly.

---

### Post by bro on 2007-05-19
I'd be happy if either one of them (beryl / desktop effect) would work Properly. But they don't. The thing with borders of windows disappearing happens when i start beryl-manager. Only if I have  desktop effects enabled it works, but my cube is gone.. it was there for a moment but I don't know what I did.. it's gone, after that I removed and reinstalled the whole bunch of beryl.  To no avail, the output is as above.

---

### Post by eks on 2007-05-19
Hello!

First of all, thanks a lot for all the posts! I've been reading this thread since it started because I'm also the unfortunate owner of a Radeon X1600 (not mobile though). I ended up re-installing the system and tried to go through slowly, with baby steps, and was able to successfully install fglrx drivers and Xgl. Or almost. And maybe this almost is preventing beryl from working, which probably is a similar problem to what bro has.

When I login into a normal **GNOME session**, everything seems to be working:

```

eks@domub:~$ glxinfo | grep direct
direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))

eks@domub:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

Beryl doesn't starts because it's not an Xgl session. Ok. Now when I reboot/logout and login into a **XGL session** I have this:

```

eks@domub:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))

eks@domub:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```

This was all after a **clean install**. The weird thing is that I can turn on and off desktop effects and they work without any problem. Beryl though has no windows borders and no cube, similar I think to whats happening to bro (?). The difference is that I was never able yet to run Beryl, and Feisty is my first Ubuntu. :)

All drivers and programs were downloaded from the repositories, through the Synaptic Package Manager, with the following order:

. xorg-driver-fglrx
. xserver-xgl (then configured startxgl.sh and xgl.desktop, tested and worked, although without direct rendering on xgl already)
. beryl and emerald themes

I would try to install ATI drivers from their webpage, since it's a newer version. But could not do it because I ran into [this problem]("http://ubuntuforums.org/showthread.php?t=447982")...

Any ideas?


eks

---

### Post by strumluff on 2007-05-19
> **bro said:**
> I'd be happy if either one of them (beryl / desktop effect) would work Properly. But they don't. The thing with borders of windows disappearing happens when i start beryl-manager. Only if I have  desktop effects enabled it works, but my cube is gone.. it was there for a moment but I don't know what I did.. it's gone, after that I removed and reinstalled the whole bunch of beryl.  To no avail, the output is as above.

Well bro, I'll have you know that I stopped using Beryl now and switched to compiz as its just more stable and most of the effects are there anyway. Don't run beryl-manager and I can help you get your cube to work with desktop effects.

All you need to do is type the following in a terminal:

```
gconftool-2 –type int –set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 –type int –set /apps/compiz/general/screen0/options/number_of_desktops 1
```

If you want to configure compiz further and use extra effects then all you have to do is install the extra packages 

```
sudo aptitude install compiz-extra gnome-compiz-manager
```

After its installed you can go to System -> Preferences -> GL Desktop 

And configure compiz from there.

If after all that it works for you and you want more. Someone has cleverly made Emerald (theme manager) work for compiz. Check it out at this thread if you want to use beryl themes for compiz: [Linky]("http://ubuntuforums.org/showthread.php?t=423743")

---

### Post by strumluff on 2007-05-19
Hi eks the problem with you pretty much looks like the xorg drivers you installed have not actually been configured to work in your xorg.conf

Did you install the drivers through Restricted Drivers Manager? If you didn't, then you should have :P as that sorts out your xorg.conf for you.

If you like we can try and fix this manually by posting your xorg.conf. By the looks of things you have XGL and beryl installed fine.

Edit: In fact, I think I've spotted the problem already. Add this line to the top of your xorg.conf file in the "Module" Section:

```
Load          "dri"
```

---

### Post by eks on 2007-05-19
My xorg.conf is the default one (with AddRGBVisuals and Composite disabled). I didn't used Restricted Driver Manager because on my first installation it used a Mesa3d driver. With Synaptic it installed ATI drivers. One would think they both download from the same repositories, no?

Here's the xorg. Its already with load dri... :(

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:7:0:0"
	Option 		"AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"Q770"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Q770"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

---

### Post by eks on 2007-05-19
Argh. Now this is confusing. When I enable Composite in xorg.conf and reboot, the next login Ubuntu uses:

```

OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

And the Xgl session is messed up and unusable (something with the frequency it seems).

CORRECTION: Then I have to REINSTALL fglrx with Synaptic and reboot (doesn't need to uninstall and install again, just a reinstall will do the trick) :)

**What is the composite option for?** Beryl and Compiz aren't "composite managers" and thus need composite to be enabled?

If yes, how to enable it without Ubuntu changing it to this Mesa driver?


eks

---

### Post by strumluff on 2007-05-19
No composite should not be enabled, because the fglrx drivers do not support the composite extension, only the open-source drivers and nvidia drivers do. That is why we use XGL to get around this we can use compiz/beryl without composite.

What confuses me is that your xorg.conf file that you posted looks fine.

I would recommend you just use the driver in the Restricted Drivers Manager as that is all you need. Then try reinstalling beryl in case it has set any configs to a previous configuration and try again.

---

### Post by eks on 2007-05-19
Maybe it's this?

```

eks@domub:~$ xdriinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Screen 0: not direct rendering capable.

```

DRI stands for Direct Rendering Interface, right?

And if I'm using Xorg, why I need XFree86-DRI?


eks

---

### Post by Ub1476 on 2007-05-19
Hi, I don't know if this is your problem, but if you are using the latest Beryl updates (0.2.1.) it doesn't work anymore. Themes goes nuts and no desktop effetcs are working. So you most be sure of that you installed the right version!:) Also this is my glxinfo | grep direct when running in XGL:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

..and beryl (if of any help)

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```

xdriinfo:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Screen 0: not direct rendering capable.

```



Funny is that direct rendering says "no", still it's working.. Also I'm using drivers from Restricteed Drivers Manager. But I guess you know since I've been discussing this with strumluff from the beginning of the thread:biggrin:

---

### Post by adarkenigma on 2007-05-19
```
sudo depmod -ae
```
restart

---

### Post by eks on 2007-05-19
> **Ub1476 said:**
> Hi, I don't know if this is your problem, but if you are using the latest Beryl updates (0.2.1.) it doesn't work anymore. Themes goes nuts and no desktop effetcs are working. So you most be sure of that you installed the right version!:) 

Yes! It's the 2.1 one:

```

eks@domub:~$ beryl --version
beryl-core 0.2.1

```

Where can I find the previous one?? :)



eks

---

### Post by strumluff on 2007-05-19
Ah so you didn't follow that guide at the beginning of the thread properly !

Well the easiest workaround for you is to go into synaptic do a Search for -> "beryl" and set all beryl packages back to 0.2.0 by selecting each package and going to Package -> Force Version and select 0.2.0 to downgrade them. After downgrading them you should lock the versions by selecting each package and going to Packages -> Lock Version.

EDIT: If there isn't a previous version that means that the universe repo is not holding the 0.2.0 version so you will have to temporarily disable the universe repo and add a 3rd party beryl repo to install 0.2.0.

Here's the original guide again, follow the steps that you need (the parts for the 3rd party repo and locking the versions, and re-enabling the universe repo). It will also be a good idea to check that you have done the other steps too :)

---

### Post by eks on 2007-05-19
Arf... This is quite frustrating... After reading [this]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29") and [this]("https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/95394") (which is the guide you mentioned I think? :)), I'm almost sure Beryl 2.0 will work. I downloaded 2.0 version from Synaptic but it doesn't work still... And got worst, when beryl-manager starts, everything turns white (although the cube works). The problem, I think, was that Synaptic didn't allowed me to download beryl-settings-bindings other than 2.1.

I just found the [Ubuntu Beryl Repository]("http://ubuntu.beryl-project.org/dists/feisty/main/") on the web, so I will try to download and install manually. Otherwise I'm giving up on Beryl, already wasted too many days trying to make it work... :(

---

### Post by Ub1476 on 2007-05-19
Did you start from begining when following this [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")?

Cause you should remove Beryl and XGL completely before "restarting"
```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

Remember to use the alternative method (you have ATI, right?) which starts like this :
Alternate method: Using closed source FGLRX drivers from ATI. 

So just download and install everything using the terminal. Should work then

---

### Post by eks on 2007-05-19
> **Ub1476 said:**
> Did you start from begining when following this [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")?

Yes I did, and still it didn't worked. Installed all 2.0 packages manually because I have an AMD64 (had to turn off universe repository otherwise it would download the 2.1 when it needed dependencies). I'm extremely frustrated and wasted, so I give up on beryl. :(

Strumluff, would you be so kind to point how to make emerald themes run on compiz?


eks

---

### Post by strumluff on 2007-05-19
Don't worry if you can't get Beryl to work with ATI, it is still in early development and ATI are getting to work on making the composite extension work with their linux drivers so we don't need to worry about all this XGL business :)

Yeah eks read the first post of this thread: [Linky]("http://ubuntuforums.org/showthread.php?t=423743")

If you run 32bit ubuntu then you can use the debs posted in that post otherwise you will have to follow the build from source instructions for 64bit. I got it working on my ubuntu 64, so I basically have all the effects I want and the borders I want without Beryl :)

---

### Post by eks on 2007-05-19
Well... I forgot to take a look at [Beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046") and found that [typing this]("http://forum.beryl-project.org/viewtopic.php?p=23487#p23487"):

```

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl & emerald &

```

Worked. :D

But it's too fragile to be used by my wife, which will be using this computer also. I tried to compile emerald for amd64, but it gave an error then I decided gnome-look.org is easier and faster to get some themes for compiz. But really thanks a lot for all the help anyway!

Now... will I be able to install AWN dock on compiz.........? :D


eks
PS: I really hope this compiz-beryl merger will yeld some stable working results soon. It will **certainly greatly** help Linux get more mainstream.

---

### Post by Ub1476 on 2007-05-19
At least kiba-dock works in Compiz. 

Good guide here: [Linky]("http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html")

It's much like AWN, I think. Looks like a Mac doc, with just many more configurations:)

---

### Post by eks on 2007-05-19
Well...

After all my headache trying to make beryl work, now I found out that ATI drivers won't run Xgl with dual monitors setup, only single. So no desktop effects, no fancy dock, no beyrl, no compiz, because ATI doesn't care for Linux users. I had enough of this, I will be selling this card and buying a nVidia one and never by a ATI product again.



eks

---

### Post by hkahwaji on 2007-06-08
I have been following this thread and now I had the same problem as Ub1746. I am going to do a fresh re-install of Fiesty and follow the guide. I have an ATI X1400. I hope this time it will work with XGL.

---

### Post by hkahwaji on 2007-06-08
So I followed this forum and I was able to install Beryl successfully. I did a fresh install of Fiesty, enable ATI X1400 Driver in Restricted Device Driver and followed the rest of the guide by creating xgl and then installing Beryl.

I recommend following this guide

---

### Post by kubhunter on 2007-06-12
Hi

I followed this list in detail but am stuck at the point of getting xgl to work.
I tried the "alternate method" but with the same sorry effect- that it logs me out.

I am running kubuntu, does that make a difference ? 

how do I get all this working with kde ? any idea? 

this is frustrating.. 

thanks

---

