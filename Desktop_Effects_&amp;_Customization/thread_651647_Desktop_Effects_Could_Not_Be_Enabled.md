---
title: "Desktop Effects Could Not Be Enabled"
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by evolgenius513 on 2007-12-27
"Desktop Effects Could Not Be Enabled" is the message that keeps appearing when I try to use custom effects for the appearance preference settings.

My "lspci | grep VGA" reads:
  Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I have a Dual Boot Ubuntu/XP on my HP Pavilion Desktop. 

If you can help please do. Thanks.

---

### Post by Forlong on 2007-12-28
What's the output of ```
compiz
``` in a terminal?

---

### Post by Saint Angeles on 2007-12-28
make sure you have composite extensions enabled in your xorg.conf 

i'll attach my xorg.conf just for good times sake!

---

### Post by banda on 2007-12-28
having the same issue with the onboard grafics of intel dg965 motherboard.

---

### Post by Forlong on 2007-12-28
> **banda said:**
> having the same issue with the onboard grafics of intel dg965 motherboard.
Same goes for you: please post the aforementioned output.

---

### Post by banda on 2007-12-28
on running 'compiz' in terminal i get - 
> Checking for Xgl: not present. 
Blacklisted PCIID '8086:29a2' found 
aborting and using fallback: /usr/bin/metacity 

---

### Post by Forlong on 2007-12-28
Try running Compiz like this:
```
SKIP_CHECKS=yes compiz
```

If it works, do this:
```
gedit ~/.config/compiz/compiz-manager
```
Put this in there:
```
SKIP_CHECKS=yes
```
And save.

Then you don't have to run that command yourself anymore.

---

### Post by banda on 2007-12-28
yea did that and compiz works now:). but now my video playback is broken. all the players crash as soon as playback begins.

---

### Post by Forlong on 2007-12-28
> **banda said:**
> now my video playback is broken. all the players crash as soon as playback begins.
The chip has been blacklisted for a reason.

Just disable Compiz prior to watching movies then.

---

### Post by RavUn on 2007-12-28
Thanks for this info, I've been having this problem as well and will try this fix when I get home.

I read somewhere about the issue with having to disable compiz before watching movies and there's a way to set it up so you do not have to do it every time.  I'm going to browse the forums and hopefully can find it.

---

### Post by psyopper on 2007-12-28
You can try enabling the Video Playback plug-in in CompizConfig Settings Manager. As Forlong pointed out, your chipset was blacklisted for a reason, and this may be it. If you don't have CCSM installed let us know your version of Ubuntu (7.04 or 7.10) and we can give instructions on how to install it.

---

### Post by SimonM on 2007-12-29
I'm having the same problem

> simon@localhost:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

I also tried the SKIP_CHECKs method and got this:

> simon@zeta:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


Please help me, I was fine using Beryl on Feisty, but since I upgraded, I haven't been able to get any of the effects to work.

Thanks

---

### Post by Forlong on 2007-12-29
What type of graphics card are you using?

You also might want to post your xorg.conf:
```
grep -v ^# /etc/X11/xorg.conf
```
use the forum's CODE tag please (# button) instead of the QUOTE tag.

---

### Post by RavUn on 2007-12-29
I get the same as the guy above when I skip checks.

Video card:
```
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

```

output of xorg.conf
```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "1825"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "1825"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

```

---

### Post by Forlong on 2007-12-29
I'm sorry but I don't think Compiz can work on that card.

---

### Post by RavUn on 2007-12-29
I figured.  I have another PC I'm putting together so I'll try to get it working on that one whenever I get a power supply.

Thanks

---

### Post by gibby213 on 2007-12-30
I've got this same problem with an ATI Radeon X1600.  I've had several issues in the past and I'm excited at the moment just to have fglrx loading automatically.  I've tried using XGL for desktop effects but it runs abysmally slow and incidentally the effects don't work at all.  Now I'm avoiding XGL by suggestion and.

```
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
	#    InputDevice     "stylus"    "SendCoreEvents"
	#    InputDevice     "cursor"    "SendCoreEvents"
	#    InputDevice     "eraser"    "SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
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
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1200"
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
	Option		"Composite"	"1"
EndSection
```

```
gahnjc@gahnjc-1:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c5 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

```
gahnjc@gahnjc-1:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c5 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Dojan5 on 2007-12-30
When just typing in compiz in the terminal like this...
```
joel@Kissedesigns-2c:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```
And yaa, the result as above too...
I followed this blog:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
And, nothing comes out of it...
When clicking, yaa apply desktop effects the thing > Desktop Effects Could Not Be Enabled'
Comes up...
Im running Ubuntu Gutsy Gibbons (<3) and almost everything works perfectly...
Im just trying to get a theme i downloaded for beryl to work, and i got over the desktop effects...
Help?

```
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
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
	Identifier	"S3 Inc. Savage 4"
	Driver		"savage"
	BusID		"PCI:2:7:0"
