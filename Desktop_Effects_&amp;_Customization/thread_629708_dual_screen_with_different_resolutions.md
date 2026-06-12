---
title: "dual screen with different resolutions?"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by skjoldfetter on 2007-12-02
ok... i've spent all day looking through "related threads" and howto's without getting an answer to this...

i have two monitors... i would like to run one at 800x600, and one at 1280x1024...

i have an Nvidia geforce 6600 GT card. and im using the restricted driver.

it seems that this is impossible.. 
either i get two separate screens where i can move the mouse, but not windows between them...(separate X screens,xinerama off)
or a wide screen that spans them both, but only works at the same resolution...(separate X, xinerama on) 
or i get one huge screen that sticks out over the edges of one causing it to "pan" when i move my mouse to the sides...(twinview)

does anyone have a clue if this is even possible?

---

### Post by skjoldfetter on 2007-12-02
well... i managed one 1024x768 and one 1280x1024 on separate X screens with xinerama on,
it wont change down to 800x600, and no visual effects (compiz) work.

at the moment i can live with this... even though the resolution isnt optimal i've spent all day trying... so unless someone has a suggestion ill give up here <_<

---

### Post by Rupertronco on 2007-12-02
What do you want to be able to do? Do you want two different X screens or one screen? I've done this with two different monitors of different resolutions and I used twinview to do it. I edited my xorg.conf and just typed in their native resolutions. 

My advice would be to use the nVidia tool and use twinview to set this up.

---

### Post by skjoldfetter on 2007-12-02
how do i edit my xorg? :P

/noob

---

### Post by notatoad on 2007-12-02
to edit your xorg open a terminal and type "sudo cp /etc/X11/xorg.conf /etc/X11/xorgconfbackup" and then "sudo gedit /etc/X11/xorg.conf"  when you've finished editing, ctrl+alt+backspace to restart X

but the easiest way is the new gutsy screens manager.  go to system>administration>screens and graphics

set the resolution on your default monitor, enable the other monitor as a secondary screen, and set it's resolution.  that works for me, anyways.

---

### Post by skjoldfetter on 2007-12-02
i've tried the screen manager, it was the first thing i did ;)

it does all kinds of strange things (deactivate one or both screens/overlap/change both screens to 640x480)

---

### Post by skjoldfetter on 2007-12-02
ok.. so now he told me how to edit it... now im just wondering what i should edit and to what... :P

---

### Post by usererror on 2007-12-25
Can you post an example?  I am having the same issue.  I have one monitor on the VGA output that is 1280x1024 and works, and the one on the left is a widescreen that is stuck at 1024x768.  If I can get the wide screen to do its native 1440x900...  I also cannot get compwiz to work.

My video card is an ATI with on DVI and on D-Sub.

```


# Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "screen1" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "screen1"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
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

Section "Monitor"
 #  
	Identifier   "monitor1"
	VendorName   "Plug 'n' Play"
	ModelName    "Plug 'n' Play"
	Gamma        1
	ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
	ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
 #  
	Identifier   "monitor2"
	Gamma        1
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
 #  
	Identifier  "device1"
	Driver      "fglrx"
	VendorName  "ATI"
	BoardName   "ATI Radeon (fglrx)"
	Option	    "MergedFB" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
 #  
	Identifier  "device2"
	Driver      "vesa"
	BoardName   "VESA driver (generic)"
	BusID       "PCI:1:0:1"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
 #  
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024@60" "1024x768@60" "1024x768@70" "1024x768@75" 
	EndSubSection
EndSection

Section "Screen"
 #  
	Identifier "screen2"
	Device     "device2"
	Monitor    "monitor2"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection

```

---

