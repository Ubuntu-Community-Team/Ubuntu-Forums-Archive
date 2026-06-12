---
title: "Nvidia dual screens and beryl"
date: 2007-05-01
forum: Desktop Effects &amp; Customization
---

### Post by Muntted on 2007-05-01
I have recently gotten another monitor and configured the dual monitors via the wonderful *nvidia-settings* command.

However with the dual monitors beryl refuses to work. Is this a known issue? What diagnostic data would you guys like?

Cheers
Matt

---

### Post by rolf-c on 2007-05-01
Maybe this will help:

```
Beryl is incompatible with Xinerama (multiple monitors bonded together to create a larger desktop). Beryl requires the XRandR extension, and Xinerama disables it. Beryl is compatible with Twinview, a nVidia-only feature similar to the hardware-neutral Xinerama.
```

From [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

I do not have a dual setup so am not really any substantial help at all.

---

### Post by unabatedshagie on 2007-05-01
I'm using beryl just now with dual screens

All I did to get it working was to **sudo nvidia-settings** in a terminal and configure the other monitor then saved the xorg.conf file and it worked.

---

### Post by Muntted on 2007-05-01
There seems to be 3 types of setup for it. Xinerama, Twinview and seperate moniters. Im on the seperate monitors one because im using a 22" Widescreen with a 17" Normal.

---

### Post by unabatedshagie on 2007-05-01
You should be able to use twinview with different resolution monitors, I'm sure thats what mine was set to when I had two different res monitors.

---

### Post by rhennigan on 2007-05-01
Be sure that both screens are set to 24 bit color.  I had this same problem and realized that it had set both screens to 16 bit when I enabled twinview.

---

### Post by aajvs99 on 2007-05-01
Use twinview it works excellent. 
run ```
sudo nvidia-settings
```
set the monitors up how you want and save the xorg.conf file then ```
sudo gedit /etc/X11/xorg.conf
``` 
and add ```
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
```  to the screen section

---

### Post by zaf on 2007-05-02
> **Muntted said:**
> There seems to be 3 types of setup for it. Xinerama, Twinview and seperate moniters. Im on the seperate monitors one because im using a 22" Widescreen with a 17" Normal.
Using seperate monitors means that OpenGL acceleration won't work on one of the monitors. As the others have said, use TwinView. It works.

---

### Post by whoeva on 2007-05-02
After following tselliots guide on setting up the TV I can use the display on my TV but only when I disable beryl or desktop effects. With either of these settings enabled I can see the desktop and mouse on the TV screen but I cannot click anything.

I tried altering the nvidia settings to set the screens up as outlined above but get the following error when I try to save the Xorg.conf

ERROR: Unable to determine valid vertical refresh ranges for display device
       'TV-0' (GPU: GeForce 6800 GT)!


ERROR: Failed to add display device 'TV-0' to screen 0!


ERROR: Failed to add X screen 0 to X config.


ERROR: Failed to add X screens to X config.



ERROR: Failed to generate an X config file!

I am using a fairly old PAL TV connected via S-Video out on my nvidia 6800GS that goes into a scart connection on the TV. Here is my Xorg.conf if somebody would please look it over and offer any suggestions as to what is wrong.
Thanx.

```
Section "ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" Above "Screen[0]"
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
EndSection

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

Section "Monitor"
 #CRT
    Identifier     "Monitor[0]"
    HorizSync       31.5 - 69.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
 #TV 
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #adjust using 'lspci' or cat /proc/pci 
    Identifier     "Device[1]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option          "DisableGLXRootClipping" "True"
	Option		"NoLogo"	"True"
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "Composite" #or SVIDEO etc 
    Option         "TVStandard" "PAL-I" #or NTSC etc 
    Option         "ConnectedMonitor" "Monitor[1]"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_50"
    EndSubSection
EndSection
Section "DRI"
	Mode	0666
EndSection
```

---

### Post by richyrichuk on 2007-05-14
i have a simlar problem with my acer laptop, has any 1 any ideas please?????

---

### Post by celsdogg on 2007-05-15
i am also having a similar problem.

my dual monitors work fine using the Metacity (gnome) window manager. when i switch to beryl, only my primary monitor works correctly. the second monitor shows black at boot, but if i switch to metacity it shows the desktop and i can use it. switch it back to beryl, and it does not work. the desktop is there, but i cant interact with it on the second monitor.

i have a nVidia GeForce 6600. the Primary monitor is a Samsung SyncMaster 941bw widescreen (1440x900). The secondary monitor is an AOpen F95GS (1280x1024). of course, both are lcd's. the Samsung is using DVI, the AOpen is using 15 pin d-sub.

i have tried all sorts of different things and nothing seems to make a difference.

i have tried twinview, but it always seems to be spanning both displays. right now im using seperate X screens.

---

### Post by re5et on 2007-05-16
i have everything running working with twin view, but unfortunately, this kinda ruins my ability to play WoW.  anyone have it working with separate X's? :confused:

---

### Post by celsdogg on 2007-05-16
^^^ thats what i am trying to do!

---

### Post by Soybean on 2007-05-16
If I'm understanding you guys correctly, celsdogg and re5et, what you're looking for is a "multiscreen" configuration as described here: [http://forum.beryl-project.org/viewtopic.php?f=34&t=3408](http://forum.beryl-project.org/viewtopic.php?f=34&t=3408)

The summary being that it's something they're currently working on in the SVN version of Beryl. If you're feeling particularly adventurous, that thread should get you started. :)

---

### Post by re5et on 2007-05-16
i am always down for screwing stuff up so badly that i have to start over :KS

---

### Post by celsdogg on 2007-05-17
ah, so they are currently working on it.

thanks for that thread! :)

---

### Post by mist_01 on 2007-09-03
> **aajvs99 said:**
> Use twinview it works excellent. 
run ```
sudo nvidia-settings
```
set the monitors up how you want and save the xorg.conf file then ```
sudo gedit /etc/X11/xorg.conf
``` 
and add ```
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
```  to the screen section

When i was trying to hook up my monitors with twinview i was having resolution issues and it was crashing.  I found that removing all the other meta modes (at least i think that is what they were called. In any case under advanced or in your xconf file) fixed the problem. Just thought I would share in case someone else is having the same problem.

---