EndSection

Section "Monitor"
	Identifier	"Nokia 447W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. Savage 4"
	Monitor		"Nokia 447W"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
Thats the output...

---

### Post by Forlong on 2007-12-30
gibby213, you can't use Compiz without Xgl on that card (there's the latest ATI driver of course but it has other issues).
Install Xgl again:
```
sudo apt-get install xserver-xgl
```
Restart X and post the output of ```
compiz
``` in a terminal again.


Dojan5, I'm sorry but your graphics chip is not able to run Compiz.

---

### Post by pelo8280 on 2007-12-31
I have an Intel graphics card that ran compiz just fine, but then I decided to play around with dual monitors.  Intel cards can't handle more than 2048x2048 with xgl enabled, so I removed it.  Now I want compiz back, but xgl is *really* slow and pretty unusable.

Here's my xorg.conf:

```
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

Section "Files"
EndSection

Section "Module"
	Load		"dri"
	Load		"glx"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Extensions"
	Option		"Composite"	"1"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes		"1280x800@60"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

If you could help that's be great!  Thanks!

---

### Post by Forlong on 2007-12-31
> **pelo8280 said:**
> ```
Section "Extensions"
	Option		"Composite"	"1"
**	Option		"Composite"	"0"**
```
Remove this line.

And Xgl as well, you don't need that with an intel chip:
```
sudo apt-get remove xserver-xgl
```
Afterwards restart X and run ```
compiz
``` in a terminal. If it's not working, post the output here.

---

### Post by pelo8280 on 2007-12-31
Boy, you're fast.  That was, what, 5 minutes? :)

That was it!  Thank you!  Really stupid on my part, though.  I guess it just goes to show you what blind copying and pasting will do, right?

Again, thank you!

---

### Post by RavUn on 2008-01-04
Would anyone know if compiz would work on this card:
> 01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

I still get
```
ravun@RavUn:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

when running compiz...
when I run ```
SKIP_CHECKS=yes compiz
``` it gets to ```
Checking for texture_from_pixmap: 
``` then logs me out.

xorg.conf:

```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "1825"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Monitor         "1825"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

EndSection

```

---

### Post by Lacent on 2008-01-04
I get an error message with desktop effects, too. Here is what it says when I type compiz in the terminal:


```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "murrine",

```


Thanks for any help

---

### Post by Krynoc on 2008-01-05
I also am unable to enable desktop effects, when i run compiz in terminali get the output.

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0091 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
/usr/bin/compiz.real (core) - Fatal: No valid GL extensions string found.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

I have a nVidia 7800 GTX, any help would be appreciated.

~Krynoc

---

### Post by Forlong on 2008-01-06
RavUn: I'm sorry but no, Compiz won't run with that card.


Lacent: what's your graphics card & driver?


Krynoc: Post the output of ```
dpkg -l | grep compiz
```

---

### Post by Phil420 on 2008-01-06
live RavUn, when i run compiz in the terminal it gives me this..

> **RavUn said:**
> 
```
ravun@RavUn:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```


my graph card is a ATI X1650 Pro... what's wrong?

---

### Post by Forlong on 2008-01-06
You need to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by Phil420 on 2008-01-06
> **Forlong said:**
> You need to install Xgl
i did that, it was already updates, it said, but when i retype compiz, it tells me the same bull... 
when i go in my Catalyst control center, it tells me the card isn't properly installed, that drivers are missing or uninstalled or whatever so i use Envy to get the drivers fixed, but when i reboot my pc, nothing happens.. after that i reboot again and use an other thing to reconfigure my x server to make ubuntu work again... does those two things have a link? cus after doing that Catalyst still tells me my card is messed up...

---

### Post by phmcguin on 2008-01-06
This seems to be the place to get things done! I'm having simillar problems as above. 

Compiz output:

<code>
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
</code>

SKIP_CHECKS=yes compiz

<code>
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
</code>

Sorry this isn't properly formatted but I don't know how!

---

### Post by Ub1476 on 2008-01-06
> **Phil420 said:**
> i did that, it was already updates, it said, but when i retype compiz, it tells me the same bull... 
when i go in my Catalyst control center, it tells me the card isn't properly installed, that drivers are missing or uninstalled or whatever so i use Envy to get the drivers fixed, but when i reboot my pc, nothing happens.. after that i reboot again and use an other thing to reconfigure my x server to make ubuntu work again... does those two things have a link? cus after doing that Catalyst still tells me my card is messed up...

