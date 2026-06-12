---
title: "Why are Desktop Effects so slow??"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by davem2312 on 2007-09-13
So... I am really not sure if anyone else is having this problem, but here we go.
I have 3 computers, and have done the same thing to all of them.  Install feisty, get graphics drivers the Ubuntu way (Restricted Manager), in some cases with envy, or by myself, but I have tried a number of ways, and then just enable the "Desktop Effects", which I guess is compiz, not compiz-fusion.

Here are my 3 comps.

Dell E1505 with centrino duo, and built in Intel GMA card ca. 2006
Dell Inspiron 9300 with Centrino and NVIDIA GeForce Go 6800 ca. 2005
AMD Athlon 64 X2 6000+ w/ NVIDIA GeForce 8800GTS 320MB

The Intel card runs compiz the best.  Both NVIDIAs are choppy, slow, and just unbearable, and they are both much better cards. (When I say choppy and slow, I mean the minimize effect renders about 6 frames from minimized to maximized and vice versa)  The 8800GTS can handle just about anything at breakneck speed too, except for compiz.  Beryl runs more typically, slower on the intel than the NVIDIA cards.  Oh, and not to bash Ubuntu or anything, but with Fedora 7, compiz desktop effects runs like butter on the NVIDIA 8800GTS.

So here's my question... What is going on?  Am I doing something really stupid.  If anyone has any suggestions, let me know what information you want to know about my hardware, configurations... etc, and I will be glad to post them.  If you have any similar experiences, let me know as well.  Thanks.

---

### Post by me208 on 2007-09-14
I have two computers one with a Nvidia card and one ATI with Ubuntu, and this is my advice to you. Because the Nvidia drivers are proprietary they don't integrate with Ubuntu well. My advice to you would be to turn off those restricted drivers.

---

### Post by FuturePilot on 2007-09-14
> **me208 said:**
> I have two computers one with a Nvidia card and one ATI with Ubuntu, and this is my advice to you. Because the Nvidia drivers are proprietary they don't integrate with Ubuntu well. My advice to you would be to turn off those restricted drivers.

I don't think the fact that they are proprietary has anything to do with this. I have 3 computers all using the Nvidia driver and they run great.

To the OP, you might want to post your xorg.conf file.

---

### Post by Rupertronco on 2007-09-15
> **FuturePilot said:**
> I don't think the fact that they are proprietary has anything to do with this. I have 3 computers all using the Nvidia driver and they run great.

To the OP, you might want to post your xorg.conf file.

