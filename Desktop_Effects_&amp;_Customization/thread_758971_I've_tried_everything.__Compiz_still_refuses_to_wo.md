---
title: "I've tried everything.  Compiz still refuses to work."
date: 2008-04-18
forum: Desktop Effects &amp; Customization
---

### Post by MonoMatt304 on 2008-04-18
I've been trying off and on for weeks to get Compiz to work to no avail.  Here's what it tells me when I try and run it:

```
matthew@gateway-laptop:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e50 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting
```

My laptop has a Radeon 9600 Mobility in it, and the drivers are installed, as shown by running fglrxinfo:

```
matthew@gateway-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

Additionally, I have changed "Composite 0" to "Composite 1", in xorg.conf as other threads have recommended that I do.

```
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
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection

```


Can anyone please help me with this?  This is rather frustrating, and I don't know what else to do.

---

### Post by luisromangz on 2008-04-18
Have you tried using XGl? Which version of ATI's drivers are you using?

---

### Post by MonoMatt304 on 2008-04-18
> **luisromangz said:**
> Have you tried using XGl? Which version of ATI's drivers are you using?

Yeah, I've tried it, but XGL is horrifically slow and makes my system unusable.  So slow, in fact, that I can't even try to start Compiz because it takes a few minutes to even load the terminal.  Besides, from what I understand, I shouldn't even need to use it, as it's all been recently integrated or some such matter.

My fglrx drivers are 8.37.06 which, according to Adept, is the latest (as there are no updates available).

---

### Post by russo.mic on 2008-04-18
Strange, XGL works great for me. (well, as great as it can, but compiz runs fine, and looks great)  Did you disable Composite in Xorg?

Paste this (unless it already is) into your /etc/X11/xorg.conf and give XGL a shot.

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Remember to make a copy of your current Xorg first!

Russo

---

### Post by MonoMatt304 on 2008-04-18
> **russo.mic said:**
> Strange, XGL works great for me. (well, as great as it can, but compiz runs fine, and looks great)  Did you disable Composite in Xorg?

Paste this (unless it already is) into your /etc/X11/xorg.conf and give XGL a shot.

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Remember to make a copy of your current Xorg first!

Russo

Already tried.

Still no go, unfortunately.

---

### Post by pseudo-random on 2008-04-18
Try adding some of these options to your "Device" section:
```

        Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option "TexturedVideo" "on"
        Option "XaaNoOffscreenPixmaps"
        Option "UseFastTLS" "2"
        Option "RenderAccel" "true"
      

```

Don't do them all at once just add them one at a time and keep restarting your X-server with Ctrl-Alt-Bkspace and testing glxgears until you get something better.

---

### Post by luisromangz on 2008-04-18
Your driver is old. It is the latest version in the repositories because no new version of programs are added when a Ubuntu version is released, only security fixes.

Try installing the latest drivers from ATI's website, and then enable AIGLX (the older driver doesn't support it) or XGl (which should be faster with the newer driver).

---

### Post by jose158 on 2008-04-18
Try and follow this tutorial:[ http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")

Hope it helps
Jose'

Edit: It says that it is for Feisty, but it worked fine on Ubuntu 8.04!

---

### Post by MonoMatt304 on 2008-04-18
> **luisromangz said:**
> Your driver is old. It is the latest version in the repositories because no new version of programs are added when a Ubuntu version is released, only security fixes.

Try installing the latest drivers from ATI's website, and then enable AIGLX (the older driver doesn't support it) or XGl (which should be faster with the newer driver).

That did it!

Just installed the drivers and didn't have to do anything else.

Only problem now is that Compiz seems to like to get rid of all of my title bars, which is a bit annoying.

Thoughts on that?

Thanks so much for the help everyone.

---

### Post by rainwalker on 2008-04-18
Also, for future reference, if you're ever on a machine and want to see if you can use Compiz at all, try ```
SKIP_CHECKS=yes compiz
```

---

### Post by luisromangz on 2008-04-19
For the title bar problems, you should try running Compiz fussion from a little tray utility called "fusion icon", which allows you to switch between Emerald, gtk-window-decorartor/kde-window-decorator so you can see which one works best for you.

---

