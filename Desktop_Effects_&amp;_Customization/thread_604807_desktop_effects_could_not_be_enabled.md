---
title: "desktop effects could not be enabled"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by robjoski on 2007-11-06
Hi everyone!

I've been trying to get desktop effects working on my laptop, but nothing I do seems to work. I enabled DRI and AIGLX in my xorg.conf; and they are both supposedly working (i.e. no errors or crashing). lspci says I have the "ATI Technologies Inc 3D Rage LT Pro AGP-133" graphics card...
My xorg.conf:
```
Section "Module"
        Load    "dbe"
        Load    "dri"
        Load    "glx"
EndSection

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
	Identifier	"ATI Technologies Inc 3D Rage LT Pro AGP-133"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"
	Option		"AllowGLXWithComposite" "true"
	Option		"backingstore"	"true"
	Option		"DRI"	"true"
	Option		"BusType"	"PCI"
	VideoRam	32768
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc 3D Rage LT Pro AGP-133"
	Monitor		"Generic Monitor"
	DefaultDepth	16
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite"	"1"
EndSection

Section "ServerLayout"
	Option		"AIGLX"		"true"
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
```
Just in case anyone is wondering, I *did* look at the five other threads with the same title; 
none of them helped though.
Thanks in advance!

Robert

---

### Post by creeco on 2007-11-06
Witch version of ubuntu do you use?

---

### Post by Forlong on 2007-11-06
Post the output of ```
compiz
``` in a terminal.

---

