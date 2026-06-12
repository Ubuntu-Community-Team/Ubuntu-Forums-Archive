---
title: "Problems to extend desktop with ATI Graphic card"
date: 2008-05-31
forum: Desktop Environments
---

### Post by Chogogo on 2008-05-31
Hey

Hardware: 
HP Pavilion a6412.sc 
Intel Pentium Dual Core 1.8 
Gráfic Card: Asus EAX 550HM512 
Grafic processor: ATI Radeon X550 
Mail Monitor: DVI 22 " flat 
Second Monitor: VGA 19" (the big ones, crt I belive) 
Software: Ubuntu 8.04

My problem is that I want to have different picture in my two screens. I have the ATI driver installed and working, I have grafics asceleration. I´ve tried to extend the desktop (BigDesktop option in Catalyst) but din´t work.I only get Cloned images. I have extended desktop only in login screen, then goes back to cloned. I am trying to configure DualHead but doesn´t go either.  this is what I did:

**sudo aticonfig --initial=dual-head --screen-layout=above **

Then I get this: 

[B]Found fglrx primary device section 
Found fglrx secondary device section 
screen layout section corrupted. [/B]

I really apreciate any help or information that will help me to set two different Images in my monitors.

Here I paste my Xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]" 0 0
Option "Clone" "off"
Option "BigDesktop" "on"
EndSection

Section "Files"
EndSection

Section "Module"
Load "glx"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "se"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
Option "EnableMonitor" "crt1,tmds1"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "aticonfig-Monitor[0]"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection



Thanks for your attention 

God Bless You

---

### Post by namraw on 2008-05-31
new to this but have been playing aroudn with dual heads

i think you might be confusing methods...

the problem maybe that u have enabled bigdesktop before running:

```
sudo aticonfig --initial=dual-head --screen-layout=above 
```

without bigdesktop enabled will create two desktops that u **cannot** drag and drop application between with there own seperate toolbars

my xorg with out bigdesktop enabled looked like

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
	Screen      1
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


```

but i assume the two seperate desktops is not wat u want if u wanted to use bigdesktop try ziox guid:

[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

***_note_***
The use of ***sudo aticonfig --initial=dual-head --screen-layout=above*** would set u up nicely for use of Xienrama method by simply adding to the top of ur xorg.conf:

```

Section "ServerFlags"
  Option      "Xinerama"  "ON"
EndSection

```

all dual head methods are in another ziox post here:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

hope this answered your question (sorry if it didn't)

---

### Post by Chogogo on 2008-05-31
Hi
First, Thanks for replying.
What I really need is to have two differents pictures in each monitor. It really doesn´t matter if I cannot drag applications between monitors, as long as the picture is different and of course, I have access to both desktops/monitors whenever I want.

I´ve tried configuring the second device manualy on the Xorg, but failed...

How did you made it??

Thanks

---

### Post by namraw on 2008-05-31
you could try creating a clean xorg file 

```
sudo dpkg-reconfgiure xserver-xorg
```

there is some options to run through note this will reset input devices as well.

then run:

```
sudo aticonfig --initial=dual-head --screen-layout=above
```

***_note - might have to:_***
i think when i did it there was an issue that there was no driver option so i added
```
Driver      ""
```
in the device section in my xorg.conf using
```
gksudo gedit /etc/X11/xorg.conf
```

then re run aticonfig line

hope this helps

---

