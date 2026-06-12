---
title: "xorg.conf troubles"
date: 2005-06-30
forum: Desktop Environments
---

### Post by Whatsisname on 2005-06-30
greetings anyone.

I wanted to know if anyone has encountered the problem I am undergoing. I recently got a new (used) monitor and wanted to increase my resolution, from 1280x1024 up to 1600x1200. However, xorg apparently does not like that idea. 

I went into my xorg.conf and changed the Horizontal and Vertical frequencies to reflect my new monitor, then I added 1600x1200 into my screen modes section. I killed my xserver and restarted gdm and expected it to work. It doesnt. I tried a bunch of things to narrow it down but nothing seems to work. What is very odd though, is that if i run X -config /etc/X11/xorg.conf, it fires up in 1600x1200x85hz just fine. (although its just the diagnostic checkerboard screen) However, if i run startx as a user, it goes into 1280x1024x75hz, even though xorg claims its using /etc/X11/xorg.conf. I've tried ctrl+alt+ +/- to try and switch modes but it doesnt work. 

Also, i've noticed when I use gdm it uses a config file from /home/me/xorg.conf, while if i just use startx it grabs it from /etc/X11/xorg.conf. Both files are the same in each location so I doubt thats whats going on. I've also search my computer for any other renegade xorg.conf files that could be hiding and giving me trouble. Anyone have any idea what might be going on?

thanks for any and all help

---

### Post by Omnios on 2005-06-30
Only thing I could suggest is using " sudo dpkg-reconfigure xserver.xorg " outside of dgm. Its a graphical Xorg config that lets you set up a hole bunch of options including res. Downside is you have to go through a hole bunch of stuff. Also if your using nvidia   you have to use a show driver "nvidia" option etc.

 Personaly I dont like this option but it seems to get things fixed.

---

### Post by Whatsisname on 2005-06-30
I tried that but it didn't work. Upon some further investigation, I have found that the GDM thing will run at 1600x1200, but as soon as I login it gets cut down to 1280x1024. There are no xorg.conf's in my home directory, and I don't see any hidden directories pertaining to xorg. What the heck is going on? :(

this is my config file:
```
Section "Files"
  FontPath     "/usr/X11R6/lib/X11/fonts/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/local"
  FontPath     "/usr/X11R6/lib/X11/fonts/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/URW"
  FontPath     "/usr/X11R6/lib/X11/fonts/Speedo"
  FontPath     "/usr/X11R6/lib/X11/fonts/PEX"
  FontPath     "/usr/X11R6/lib/X11/fonts/cyrillic"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin2/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/latin7/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/baekmuk:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/japanese:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/kwintv"
  FontPath     "/usr/X11R6/lib/X11/fonts/truetype"
  FontPath     "/usr/X11R6/lib/X11/fonts/uni:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/CID"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/ucs/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/misc:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/75dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/100dpi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/hellas/Type1"
  FontPath     "/usr/X11R6/lib/X11/fonts/misc/sgi:unscaled"
  FontPath     "/usr/X11R6/lib/X11/fonts/xtest"
  FontPath     "/opt/kde3/share/fonts"
  InputDevices "/dev/ttyS0"
  InputDevices "/dev/ttyS1"
  InputDevices "/dev/ttyS2"
  InputDevices "/dev/ttyS3"
  InputDevices "/dev/ttyS4"
  InputDevices "/dev/ttyS5"
  InputDevices "/dev/ttyS6"
  InputDevices "/dev/ttyS7"
  InputDevices "/dev/ttyS8"
  InputDevices "/dev/psaux"
  InputDevices "/dev/logibm"
  InputDevices "/dev/sunmouse"
  InputDevices "/dev/atibm"
  InputDevices "/dev/amigamouse"
  InputDevices "/dev/atarimouse"
  InputDevices "/dev/inportbm"
  InputDevices "/dev/gpmdata"
  InputDevices "/dev/mouse"
  InputDevices "/dev/usbmouse"
  InputDevices "/dev/adbmouse"
  InputDevices "/dev/input/mice"
  InputDevices "/dev/input/event0"
  InputDevices "/dev/pointer0"
  InputDevices "/dev/pointer1"
  InputDevices "/dev/pointer2"
  InputDevices "/dev/pointer3"
EndSection


Section "ServerLayout"
	InputDevice  "Keyboard0" "CoreKeyboard"
	InputDevice  "Mouse0" "CorePointer"
	Identifier     "Custom Layout"
	Screen         "DefScreen" 0 0
EndSection


Section "Module"
	Load  "v4l"
	Load  "type1"
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "freetype"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Buttons" "5"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "keyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "chicony"
	Option	    "XkbLayout" "us"
EndSection

Section "Modes"
  Identifier   "BlackModes"
  Modeline 	"1600x1200" 229.5 1600 1664 1856 2160 1200 1201 1204 1250
  EndSection

Section "Device"
	  BoardName    "GeForce3"
	  BusID        "2:0:0"
	  Driver       "nvidia"
	  Identifier   "Geforce3"
	  Screen       0
	  Option       "Rotate" "off"
	  VendorName   "NVidia"
EndSection

Section "Monitor"
	Identifier	"IBM P275"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	48-170
   Modeline 	"1600x1200" 229.5 1600 1664 1856 2160 1200 1201 1204 1250
EndSection

Section "Screen"
	Identifier	"DefScreen"
	Device		"GeForce3"
	Monitor		"IBM P275"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by walkeral on 2005-07-01
Sounds like your user profile is taking over the screen resolution after you log in. I don't know where these files are - perhaps just try the "Change screen resolution" option from the menus, and hopefully 1600x1200 will be there.

---

### Post by Whatsisname on 2005-07-01
[QUOTE=walkeral]Sounds like your user profile is taking over the screen resolution after you log in. I don't know where these files are - perhaps just try the "Change screen resolution" option from the menus, and hopefully 1600x1200 will be there.[/QUOTE]
 indeed thats what it was. I went into the gnome control panel thing and was able to change the resolution there. The whole time I thought it was only up to X for determining your resolution. Guess I was wrong.

Thanks for the help.

---