When you installed the drivers using Envy, did you remove the previous drivers first? Did you use the restricted drivers or had you manually installed those from ATIs website? Did you tell Envy to reconfigure xorg.conf (xserver) automatically for you as well? 

> **phmcguin said:**
> This seems to be the place to get things done! I'm having simillar problems as above. 

Compiz output:

<code>
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
</code>

SKIP_CHECKS=yes compiz

<code>
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
</code>

Sorry this isn't properly formatted but I don't know how!

Please post the output of:

```
lspci | grep VGA
```

---

### Post by phmcguin on 2008-01-06
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)


That's it. Do you think you can help. I've really no idea what to try.

Thank you so much for taking the time to look at this!

---

### Post by Ub1476 on 2008-01-06
> **phmcguin said:**
> lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)


That's it. Do you think you can help. I've really no idea what to try.

Thank you so much for taking the time to look at this!

Do you have resolution issues? It might be the root to the probem that direct rendering isn't working either. If so, look [here]("http://ubuntuforums.org/archive/index.php/t-594428.html") (the latest posts).

---

### Post by phmcguin on 2008-01-06
I had resolution issues but I've managed to fix them. I just had to select the correct display adapter.

I'm confident I have the correct drivers installed too.

Can you think of anything else it might be? Or how can I try and debug what's going on? The output from "compiz" doesn't mean much to me.

---

### Post by nnamdi on 2008-01-06
am usin a hp pavilion and i used this command to get my compiz workin
but pls tryin dis will be at ur risk cos i was told the same thing. the problem is some graphics card has been blacklisted so u could get it workin try this


mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

### Post by phmcguin on 2008-01-06
I don't think that will fix it because when I run "SKIP_CHECKS=yes compiz" it still doesn't work. If you look back at my previous post you can see the output of SKIP_CHECKS=yes compiz. It's a mess!

---

### Post by Ub1476 on 2008-01-06
Alright, post the output of:

```
glxinfo | grep render
```

And show us your xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by phmcguin on 2008-01-06
```
glxinfo | grep render
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

and 

xorg.conf is:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Acer"
	Modelname	"Acer V771"
	Horizsync	30.0-72.0
	Vertrefresh	50.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1280x1024@60"	"1400x1050@60"	"1280x960@60"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection
```

if you can make sense of this I'm very impressed!

---

### Post by Ub1476 on 2008-01-06
Well, you're definetly not getting 3d acceleration with the vesa failsafe driver. Look at post #19-#22 in this [thread]("http://ubuntuforums.org/showthread.php?t=594428&page=2") to solve your issue.

BTW, backup your xorg.conf before doing anything with it:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bac
```

Should X fail, simply use the old settings by:

```
cp /etc/X11/xorg.conf.bac /etc/X11/xorg.conf
```

---

### Post by phmcguin on 2008-01-06
Ok. I think there might be something here. Under System > Administration >Screen and Graphics the screen setting and selection is correct.

BUT..in the Graphics Card tab it has "graphics card (NVIDIA GeForce2 DDR (Generic))

and driver is: "vesa -Generic VESA-sompliant video cards"

I selected the correct driver..logged out/logged in. let it install the drivers. Then did a restart. 

and now the right driver is displayed in Screen and Graphics. But I still can't enable desktop effects.

What should I check now?

---

### Post by Ub1476 on 2008-01-06
Just repost the above commands I gave you as well as "compiz". I got to go now thought, but I'll help you tommorow:)

---

### Post by fbwr75215 on 2008-01-06
I am having the same problem that Krynoc is having.  I have two seperate X Sessions running.  One is my LCD screen and the other is my TV.  Here is the results from running dpkg -l | grep compiz...

```
fbwr@ubuntu:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings

```

---

### Post by Ub1476 on 2008-01-07
If I recall correctly you can't run Compiz with two sessions at the same time. it will be possible in the future though, so no worries (future means "pretty close" in Linux). 

If you can't run Linux when only using your default monitor, post the output of:

```
compiz

lspci | grep VGA
```

---

### Post by phmcguin on 2008-01-07
I'm making progress. But I still need some help. I've no got the correct drivers installed and my card is working correctly. I can now see screensavers! But still no desktop effects :confused:

```
glxinfo | grep direct
direct rendering: Yes
```

--this looks good. 

```
compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0150 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

But compiz only get this far then hangs! If I use SKIP_CHECKS=yes COMPIZ
it crashes the GUI and I can just see my desktop without toolbars or anything.

