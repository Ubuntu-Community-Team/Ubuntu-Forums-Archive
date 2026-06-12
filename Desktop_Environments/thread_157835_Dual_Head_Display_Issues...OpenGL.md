---
title: "Dual Head Display Issues...OpenGL"
date: 2006-04-10
forum: Desktop Environments
---

### Post by Anduu on 2006-04-10
Okdk here goes...my first post :rolleyes: 

I have managed to get my Radeon 9600 dual head setup running.It seems like everything is functioning(ie. I can move windows between desktops yadda yadda...)

OpenGL however is driving me nuts ](*,) 

Accelerated screensavers do not display correctly...they are "squashed" to one side(the right) on both monitors and there is a nasty garbled stripe down the middle of my secondary display.

Additionally when I play DVDs using gl/gl2 I only get half of the picture.It appears that the left half of the movie has been cut off and is jammed against the left side of the window.I have tried many players Totem,Mplayer,VLC etc...with the same results.

I'm not sure I even want to try and see how OpenGL games react ;) 

I have been searching the forums all day on and off for a solution but can't seem to find any dual head threads that apply to my problem :-k 

Anywhooo this is my Xorg.conf as it sits right now...you can see by the commented out lines what I have been experimenting with...none of which seem to have any effect on anything :( 

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Insignia"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 1"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "fglrx"
#	Option	    "(null)"
#	Option	    "VideoOverlay" "on"
#	Option      "OpenGLOverlay" "on" 	
	Option	    "DesktopSetup" "horizontal"
	Option	    "UseInternalAGPGART" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor    "Insignia"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 1"
	Device     "ATI Graphics Adapter 1"
	Monitor    "aticonfig Monitor 1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

Oh did I mention I have only been playin with linux for a week and these forums have been a godsend :-D

***ANY*** advice would be greatly appreciated

---

### Post by Anduu on 2006-04-10
Hmmmm...after tinkering a bit more I have discovered that if I set my screens in a vertical arrangement everything seems to behave :-k 

I just don't know if I can adjust to this method as I have been using side by side for sooo long now.

It just don't feel right ](*,)

---

### Post by Firebird8 on 2006-04-10
How did u get it so you can move things between screens? I have a 9600 and I can't do it :confused:

---

### Post by Anduu on 2006-04-10
[QUOTE=Firebird8]How did u get it so you can move things between screens? I have a 9600 and I can't do it :confused:[/QUOTE]

Actually I found this little how-to...It was written for Gentoo but it worked like a charm ;) 

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#ATI](http://gentoo-wiki.com/HOWTO_Dual_Monitors#ATI)

Anyways this vertical layout is drivin me nuts...I'm switching back to horizontal;bugs and all...heh :-\"

---

### Post by Anduu on 2006-04-11
WooT!

Update...

After more tinkering it seems I have my problems 75% solved...

By Adding
```
Option 	    "EnablePrivateBackZ" "yes"
```to my Device section of /etc/X11/xorg.conf I have fixed dvd playback issues as well as getting rid of the garbled display on my second monitor during OpenGL screensavers...YAY!!! \\:D/ 

Only one problem remains...1/3 of the right of my screen on my secondary display is still being cut off during OpenGL screensavers. :-k 

I will continue tinkering but maybe my fix so ar will give someone else an idea of what to try next ?

Here is my xorg.conf as it stands now

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
	Load  "record"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Insignia"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 1"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "fglrx"
	Option	    "(null)"
	Option 	    "EnablePrivateBackZ" "yes"
#	Option	    "VideoOverlay" "on"
#	Option      "OpenGLOverlay" "on" 	
	Option	    "DesktopSetup" "horizontal"
	Option	    "UseInternalAGPGART" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor    "Insignia"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 1"
	Device     "ATI Graphics Adapter 1"
	Monitor    "aticonfig Monitor 1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

---

### Post by Anduu on 2006-04-14
Ok... tested OpenGL games a bit and they seem to work ok but the missing chunk of my second screen with OpenGL screensavers is gettin on my nerves :confused:

---

