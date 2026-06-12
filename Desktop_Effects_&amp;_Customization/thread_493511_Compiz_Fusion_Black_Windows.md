---
title: "Compiz Fusion Black Windows"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by Alex&amp;Linux on 2007-07-05
Hey all
Ive been experiencing the black window bug (caused by currently available Nvidia driver) while using Compiz Fusion window manager.

This was avoided in the past by changing the rendering path from texture from pixmap, to copy.

At the moment, all that can be done as far as I know is the reloading of the manager, which has obvious limitations, and its annoying.

Is anyone aware of a way to change this with Fusion, any other suggestions?

---

### Post by kansei on 2007-07-06
Yeah this was a lot easier to resolve in Beryl. I know there were a handful of changes I made to my xorg.conf that fully remedied the problem.

```
Section "Module"
    Load "dri"
    Load "vbe"
    Load "glx"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
#    Option         "AddARGBVisuals" "True"
    Option "AllowGLXWithComposite" "True"
    Option         "NoLogo" "False"
    Option         "AddARGBGLXVisuals" "True"
    Option      "TripleBuffer" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "DRI"
 Mode 0666
EndSection

Section "Extensions"
 Option "Composite" "Enable"
 Option "RENDER" "Enable"
EndSection



```

There's still something missing though. I should have backed up my xorg.conf before I switched from Feisty to Gutsy..

---

### Post by Alex&amp;Linux on 2007-07-06
Hey, thanks for the reply!

Could you clarify the changes you have found effective?
I wasnt aware that a fix was available via altering x, thinking that the solution must come from Nvidia or through the window manager!

Thanks for your time!

---

### Post by kansei on 2007-07-06
> **Alex&Linux said:**
> Hey, thanks for the reply!

Could you clarify the changes you have found effective?
I wasnt aware that a fix was available via altering x, thinking that the solution must come from Nvidia or through the window manager!

Thanks for your time!

There are some specific nvidia driver tweaks that totally fixed the problem for me.. the only weird thing was that occasionally the screen would flicker (as if purging graphics memory or something). That was on feisty though, so far I haven't been able to get it to that same state on gutsy.

---

### Post by Alex&amp;Linux on 2007-07-07
Well, could you possibly be more explicative?

---

### Post by kansei on 2007-07-08
Ok a full day later I haven't seen any black windows since my last changes.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    Option         "AIGLX" "true"
EndSection

Section "Files"
EndSection

Section "Module"
    Load "dri"
#    Load "vbe"
    Load           "glx"
EndSection

```

```
Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
    Option         "DRI" "true"
    Option         "XAANoOffscreenPixmaps" "true"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo" "False"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "DRI"
 Mode 0666
EndSection

Section "Extensions"
 Option "Composite" "Enable"
 Option "RENDER" "Enable"
EndSection

```

I *think* adding the backingstore option along with nooffscreenpixmaps were the last modifications I made to it before it started 'working'. Occasionally I see the contents of my firefox (or other but 99% of the time firefox is the maximized and active window for me) window flicker (quickly, barely noticeable). It's the behavior I had experienced in Feisty when I had actually fixed the black window problem.

---

### Post by Alex&amp;Linux on 2007-07-08
Thank you for the further information.
I have tried adding:

 ```
        Option          "XAANoOffscreenPixmaps" "true"
                   Option          "backingstore"          "true"
```

to no avail!
I noticed you were using AIGLX, and have seen some people reporting this as a fix. However, this didnt seem to help with beryl, while changing the rendering path did.

I'll post up my xorg.conf for anyone to take a look at if its useful.

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
	Identifier	"nVidia Corporation C51 [GeForce 6150 LE]"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
        Option          "XAANoOffscreenPixmaps" "true"
        Option          "backingstore"          "true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
```

---

### Post by kansei on 2007-07-08
Gosh I really wish I knew what options actually fixed something, all I can tell you is that it's totally working. Some other things that I noticed are different is that I have 'addargbglxvisuals' in my Screen section, not the device section, and also I have the DRI and Extensions sections at the end (both of which were added in my quest).