Agreed. Definitely post your xorg.conf so we are more able to diagnose the problem. The proprietary drivers work just fine on my 7600gt x2 and 8800 Ultra setups. I also have the family computer with much less power than yours (it's a 6000 series card, although I forget which), running fusion beautifully.

---

### Post by alpin19 on 2007-09-15
At first, let's check your 3D Support by typing in console:
```
glxinfo | grep direct
```

---

### Post by dougfractal on 2007-09-15
I have aNVIDIA GPU GeForce 7100
with aiglx everything is smooth but takes about 1 second to do anything. (Menus, previews....) The delay does my head in.

but with **xserver-xgl**   SMOOTH and responsive.

---

### Post by spikegotti on 2007-09-15
i personally would get rid of compiz, i too had the same problem after a day of using it, so i switched to beryl like a month ago and dont have one regret, everything is swift and makes my peers mac os x and windows systems computers look like slugs.  only prob i encounter with beryl really is that sometimes i may have o reload the beryl which is nothing hard just by two clicks

---

### Post by garthoverman on 2007-09-15
I am also having this same exact problem. Compiz and Compiz Fusion both run pretty badly. I've tried multiple different driver versions, also. I began using Envy to install the drivers, and where the Animations would be smooth, the cube would rotate with a lot of choppiness, and a few other plugins seemed sluggish. So i manually installed nvidia-glx and then after tried nvidia-glx-new, and in both instances, the 
Animations would become really choppy (like the OP described) but then cube would rotate really smoothly.

I'm not at home with access to my xorg.conf file, but I am headed there right now. When I get there I will post it. 

I'm also having difficulty getting Ubuntu to let me render everything at the 60hz refresh rate that my monitor is capable of. I don't think these problems are related, but I think it can also be resolved with some tweaks to my xorg.conf, so I thought I would mention it, too.

My system specs are: 

A64 3500+
1GB RAM
nvidia GF6800GT
LCD monitor, 1920x1200 @ 60Hz

---

### Post by garthoverman on 2007-09-15
Here's my xorg.conf:

> Section "Files"
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
	Identifier	"nVidia Corporation NV40 [GeForce 6800 Series GPU]"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV40 [GeForce 6800 Series GPU]"
	Monitor		"Generic Monitor"
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
		Modes		"1920x1200"	"1024x768"	"800x600"	"640x480"
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

---

### Post by dougfractal on 2007-09-15
use **displayconfig-gtk** to reconfigure your monitor settings

have you tried **xserver-xgl**?

whose CF are you using? (what's your sources.list)

---

### Post by FuturePilot on 2007-09-15
Try adding 
```
Option    "RenderAccel"   "True"
```
To the device section.
Log out and restart X server with Ctrl+Alt+Backspace

---

### Post by leohart on 2007-09-16
I have an Nvidia card (8600M GS) and Compiz Fusion was running sluggishly (despite this being a pretty new computer). After some searching I found out that adding --loose-binding to your /usr/bin/compiz (at the right place) will give you significant speed boost. 

Give it a try.

---

### Post by davem2312 on 2007-09-16
Well, OP here....  I am currently running the development branch of Gutsy (32-bit version) on my AMD 64 X2 6000+ with NVIDIA 8800 GTS.  So I guess I am not really looking for any fixes, or too much of that sort, I have most likely already tried what you are going to tell me.  Recently, I found another post that said to start compiz with this...

```
__GL_YIELD="NOTHING" compiz --replace --loose-binding

```

So I did that, and it is considerably better, but not as good as you might think... considering I have hardware that should be able to dominate anything else on the consumer market.  Well, for anyone who is wondering, I will update any info anyone asks about my 3 systems as noted in the original post.  
```

david@Max:~$ glxinfo | grep direct
direct rendering: Yes
```

Well, that works, and so does this, but only when compiz is not running.
```

david@Max:~$ glxgears
91535 frames in 5.0 seconds = 18306.978 FPS
100435 frames in 5.0 seconds = 20086.988 FPS
100356 frames in 5.0 seconds = 20071.165 FPS
100416 frames in 5.0 seconds = 20082.461 FPS
95173 frames in 5.0 seconds = 19034.135 FPS
102970 frames in 5.0 seconds = 20593.955 FPS

```

Here is my xorg.conf courtesy of Gutsy's new restricted manager, but keep in mind that I have tried these things on Feisty, with restricted manager, install by hand, and with envy.

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
	Load		"dbe"
	Load		"dri"
	Load		"glx"
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

Section "Device"
	Identifier	"Failsafe Device"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	16
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
```

I will note that this is one of the strangest xorg.conf files I have seen, mostly because it doesn't contain my screen resolution... which is 1920x1200.  Feel free to suggest, but as I said before, I have probably tried it already.  Thank you.

---

### Post by FuturePilot on 2007-09-17
I'd say it's strange alright. I think it's because you're running it in Failsafe mode or something.  I think that's why it's running so slow. Quote from xorg.conf
[QUOTE=xorg.conf]# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg[/QUOTE]
I think you need to do
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by davem2312 on 2007-09-17
Right, well, I was running in failsafe mode, and then I just clicked enable restricted driver to try out the gutsy stuff, and then I got 1920x1200, with no glx, so then I enabled the modules to load glx etc.  But, here goes the reconfigure... get back to you in a second.

---

### Post by FuturePilot on 2007-09-17
Make sure you restart X afterwards. Log out and press Ctrl+Alt+Backspace.

---

### Post by davem2312 on 2007-09-17
Ran dpkg-reconfigure... then restarted the X server, and it broke.  Booted into recovery, and moved old xorg.conf back.  Here is what dpkg-reconfigure did.

All dpkg-reconfigure did was ask me what resolution I ran.  Shall we give nvidia-xconfig a go?

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
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:0:18:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200"
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
EndSection
```

---

### Post by FuturePilot on 2007-09-17
Hmm. It should have asked you what driver you want to use. The reason it broke is because it used the "nv" driver doesn't support your card as of now. nvidia-xconfig might be worth a shot. If it doesn't work let's just tweak the config file you just posted, shall we?;)
Add this towards the beginning
```
Section "Module"
	Load		"dbe"
	Load		"dri"
	Load		"glx"
	Load		"vbe"
EndSection
```
Replace 
```
Driver		"nv"
```
under the Device section with this
```
Driver             "nvidia"
```
And also add these as well to the device section
```
Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
          Option          "RenderAccel"     "True"
```
And add this to the very bottom
```
Section "DRI"
	Mode	0666
EndSection
```

---

### Post by davem2312 on 2007-09-17
Here is what nvidia-xconfig gave me.  I had to edit the resolution... but thats it.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "glx"
    Load           "vbe"
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

Section "Monitor"
    Identifier     "Failsafe Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "800x600"
    EndSubSection
EndSection
```


However, now, whenever I Ctrl+Alt+Backspace to restart the X server, A blank screen shows, and it never reloads, I must restart my computer with the switch.

---

### Post by joshuachad on 2007-09-17
i had the same issue and i googled a page in espanol and they told me to enable backports cuz there was a patch pushed out that fixed the issue. Not sure if there is any relation here since i am using Gutsy. at any rate if you have something to tranlate the page here it is:[http://ubox.wordpress.com/2007/06/21/installare-compiz-fusion-tramite-script/](http://ubox.wordpress.com/2007/06/21/installare-compiz-fusion-tramite-script/)

also there is an aswesome script there that compiles compiz fusion from source. worked absolutley awesome for me. I never had compiz run so well.

Cheers.

---

### Post by FuturePilot on 2007-09-17
Hmm. Let's go back to this one
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
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:0:18:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200"
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
EndSection
```
And add in the stuff from my post above.

---

### Post by davem2312 on 2007-09-17
I edited it as such, and it also did not work.  Sorry...

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
	Load		"dbe"
	Load		"dri"
	Load		"glx"
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
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:0:18:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
        Option          "RenderAccel"     "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200"
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
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by FuturePilot on 2007-09-17
Don't be sorry, I should be sorry, because as of now, I'm out of ideas:redface:
Maybe if I sleep on it, I'll think of something.

---

### Post by zero244 on 2007-09-17
On my Edgy machine I run Beryl with XGL and it runs faster than running it will aiglx. I have a 7600 nvidia card.
Beryl runs very smooth, fast and stable. I have most of the features turned on.

---

### Post by dougfractal on 2007-09-17
I agree with zero244
I have a vanilla gutsy 7100 nvidia
XGL and it runs faster than running it will aiglx.
Compiz Fusion runs very smooth, fast and stable. I have most of the features turned on.

Does anybody else find xserver-xgl  better?

---

### Post by DarthTibault on 2008-01-22
> **dougfractal said:**
> Does anybody else find xserver-xgl  better?
OMG, I wish I could KISS you!
I never knew about xserver-xgl, I just installed it... everything is suddenly SO FRIGGIN FAST!
Thx again, you made my day :D

---