Output of my xorg.conf is:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
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

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce2 DDR (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Acer"
	Modelname	"Acer V771"
	Horizsync	30.0-72.0
	Vertrefresh	50.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1024x768@85"	"1024x768@75"	"832x624@75"	"1024x768@70"	"800x600@60"	"1024x768@60"	"800x600@85"	"1024x768@43"	"800x600@75"	"1152x864@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@85"	"1400x1050@60"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection
```

any ideas on how to get desktop effects working?

thanks in advance. I'm really stuck on this.

---

### Post by Forlong on 2008-01-07
Try resetting your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```
And afterwards run this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restart X and see if it worked.

---

### Post by phmcguin on 2008-01-07
I completed step one and it made absolutely no change to the system! 

I can't run the second command I don't think I have that package installed. Is it driver dependant?

---

### Post by Forlong on 2008-01-07
> **phmcguin said:**
> I can't run the second command I don't think I have that package installed. Is it driver dependant?
How did you install the driver for your card?

---

### Post by phmcguin on 2008-01-07
I just reinstalled using "Envy". But no success. Still can't enable desktop effects.

:mad:

---

### Post by Forlong on 2008-01-08
You should try getting rid of the driver you installed with Envy and install the driver from the repositories via *System &#8594; Administration &#8594; Restricted Drivers Manager*

---

### Post by Krynoc on 2008-01-09
output of compiz
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0091 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
/usr/bin/compiz.real (core) - Fatal: No valid GL extensions string found.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

output of  dpkg -l | grep compiz
```

ii  compiz                                 1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager
ii  compiz-core                            1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra            0.5.2+git20070928-0ubuntu1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main             0.5.2+git20070928-0ubuntu2        Collection of plugins from OpenCompositing f
ii  compiz-gnome                           1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager - GNOM
ii  compiz-plugins                         1:0.6.0+git20071008-0ubuntu1.1    OpenGL window and compositing manager - plug
ii  libcompizconfig-backend-gconf          0.5.2+git20071010-0ubuntu1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                       0.5.2+git20070919-0ubuntu3        Settings library for plugins - OpenCompositi
```

Sorry that took so long to get up, again thanks for your help

---

### Post by Forlong on 2008-01-09
Krynoc, please post your xorg.conf:
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by JCHIRO on 2008-01-09
Check to see if your PCIID is blacklisted.  There are some downfalls when using Intel.

---

### Post by josh.on.linux on 2008-01-09
Hi!

I am encountering the same problem, cannot get Compiz to work.  Since I am relatively new to Linux, I have not had much success in fixing this yet.

Here's my information:

**glxinfo | grep direct**

```
joshua@MainTowerJ:~$ glxinfo | grep direct
direct rendering: Yes
```

**SKIP_CHECKS=yes compiz**

```
joshua@MainTowerJ:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0150 (rev a4) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: present. 
/usr/bin/compiz: 352: nvidia-settings: not found
[: 352: 65536: unexpected operator
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
/usr/bin/emerald: /home/joshua/.mono-1.2.5.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/bin/metacity: /home/joshua/.mono-1.2.5.1/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
```

**xorg.conf**

```
xorg.conf

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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"nVidia Corporation NV15 [GeForce2 GTS/Pro]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"AL1916"
	Vendorname	"Acer"
	Modelname	"Acer AL1914"
	Horizsync	30.0-83.0
	Vertrefresh	55.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"AL1916"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

Any help is greatly appreciated!  Thank you!

Josh

---

### Post by Forlong on 2008-01-10
Josh, how did you install the driver to your graphics card?

---

### Post by johnwren on 2008-01-10
I'm running 7.10 (32 bit) on a Dell Latitude D531.  I've intalled the ATI restricted drivers using the restricted drivers manager.  3D games run fine, but compositing does not. I ran the compiz as per previous entries in the thread:
johnwren@johnwren-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


johnwren@johnwren-laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 

Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:12812): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:12812): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension

And what I hope is the relevant output of xorg.conf is:
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        
        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

i'm tempted to just manually edit that 'composite  "0" entry to a one.  Will that work?

Thanks for any and all help.  I'm learning.

---

### Post by Forlong on 2008-01-10
> **johnwren said:**
> i'm tempted to just manually edit that 'composite  "0" entry to a one.  Will that work?
No. With the proprietary fglrx driver you need to install Xgl in order to run Compiz.:
```
sudo apt-get install xserver-xgl
```

But then you may have troubles running 3D-games.

---

### Post by mirulmuffs on 2008-01-10
hey i have some trouble with wine today and when i remove wine the desktop effects was disabled.

this is the output of compiz

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

what should i do? i've reinstall compiz several times and it didn't seems to work.
can somebody help?

---

### Post by mirulmuffs on 2008-01-10
cont'd from above..

this is the output of 

$ grep -v ^# /etc/X11/xorg.conf

_____



```


$ grep -v ^# /etc/X11/xorg.conf


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
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection



```

---

### Post by Forlong on 2008-01-10
You seem to be using an intel chip with the nvidia driver.

If you do have an intel chip (and _not_ a Nvidia card), change this:
```
Section "Device"
    Identifier     "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver         "nvidia"
EndSection
```
to
```
Section "Device"
    Identifier     "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver         "i810"
EndSection
```
Then restart X and see if it worked.

Either way, you don't need Xgl:
```
sudo apt-get remove xserver-xgl
```

---

### Post by johnwren on 2008-01-10
Forlong: Thank you very much for your assistance.  This message posted on my fully functional (and compositing) Dell D531
John

---

### Post by josh.on.linux on 2008-01-11
> **Forlong said:**
> Josh, how did you install the driver to your graphics card?

I did it through System - Administration - Restricted Drivers (or something like that); I did it the Ubuntu Way (Ubuntu told me I needed to install and activate the restriced driver if I wanted to use Desktop Effects and 3D).  I then chose the nVidia legacy driver, which is currently in use.

---

### Post by RavUn on 2008-01-11
So, I've installed Ubuntu on 2 computers and neither of the graphics cards can run compiz.  The computer I installed it on recently is an AMD Sempron 3000+... does anyone know of a decent yet cheap graphics card I could get for it that will work with compiz?  I do not know a thing about graphics cards... I built this computer but I have never messed with a graphics card since it came with the motherboard+CPU combo.

---

### Post by Forlong on 2008-01-11
> **josh.on.linux said:**
> I did it through System - Administration - Restricted Drivers (or something like that); I did it the Ubuntu Way (Ubuntu told me I needed to install and activate the restriced driver if I wanted to use Desktop Effects and 3D).  I then chose the nVidia legacy driver, which is currently in use.
As far as I know the legacy driver has troubles with Compiz (but you may want to search the forums for a definitive answer). Getting a new(er) would be a good idea.


RavUn: Any current Nvidia card should be fine.

---

### Post by bscasta on 2008-01-11
Ok   Im really new.  when i type compiz it says
brian@brian-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

and that xorg thing says:
 brian@brian-desktop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

EndSection
brian@brian-desktop:~$

---

### Post by mirulmuffs on 2008-01-11
> **Forlong said:**
> You seem to be using an intel chip with the nvidia driver.

If you do have an intel chip (and _not_ a Nvidia card), change this:
```
Section "Device"
    Identifier     "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver         "nvidia"
EndSection
```
to
```
Section "Device"
    Identifier     "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver         "i810"
EndSection
```
Then restart X and see if it worked.

Either way, you don't need Xgl:
```
sudo apt-get remove xserver-xgl
```

i've done everything u mentioned and when i type compiz on terminal it ended up like this.

```


Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0




```

---

### Post by josh.on.linux on 2008-01-11
> **Forlong said:**
> As far as I know the legacy driver has troubles with Compiz (but you may want to search the forums for a definitive answer). Getting a new(er) would be a good idea.


RavUn: Any current Nvidia card should be fine.

So you think my card can work with newer drivers?  To be on the safe side, would I have to do a backup of the whole system prior to updating, or is there a specific directory/file that I could update and replace, should anything go wrong?

Thank you for your help!

---

### Post by Forlong on 2008-01-12
> **bscasta said:**
> 
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
Sorry, your graphics chip('s driver) can't handle Compiz.


mirulmuffs, please post your xorg.conf again.
Oh, and please don't skip checks anymore. Your graphics chip is not on the blacklist.

> **josh.on.linux said:**
> So you think my card can work with newer drivers?
No, I don't think so, I recommend using only the driver Ubuntu "gives" you.
But I'm by no means a Nvidia expert - maybe there is a way to get Compiz working with your card but I doubt it, frankly.
All I can recommend you for now is doing a search in the forum to see if anyone managed to get Compiz working with your type of card (and how).

---

### Post by josh.on.linux on 2008-01-12
> **Forlong said:**
> 
No, I don't think so, I recommend using only the driver Ubuntu "gives" you.
But I'm by no means a Nvidia expert - maybe there is a way to get Compiz working with your card but I doubt it, frankly.
All I can recommend you for now is doing a search in the forum to see if anyone managed to get Compiz working with your type of card (and how).

Ok, thank you for your help! :-)

Kind regards,

Joshua

---

### Post by POV_Dave on 2008-01-12
Greetings one and all, I'm a first time linux user as of a week ago, I've installed Ubuntu 7:10 and I too am having problems getting visual effects to work.  If anyone could offer a first timer a hand on this, I'd be forever in your debt.

OK, so here's the info I think I need to show:

> dave@Silly-Ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF


and...

> dave@Silly-Ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5446 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 

Here's the xorg.conf:
> 

dave@Silly-Ubuntu:~$ xorg.con
bash: xorg.con: command not found
dave@Silly-Ubuntu:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5446 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Root visual is not a double buffered GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
gedit ~/.config/compiz/compiz-manager
dave@Silly-Ubuntu:~$ gedit ~/.config/compiz/compiz-manager
dave@Silly-Ubuntu:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Rage 128 Pro Ultra TF"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "S/M 170MP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Rage 128 Pro Ultra TF"
        Monitor         "S/M 170MP"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

EndSection

Is it possible to get the visual effects working or am I blacklisted?
also, as a total n00b to the use of linux, please forgive me if i missed something, I looked over the posts here, but I may have missed the obvious answer :)

Thanks in advance!

-Dave

---

### Post by Forlong on 2008-01-13
Rage cards are too old for Compiz. ATI doesn't support them anymore and they are not Radeon cards, so they are not supported by the open radeon driver.

---

### Post by POV_Dave on 2008-01-13
> **Forlong said:**
> Rage cards are too old for Compiz. ATI doesn't support them anymore and they are not Radeon cards, so they are not supported by the open radeon driver.

Well that solves that mystery.  Thanks anyway, That is yet another reason why I need to build a new computer.  

No fancy desktop effects for me.  Not mine,

---

### Post by audiored on 2008-01-13
So this is a clean reinstall.  

My video card is an:
> ATI Radeon X300 SE 128 MB

The steps I've taken so far:
> sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv

I rebooted...

My xorg.conf:

> xxx@ubuntu-desktop:~$ grep -v ^# /etc/X11/xorg.conf


Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
        Load  "GLcore"
        Load  "dri"
        Load  "v4l"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
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



and if...

> xxx@ubuntu-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

and if then..

> xxx@ubuntu-desktop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv

What's my prognosis?  :confused:

---

### Post by mondoUNC on 2008-01-14
ok, i installed drivers for my IBM Thinkpad R51 laptop using the Restricted Drivers Manger. I'd been using Gutsy for a month and had a few problems today and now compiz suddenly doesn't work. I tried installing xserver-xgl and that resulted in not being able to login.

When i try to run compiz:
```
mondo@mondo-ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Skip Check:
```
mondo@mondo-ubuntu:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: /usr/bin/glxinfo: symbol lookup error: /usr/bin/glxinfo: undefined symbol: glXChooseVisual
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real: symbol lookup error: /usr/bin/compiz.real: undefined symbol: glXGetConfig

```

xorg.conf:
```
mondo@mondo-ubuntu:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

        InputDevice     "Synaptics Touchpad"
EndSection

```

Any help would be great. seems like Forlong is doing a great job. Thanks in advance.

---

### Post by Forlong on 2008-01-14
> **audiored said:**
> What's my prognosis?  :confused:
You need to install Xgl:
```
sudo apt-get install xserver-xgl
```
> **mondoUNC said:**
> ok, i installed drivers for my IBM Thinkpad R51 laptop using the Restricted Drivers Manger. I'd been using Gutsy for a month and had a few problems today and now compiz suddenly doesn't work. I tried installing xserver-xgl and that resulted in not being able to login.
According to the PCI ID you are having an intel 82852/855GM chip in use.
You don't need any restricted drivers for that (in fact, there is none, intel's drivers are open source and come with Ubuntu pre-installed) and you don't need Xgl either.