Make a backup of your xorg.conf (cp /etc/X11/xorg.conf /home/YOUR_USER/xorg.conf) and I can give you the 'whole thing' of my xorg.conf (though most of it is already here) to play around with.

I should probably file a bug report or post my information to one but this is an nvidia bug.. what I have working is at best a workaround, a crappy one at that (the flickering isn't obtrusive but it still would be nice if it didn't do that).

either way, it's still better than my thinkpad (ATI Radeon 9600pro) that can't do compiz-fusion at all..

---

### Post by Alex&amp;Linux on 2007-07-09
Hey, thanks a lot for your help, much appreciated!

Ive not yet had to deal with X11 problems, so my experience with restoring from hosed settings, or starting it from command line!
Ive already a backup, would it be as simple as 
 
 cp /home/[user]/xorg.conf backup /etc/X11/xorg.conf ?

---

### Post by kansei on 2007-07-09
> **Alex&Linux said:**
> Hey, thanks a lot for your help, much appreciated!

Ive not yet had to deal with X11 problems, so my experience with restoring from hosed settings, or starting it from command line!
Ive already a backup, would it be as simple as 
 
 cp /home/[user]/xorg.conf backup /etc/X11/xorg.conf ?

As root (i.e. sudo before that command) that'll do the trick.

---

### Post by testube_babies on 2007-07-09
If there is a space in the file name it needs to be preceded with a back-slash \

mv /etc/X11/xorg.conf\ backup /etc/X11/xorg.conf

Also, if you use the tray icon for compiz fusion (on Arch it can be run with "fusion-icon"), you can choose the rendering platform "Indirect Rendering" to get rid of the black windows.

If you don't have the tray icon as an option, I'm pretty sure you can start compiz with "compiz --replace --indirect-rendering"

---

### Post by kansei on 2007-07-09
> **testube_babies said:**
> If there is a space in the file name it needs to be preceded with a back-slash \

mv /etc/X11/xorg.conf\ backup /etc/X11/xorg.conf

Also, if you use the tray icon for compiz fusion (on Arch it can be run with "fusion-icon"), you can choose the rendering platform "Indirect Rendering" to get rid of the black windows.

If you don't have the tray icon as an option, I'm pretty sure you can start compiz with "compiz --replace --indirect-rendering"

doh didn't notice the space in there :P

Another arch user? hooray!

I don't even use compiz/beryl/compositing in Arch though.. stupid ATI graphics card suckage haha. I was wondering if there was a compiz-fusion tray icon in Ubuntu, from your response I suspect there is.

As a temporary solution when everything goes black I just Alt-F2 and run compiz --replace

---

### Post by testube_babies on 2007-07-09
Have you tried using --indirect-rendering?  I'm curious to see if it works...

---

### Post by kansei on 2007-07-09
> **testube_babies said:**
> Have you tried using --indirect-rendering?  I'm curious to see if it works...

It works as in it feels just as it did with direct rendering. I guess I should have run that at a command line to make sure it actually worked and didn't just enable it the normal way.

edit: when I rotate cube it isn't really cubing.. more like just flipping a single pane. wait nvm I only have two desktops now. weird.

---

### Post by dimmanramone on 2007-07-12
take a look here it worked perfect for me...

[http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window](http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window)

---

### Post by kansei on 2007-07-12
> **dimmanramone said:**
> take a look here it worked perfect for me...

[http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window](http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window)

good show! :guitar:

I hadn't seen this "DAMAGE" stuff before!

---

### Post by tadtoll on 2007-07-19
> **testube_babies said:**
> ...

 I'm pretty sure you can start compiz with "compiz --replace --indirect-rendering"

Thanks very much. That worked for me. Black windows banished.

I just made a panel launcher with the following command string, and I am all set:

compiz --replace --indirect-rendering & emerald --replace 

And another panel launcher with:

metacity --replace

to get out of compiz-fusion (when need be).

I'll have to look into that tray icon. "fusion-icon" does not work for me in Feisty. I miss the old beryl tray icon for the beryl-manager.

---

