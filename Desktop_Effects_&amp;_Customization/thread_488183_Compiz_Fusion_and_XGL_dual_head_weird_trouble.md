---
title: "Compiz Fusion and XGL dual head weird trouble"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by alv22 on 2007-06-29
Hi everyone. o/

It seems I have trouble starting Compiz Fusion. I'm running 7.04 feisty and my gfx card is ATI Radeon 9800 Pro (128mb).

Now, I've read several guides and pulled out all my hair trying to fix this.

I've tried many things. [http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773) This was the latest I've tried.

My fglrxinfo lists as follows:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6474 (8.38.6)
```

Yet, when running compiz --replace:

```
grep: 7784/smaps: No such file or directory
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Now, it would seem like XGL isn't running. When I log in, choose XGL as my session, it pauses for 4 seconds, as the script says, runs all nice but still looks exactly like the normal xorg session. And of course, displays the pixmap failure error.

I've set my startxgl.sh like this:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:0 
exec gnome-session

```

Note that I changed the DISPLAY 1 to 0 because when running it as 1 when logging into the session it starts whining stuff about "no found displays" or something. This, I thought is because I have a little different than the average fusion guide setup (I run ATI's big desktop, two 19" displays - in total 2560x1024 resolution. Dual screens work nicely, no trouble with them at all.) 

This is my xorg.conf if it helps:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fi"
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
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "VA902"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x1024+1280x1024"
	Option	    "EnableMonitor" "crt1,crt2"
	Option	    "ForceMonitors" "crt1,crt2"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor    "VA902"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


Section "Extensions"
	Option "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

Any thoughts on this? I'm running out of ideas, and hair. I'm still optimistic about this, I feel like it can still be solved by editing one tiny number somewhere and suddenly I'm greeted with hardware accelerated fractal soup of goodness.

---

### Post by kpolice on 2007-06-30
Dual monitor won't work, try with one.

To make sure XGL is running use gnome-system-monitor or top to see if the Xgl process is running.

---

### Post by superyounan1 on 2007-06-30
hi,

i have the same video card, same fglrx version, dual displays (one of them is my TV), i used the --initial=dual-head option setting up with aticonfig, and I'm successfully running xgl and fusion. TV doesnt work during the xgl session though

here's my xgl startup script, its a bit different than yours, maybe it will help

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

i suggest you backup your current version before making changes

---