So the question is what did you last do to make it stop working?


P.S. Everybody, [COLOR="Red"]please do not run Compiz with SKIP_CHECKS set to "yes" if you don't know what you are doing. It's doing more harm than good.[/COLOR]

---

### Post by mondoUNC on 2008-01-14
I had messed up some folder permissions trying to delete a bad install of Fuppes. once i got that fixed, i noticed that i only had a few kb of memory in / even though i had about 4gb hours earlier. When i looked around I found what i think was taking up the memory, but also decided to do some cleaning and accidently deleted /.metacity not realizing what it was. although I dont see how that would affect compiz

```
mondo@mondo-ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

mondo@mondo-ubuntu:~$ compiz --indirect rendering
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option --indirect

```

---

### Post by Forlong on 2008-01-14
The problem is not Compiz but your graphics chip. I don't know what went wrong there but it seems to be misconfigured now.
What's the output of ```
glxinfo | grep "direct rendering"
```

---

### Post by mondoUNC on 2008-01-14
```
mondo@mondo-ubuntu:~$ glxinfo | grep "direct rendering"
glxinfo: symbol lookup error: glxinfo: undefined symbol: glXChooseVisual

```

---

### Post by Forlong on 2008-01-14
Oh boy, that looks like a serious problem.
Unfortunately I don't know how to "fix" glxinfo. I recommend starting your own thread about this. (I guess the Hardware section would be the most appropriate for this.)
Good luck.

---

### Post by mondoUNC on 2008-01-14
Thanks for trying, I'll start a thread in hardware then.

---

### Post by audiored on 2008-01-14
Thank you Forlong.

I installed xgl.

I'm now able to turn my desktop effects on.  I am not able to see options to modify my desktop effects.  How do I customize or enable the ability to customize the effects?

Here is some additional information.



```
jarivera@ubuntu-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