### Post by robjoski on 2007-11-06
I use Ubuntu 7.10 (gutsy).
By the way, I have been messing around, and I think DRI is disabled now (I'm trying to get it back)...
```
robert@lappy:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c42 (rev dc) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by 5h4rk on 2007-11-08
I have the same problem, is it because of the XGL?

> Checking for Xgl: not present. 

My card is a Intel 945.

---

### Post by Forlong on 2007-11-09
What's the output of
```
glxinfo | grep "direct rendering"
```


@5h4rk: no, with an intel chip, you shouldn't need Xgl.

---

### Post by 5h4rk on 2007-11-09
> **Forlong said:**
> What's the output of
```
glxinfo | grep "direct rendering"
```


@5h4rk: no, with an intel chip, you shouldn't need Xgl.


chad@laptop:~$ glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
chad@laptop:~$

---

### Post by ricanelite on 2007-11-09
is the Restricted Drivers Enabled? As for the Graphics Card? Cause I had a similar problem and when I went Admin>Restricted Drivers I enabled my Graphics card and it installed and updated. Rebooted my system and it worked. Check that out.

---

### Post by 5h4rk on 2007-11-09
> **ricanelite said:**
> is the Restricted Drivers Enabled? As for the Graphics Card? Cause I had a similar problem and when I went Admin>Restricted Drivers I enabled my Graphics card and it installed and updated. Rebooted my system and it worked. Check that out.

I only have my Wireless card drivers there:

[IMG]http://img101.imageshack.us/img101/6770/screenshotbp0.png[/IMG]

:S

---

### Post by jslmg on 2007-11-09
5h4rk, I've got the same problem as you! And it only started tonight. I followed Forlong's procedure, and I got exactly the same output as you did, including the "no XGL" notice. However, in my Restricted Drivers manager, I see only Atheros Hardware Access Layer (HAL), and no others (I'm on an Intel Mac mini).

This problem resulted, or seems to have resulted, from changes made while trying to get wireless mouse and keyboard to work. I was using Compiz successfully until that.

 See this thread, scroll down to the last message, which is mine:
[http://ubuntuforums.org/showthread.php?t=574631&highlight=Mighty+Mouse](http://ubuntuforums.org/showthread.php?t=574631&highlight=Mighty+Mouse)

Would you please let me know if you find a solution, getting compiz started again?

---

### Post by jslmg on 2007-11-09
OK, I ran  compiz --replace

and this was the output:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

So, how would I get that driver back? I wonder how it disappeared in the first place!

---

### Post by jslmg on 2007-11-09
Update: 

I decided to install xgl, to see if that would solve anything. After installation, I rebooted, but I still got the same output in terminal:

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by twizler on 2007-11-09
YO 
Type this in the terminal -- 
it skips the whitelist. 
:KS

> 
SKIP_CHECKS=yes compiz

---

### Post by jslmg on 2007-11-09
Thanks, twizler. The problem has been solved in another thread: [http://ubuntuforums.org/showthread.php?p=3740570&posted=1#post3740570](http://ubuntuforums.org/showthread.php?p=3740570&posted=1#post3740570)

It turns out that I'd replaced my original xorg.conf file with one that called on VESA video. I had to download a new xorg.conf. This happened while I was trying different things to get the Mighty Mouse working in Ubuntu on my Mac mini.

---

### Post by 007_b0nd3 on 2007-11-10
so pissed. my graphics card supports compiz because i was using all the effects on Fedora 7 and stuff. I wanted to go with Ubuntu because I heard it was better. I have an ATI Radeon 9500 256 MB graphics card. I tried enabling restricted drivers it says my hardware does not need any restricted drivers. I cant even enable simple desktop effects? is this some kind of stupid bug with Ubuntu? And for the experts with Linux that read this message, throw ideas at me of things I could do because I am a little new to this.

---

### Post by Forlong on 2007-11-10
What's the output of ```
compiz
``` in a terminal?

---

### Post by abds on 2007-11-10
Hi

I am having the same problem. I have an ATI Radeon X200.

Output of "fglrxinfo":

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release


Output of "glxinfo | grep "direct rendering"":

direct rendering: Yes

Output of "compiz"

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Any suggestions on what I should do? Any help would be appreciated!

---

### Post by robjoski on 2007-11-10
5h4rk - Your XGL error probably isn't the problem.
I tried XGL, but it crashed on me... So I tried AIGLX.
I don't know if it works or not (It's not giving me any errors - ?)
Anyway, Compiz is not working yet. [Well, on lappy - I got it to work on my Pentium II desktop... Why can't it work on Lappy? Oh, that's right. Lappy has an even slower
processor and less memory. Duh.]

I should just get a Macbook... *sigh*

---

### Post by jslmg on 2007-11-10
> 5h4rk - Your XGL error probably isn't the problem.
I tried XGL, but it crashed on me... So I tried AIGLX.
I don't know if it works or not (It's not giving me any errors - ?)
Anyway, Compiz is not working yet.

That's right. If you've got an Intel machine, XGL is not necessary, and your installation won't be recognized.

5h4ark: Have you got compiz-config installed? That's the first question we should ask. Everything starts with compiz-config. Without it, you can have compiz running, but never be able to do anything with it.

---

### Post by 5h4rk on 2007-11-10
> **jslmg said:**
> That's right. If you've got an Intel machine, XGL is not necessary, and your installation won't be recognized.

5h4ark: Have you got compiz-config installed? That's the first question we should ask. Everything starts with compiz-config. Without it, you can have compiz running, but never be able to do anything with it.

EDited:

Yes, I did:

sudo apt-get install emerald compizconfig-settings-manager

---

### Post by jslmg on 2007-11-10
OK. Compiz-config is a package that will give a front-end GUI to manage the settings for compiz. After you install it, you'll have "Advanced Desktop Effects Settings" in your System-->Preferences.

To get it, (1) go to System-->Administration-->Synaptic Package Manager. 

(2) Click the "Search" button, then type "compiz-config" in the text field there.

(3) When you see "compiz-config" in the list, click the box on the left.

(4) You'll get another window confirming that you want to "mark" it for installation. After you confirm, click "Apply" in the tool bar at top.

(5)Just let Synaptic finish its task--it's all automatic.

When it's done, check the System-->Preferences to make sure "Advanced Desktop Effects Settings" is there.

Then, we'll go on from there.

---

### Post by jslmg on 2007-11-11
Oh, sorry! Our messages crossed...

Is the Advanced Desktop Effects Settings in your preferences?

If so, did you open a terminal and type 

```
compiz --replace
``` ?

i did not install compiz-config through the emerald command, but with Synaptic.

---

### Post by 5h4rk on 2007-11-11
> **jslmg said:**
> Oh, sorry! Our messages crossed...

Is the Advanced Desktop Effects Settings in your preferences?

If so, did you open a terminal and type 

```
compiz --replace
``` ?

i did not install compiz-config through the emerald command, but with Synaptic.

chad@laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2960x1050) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

[1]+  Stopped                 compiz --replace
chad@laptop:~$

---

### Post by abds on 2007-11-11
Hi

I am having the same problem. I have an ATI Radeon X200.

Output of "fglrxinfo":

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release


Output of "glxinfo | grep "direct rendering"":

direct rendering: Yes

Output of "compiz"

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Any suggestions on what I should do? Any help would be appreciated!

---

### Post by abds on 2007-11-12
anyone??

---

### Post by Forlong on 2007-11-12
Se the last step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support).

---

### Post by abds on 2007-11-12
That worked. Thanks a lot!

---

### Post by K-Man_22 on 2007-11-15
> **abds said:**
> Hi
Output of "fglrxinfo":

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6958 Release


Output of "glxinfo | grep "direct rendering"":

direct rendering: Yes

Output of "compiz"

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Any suggestions on what I should do? Any help would be appreciated!

I know, this one is solved for you, but just for the record since I had the very same constellation and got it to run only after an extensive web search, find my steps in this [WIKI]("http://wiki.ubuntuusers.de/Compiz/Problembehebung"). One has to modify the whitelist of drivers in the compiz config and the xorg.conf as stated there in order to enable AIGLX.

---

### Post by 5h4rk on 2007-11-17
I still can't make it work =(
> 
chad@laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2960x1050) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

[1]+  Stopped                 compiz
chad@laptop:~$ 

> chad@laptop:~$ more /etc/X11/xorg.conf
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
        Load            "glx"
        Load            "GLcore"
        Load            "dri"
        Load            "v4l"
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "Intel 945"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
        Option          "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x800"
        Horizsync       31.5-50.0
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsyn
c
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsyn
c
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsyn
c
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1280    800
                Modes           "1280x800@60"   "1280x720@60"   "1280x768@60"
"800x600@60"    "800x600@56"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" leftof "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "device" #             
        Identifier      "device1"
        Boardname       "Intel 945"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  1
        Vendorname      "Intel"
        Option          "MonitorLayout" "CRT,LFP"
EndSection
Section "screen" #             
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "1680x1050@60"  "1600x1024@60"  "1440x900@60"
"1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "800x600@56"
        EndSubSection
EndSection
Section "monitor" #             
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1680x1050"
        Horizsync       31.5-65.5
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsyn
c
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsyn
c
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsyn
c
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsy
nc
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync
 +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync
 +vsync
        Gamma   1.0
EndSection
Section "ServerFlags"
        Option          "Xinerama"      "true"
EndSection
chad@laptop:~$ 


I haven't touched the xorg.conf, I only configured it from "Screen and Graphics".

---

### Post by mrmiserable on 2007-11-17
5H4RK

it appears you are using dual screens if so compiz will only render to 2048

---

### Post by 5h4rk on 2007-11-17
> **mrmiserable said:**
> 5H4RK

it appears you are using dual screens if so compiz will only render to 2048

Yes I'm on dual screens, but the biggest one's resolution is only 1680x1050.

---

### Post by mrmiserable on 2007-11-17
ok done dual screen the other day had same problem

just put 2048x1024 in screen section of xorg.conf

then when you reboot goto  preferences/screen resolution and change to that resolution and compiz should work

fingers and everything crossed

---

### Post by 5h4rk on 2007-11-17
> **mrmiserable said:**
> ok done dual screen the other day had same problem

just put 2048x1024 in screen section of xorg.conf

then when you reboot goto  preferences/screen resolution and change to that resolution and compiz should work

fingers and everything crossed

You mean change the resolution of my LCD to 2048x1024? The thing is that my screen supports up to 1680x1050, and it's its native resolution which I want to keep :(

---

### Post by mrmiserable on 2007-11-17
just add this to /etc/X11/xorg.conf 


Modes "1680x1050@60" "1600x1024@60" "1440x900@60"
"1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"

Modes "2048x1024"  "1680x1050@60" "1600x1024@60" "1440x900@60"
"1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"

i hope this works its 4 o'clock here in feezing france

---

### Post by 5h4rk on 2007-11-17
Nop, it doesn't work.

> chad@laptop:~$ sudo gedit /etc/X11/xorg.conf
...
Comparing resolution (2960x1050) to maximum 3D texture size (2048): Failed.
...


Why "2960x1050" is there? I don't have that anywhere in my xorg.conf 

:(

Thanks

---

### Post by mrmiserable on 2007-11-17
did you reboot and change resolution in system/preferences/screen resolution

my xorg looks like this
not to sure with intel graphic cards 


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
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
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
	Option	    "XkbLayout" "fr"
	Option	    "XkbVariant" "oss"
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
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "second Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 80.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "true"
	Option	    "AllowGLXWithComposite" "true"
	Option	    "AccelMethod" "XAA"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1024x1024+1024x1024,0x0+0x0"
	Option	    "EnableMonitor" "tmds1,crt1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "2048x1024" "1280x1024" "1024x768"
	EndSubSection
EndSection

---

### Post by mrmiserable on 2007-11-17
sorry in response to your question it is the combined resolution of both your screens

ie Comparing resolution (2960x1050) to maximum 3D texture size (204: Failed.

you need to lower the total resolution for compiz to work

---

### Post by 5h4rk on 2007-11-17
Maybe my dual screens is not configured correctly, maybe I should make it work with one screen first.

---

### Post by mrmiserable on 2007-11-17
does dual screen function ok

my ati card was giving me the same headache as you ie to high resolution for compiz but after changing this in gnome settings it worked fine 

anyway good luck

---

### Post by mrmiserable on 2007-11-17
just saw this maybe for you this will work 

[http://www.shawnc.org/2007/10/30/ubuntu-gutsy-upgrade-dual-head-monitors-now-working/](http://www.shawnc.org/2007/10/30/ubuntu-gutsy-upgrade-dual-head-monitors-now-working/)

---

