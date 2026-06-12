---
title: "cant enable compiz- fusion"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by light-angel on 2007-12-29
i have a DELL DIMENSION 3100 with a intel 915i video card, i'm using ubuntu gutsy.
For some reason i cant enable compiz-fusion efects. when i go to System > preferences > Appeareance > Visual Effects and try to enable compiz-fusion some message apperas telling me "cant enable visual efects"

i know its not the pc because i used to have it installed, one day i stared the computer and it didn't load :S

---

### Post by Sef on 2007-12-29
Have you installed the restricted drivers?  System > Administration > Restricted Drivers Manager

---

### Post by light-angel on 2007-12-30
i did it, and it says that i have all the drivers installed. but i know its not that because i used it have it before with the same install, one day it just stops working!

---

### Post by Forlong on 2007-12-30
There are no restricted drivers for intel chips because they are open source and therefore shipped by default in Ubuntu.

What's the output of ```
compiz
``` in a terminal?

---

### Post by TolTime on 2007-12-30
I am Having the exact same problem and the output I'm getting is this

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format





don't mean to Tread hack, if i am disregard.

---

### Post by Forlong on 2007-12-30
> **TolTime said:**
> I am Having the exact same problem
Really? Do you get "cant enable visual efects" when trying to enable compiz-fusion in System > preferences > Appeareance > Visual Effects like the OP said?

---

### Post by TolTime on 2007-12-30
i don't know what i did but now it works, I'm so confused. 
i used ubuntu Tweak, before compiz that might have been the sources of my problem.
i had not been able to get the extra effects to work at all, but now everything is working fine

---

### Post by Forlong on 2007-12-30
Great. :)
I thought so, because the output gave no error-message whatsoever.

---

### Post by TolTime on 2007-12-30
well last night all i got was that error, i just guess i fixed it without knowing it.

---

### Post by light-angel on 2007-12-30
i still cant resolve my problem...
how do i get the terminal output of compiz-fusion?

---

### Post by Forlong on 2007-12-31
Like I said, just put ```
compiz
``` in a terminal.

---

### Post by Dropknee on 2007-12-31
This is my output:

```
dropknee@Drop-Ubuntu-PC:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4a50 (prog-if 00 [VGA])
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

pls help

---

### Post by light-angel on 2008-01-02
this is my output
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

but i dont know why, because 2 weeks ago it worked fine with the same installation plus when i go to the restrictive drivers managers there's no new driver available :confused:

---

### Post by solemnavalanche on 2008-01-04
> **light-angel said:**
> this is my output
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

but i dont know why, because 2 weeks ago it worked fine with the same installation plus when i go to the restrictive drivers managers there's no new driver available :confused:

Are you running a 64 bit installation? I had the same problem, and found that the compiz script is slightly broken on 64 bit machines. It looks for /usr/lib/xorg/..etc instead of /usr/lib64/xorg/... in the logfile. Try opening /usr/bin/compiz in a text editor and changing this line:

XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

to this:

XORG_DRIVER_PATH="/usr/lib64/xorg/modules/drivers/+"

---

### Post by Dojan5 on 2008-01-04
> **light-angel said:**
> this is my output
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

but i dont know why, because 2 weeks ago it worked fine with the same installation plus when i go to the restrictive drivers managers there's no new driver available :confused:

Thats exactly what i get, but according to forlong i cant run Compiz fusion...
I hope its not that it means :S

---

### Post by Forlong on 2008-01-06
light-angel: try running Compiz like this:
```
SKIP_CHECKS=yes compiz
```


Dropknee: you need to tell us more about your setup. Mainly what graphics card and driver.

---

### Post by light-angel on 2008-01-07
this is what i get after typing :SKIP_CHECKS=yes compiz
```

light-angel@Heaven:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
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

i have a DELL DIMENSION e310 without modifications
i'm not pretty sure, but i think my video card is Intel i915

---

### Post by SoDanishWasLike on 2008-01-07
I am having the same problems - I cannot turn on Compiz effects in the Appearance window. I am running a 32MB ATI Mobility Radeon 9200 with a 1.7 GHz Pentium M and 1 GB RAM

```
danish@danish-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5c61 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by Ub1476 on 2008-01-07
> **light-angel said:**
> this is what i get after typing :SKIP_CHECKS=yes compiz
```

light-angel@Heaven:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
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

i have a DELL DIMENSION e310 without modifications
i'm not pretty sure, but i think my video card is Intel i915

Post the output of:

```
lspci | grep VGA

glxinfo | grep render
```

> **SoDanishWasLike said:**
> I am having the same problems - I cannot turn on Compiz effects in the Appearance window. I am running a 32MB ATI Mobility Radeon 9200 with a 1.7 GHz Pentium M and 1 GB RAM

```
danish@danish-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5c61 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

```

Look [here]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200").

---

### Post by light-angel on 2008-01-16
this is the output you ask me for:

```

light-angel@Heaven:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
light-angel@Heaven:~$ 
light-angel@Heaven:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
light-angel@Heaven:~$ 

```

---

### Post by Ub1476 on 2008-01-22
Direct rendering is no, which means that you have no 3D. Have you made sure you are using the Intel i810 driver? 

System>Preferences/Amin>Screens and graphics

You can also post your xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by light-angel on 2008-01-24
this is the output:
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
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"800x600@60"	"1024x768@60"	"800x600@56"	"640x480@60"
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

---

### Post by Ub1476 on 2008-01-25
You are currently using the vesa driver which do not support desktop effects. You need to change it to i810 (as I said above). You can do this by editing your xorg.conf or read my above post.

---

### Post by rosegarden78 on 2008-01-25
As far as I know you need ALL the packages from Synaptic that have 'compiz' in the name and description.  Except one package will ask you to remove compiz.  Do not install this one package all the others including compiz-kde and compiz-kicker.But it only worked for me on a fresh install of Ubuntu GG 7.10 on an Intel 915 mobile Dell Inspiron 1200.  Then press Alt-F2 type compiz to restart.

Check [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981") for instructions.

---

### Post by _Phineas_ on 2008-01-26
I have the same Problem.Same computer Dimension E310 but with an,ATI X1550.
I have Tried just about everything to get compiz to work.I guess ill wait until I get a new computer.

---

### Post by Weidbrewer on 2008-03-24
> **rosegarden78 said:**
> As far as I know you need ALL the packages from Synaptic that have 'compiz' in the name and description.  Except one package will ask you to remove compiz.  Do not install this one package all the others including compiz-kde and compiz-kicker.But it only worked for me on a fresh install of Ubuntu GG 7.10 on an Intel 915 mobile Dell Inspiron 1200.  Then press Alt-F2 type compiz to restart.

Check [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981") for instructions.

Although not technically a fresh install, mine is only a few days old.   I have the same laptop you have specified, and installed all packages you mentioned...No luck.  Below is my output when I try to run Compiz.   Any suggestions?

```
weidbrewer@********:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by SoDanishWasLike on 2008-04-08
> **Ub1476 said:**
> 
Look [here]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200").



I tried this, and it still doesn't work for me. When I try to enable Compiz-Fusion, it simply tells me that it couldn't be enabled

---

### Post by Forlong on 2008-04-08
What's the output of ```
compiz
``` in a terminal?

---

### Post by +++ IGOR +++ on 2008-04-08
@light-angel:

To get the terminal output you just open up a terminal window and then type:

compiz

This will attempt to start compiz. If you copy/paste the output from that to this thread we might be able to see what's the matter with your machine.

---

### Post by Weidbrewer on 2008-04-08
Forlong...not sure if your request was directed at me or not, but my output is listed in my post above.   Any suggestions?

---