```
jarivera@ubuntu-desktop:~$ glxinfo | grep "direct rendering"
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

---

### Post by Bezvardis on 2008-01-14
Hi, I have the same problem: Nvidia RIVA TNT, legacy driver installed. When I want to start desktop effects I get 'Desktop effects could not be enabled'

running compiz in terminal gives exactly the same as for mondo above: 
```

-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:002d (rev 15) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

direct rendering: ```
-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

```

I fiddled around a bit with my xorg.conf file but that did not change anything I noticed

Any ideas regarding this?

---

### Post by Forlong on 2008-01-14
> **audiored said:**
> I installed xgl.

I'm now able to turn my desktop effects on.  I am not able to see options to modify my desktop effects.  How do I customize or enable the ability to customize the effects?
See here: [How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by Forlong on 2008-01-14
> **Bezvardis said:**
> Hi, I have the same problem: Nvidia RIVA TNT
Sorry, GeForce2 MX is the oldest card that is able to run Compiz.

---

### Post by Bezvardis on 2008-01-14
> Sorry, GeForce2 MX is the oldest card that is able to run Compiz.

Thanks, at last I find why :-) Well, but this info came a bit late since I installed the xgl and it messed up a bit my screen. So  - is there a way to uninstall it?

---

### Post by Forlong on 2008-01-14
```
sudo apt-get remove xserver-xgl
``` should do the job.

---

### Post by audiored on 2008-01-14
> **Forlong said:**
> See here: [How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

I believe I got it all set up.  I really appreciate the assistance.  Thank you.  I'm sure you've answered the same newb questions a hundred times.  =)

---

### Post by coc_21 on 2008-01-14
> **Forlong said:**
> Try running Compiz like this:
```
SKIP_CHECKS=yes compiz
```

If it works, do this:
```
gedit ~/.config/compiz/compiz-manager
```
Put this in there:
```
SKIP_CHECKS=yes
```
And save.

Then you don't have to run that command yourself anymore.
I got this message when I ran SKIP_CHECKS=yes compiz

Checking for Xgl: not present. 
Blacklisted PCIID '1002:3150' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :20.0

---

### Post by Forlong on 2008-01-15
> **coc_21 said:**
> /usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :20.0
You are trying to run Compiz as a secondary user, which is not possible.

---

### Post by phoogkamer on 2008-01-17
Hello Furlong,

I have a question about Compiz on Ati Mobility Radeon running Hardy with fglrx.
When try to enable "Desktop Effects" it tells me that the Composite extension is not available.

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.1.7059 Release

~$ glxinfo | grep "direct rendering"
direct rendering: Yes

~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7149 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
 
Peter

---

### Post by mirulmuffs on 2008-01-27
i cant enable compiz.

output of compiz

```


Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5046 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 



```

---

### Post by Ub1476 on 2008-01-27
> **mirulmuffs said:**
> i cant enable compiz.

output of compiz

```


Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5046 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 



```

What's your graphic card?

```
lspci | grep VGA
```

---

### Post by phoogkamer on 2008-01-28
I have installed xserver-xgl, but after that my x session does not start. The file .xsession-errors shows the following:
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Waiting 10 more seconds for Xgl to start...
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 315672 requests (315670 known processed) with 0 events remaining.

xmodmap:  unable to open display ':1'
cannot open display: 
Voer '/usr/bin/seahorse-agent --help' uit voor een volledige lijst van opdrachtregelopties.

Could this be an authentication problem with xserver-xgl??

Peter

---

### Post by Ub1476 on 2008-01-28
> **phoogkamer said:**
> I have installed xserver-xgl, but after that my x session does not start. The file .xsession-errors shows the following:
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Waiting 10 more seconds for Xgl to start...
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 315672 requests (315670 known processed) with 0 events remaining.

xmodmap:  unable to open display ':1'
cannot open display: 
Voer '/usr/bin/seahorse-agent --help' uit voor een volledige lijst van opdrachtregelopties.

Could this be an authentication problem with xserver-xgl??

Peter

Which driver are you using? Those from ATI or those from Restricted Driver Manager?

By the way, please use the CODE tag (**#**) next time (avoids smiley and paragraph errors):)

---

### Post by phoogkamer on 2008-01-28
I am using the driver from the restricted manager, fglrx.

I'll use the code tag next time

Peter

---

### Post by audiored on 2008-01-28
I guess this is a question for Forlong since I followed your blog tutorials and posts here in setting up my graphics card and compiz.  Is there is a way to enable direct rendering?  How?  Link?  

Thanks.  =)

---

### Post by audiored on 2008-01-29
> **audiored said:**
> I guess this is a question for Forlong since I followed your blog tutorials and posts here in setting up my graphics card and compiz.  Is there is a way to enable direct rendering?  How?  Link?  

Thanks.  =)

Is the silence a 'no'?

---

### Post by lhardyl on 2008-01-30
heya peoples! I'm having the same problem with compiz

after entering 'compiz' in terminal i get this:

```
craig@craig-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4150 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

I'm quite sure ive installed the ATI drivers for my 9600pro, but i could be mistaken

---

### Post by sprichar on 2008-01-30
I have recently browsed through the Ubuntu forums for solutions to why my Gusty install wouldn't enable compiz-fusion or the custom desktop effects. For anyone who is getting this message when trying to enable the custom effects, I have a quick test that depends on your graphics card and drivers but may solve your problem. My issue was solved because my desktop resolution was to high for the custom effects to initialize (1280X800). I simply turned it down to 1024X768 and compiz worked great! I hope this helps someone fix a frustrating problem that took me too long to solve!

---

### Post by jordanubun on 2008-02-02
i to have this problem but when i type this"SKIP_CHECKS=yes compiz" desktop effects are not enabled

---

### Post by joshthejest on 2008-02-03
```
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 178 request_code 156 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)
```


Here is my output.  I'm running an Nivida GeForce 8800 GTS with the restricted drivers enabled.

---

### Post by Rome.konig on 2008-02-03
I had this compiz problem with Gutsy, my way around it was.......

my vid card is  an ati9600xt and the drivers from ati website didnt work form my AMD64
it would give me and error and not won't enable compiz effects.

when i did a fresh install of Gutsy again i left the restricted drivers out and didn't update my video card, 
the fglrx driver that comes installed with Gutsy works fine, although my MatrixGL screen saver would freeze up.
i was able to install Compiz editor to customize the effects.

---

### Post by joshthejest on 2008-02-03
I have run the nvidia-settings to make my dual monitor setup work.  I disabled the second monitor and there was no problem getting it to work, but with the second monitor running the desktop effects do not work.

---

### Post by wilson47 on 2008-02-03
I am having similar problems, but I changed my graphics driver (stupid me) and now I can't get past the command line...

I run 
#compiz#

and I get 

#
Checking for Xgl: xvinfo: Unable to open display not present.
xset: unable to open display ''''
AIEEEEH, no Log file found
xsetL unable to open display ''''

Blacklisted PCIID ;8086:2a02' found
aborting and using fallback: /usr/bin/metacity
Window manager error: Unable to open X disply
#

Thanks in advance............

---

### Post by iamchialike on 2008-02-13
I keep getting "Desktop effects could not be enabled"
Can anyone tell me is my computer even compatible with compiz?
Its a Lenovo y410 and i listed the xorg.conf and compiz outputs below
i'm not sure if this thread is still alive but any help would be wonderful thank you

```
 grep -v ^# /etc/X11/xorg.conf

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "(pitch" "1280)"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800" "(pitch" "1280)"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "(pitch" "1280)"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800" "(pitch" "1280)"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "(pitch" "1280)"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "(pitch" "1280)"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```
compiz says:
```
compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/src/metacity

```

---

### Post by ajie on 2008-02-15
Hi, everyone! I am having a problem too running compiz on my laptop with S3 Twister K video card. I have gutsy installed.

My compiz output is:

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

My compiz skip-check output is:

```
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

output of glxinfo | grep render

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Twister 20061110 AGP 1x x86/MMX+/3DNow!+/SSE

```
and finally, my xorg.conf codes:

```

Section "Device"
	Identifier	"S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
	Boardname	"savage"
	Busid		"PCI:1:0:0"
	Driver		"savage"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP Pavilion M45/S40 Monitor"
	Horizsync	31.468-50.0
	Vertrefresh	56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection


```

Anyone, please help me.

---

### Post by Rome.konig on 2008-02-28
i hope this will help a few people. 
i seen through out this post that most of the people here are having problems with video driver and XGL.

run this in terminal if you don't already have these packages installed
 sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

then do

sudo apt-get install xserver-xgl

then reboot

this worked for me in gutsy.

make sure that you are using fglrx driver. Vesa doesn't work too good for compiz

---

### Post by mtbterain on 2008-04-23
same errors, read and did most of the stuff but can't figure out why compiz isn't enabling.....

---

