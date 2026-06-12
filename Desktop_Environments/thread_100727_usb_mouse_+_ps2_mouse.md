---
title: "usb mouse + ps2 mouse"
date: 2005-12-08
forum: Desktop Environments
---

### Post by Jabone on 2005-12-08
I can't get those mouses to work together with all buttons available.

I have configured usb-mouse to use evdev and ps2 mouse to use imps2.

When I comment out ps2 mouse from xorg.conf all buttons from usb mouse works. 
 
I can use both mouses with basic buttons such as buttons 1,2,3 and mousewheel buttons 4 and 5

I know this is available but i lost my xorg.conf when reinstalling ubuntu. 

Can someone help me?

My xorg.conf with mouse configurations:

Section "InputDevice"
	Identifier	"Configured Mouse" #The basic logictech wheelmouse
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
    	Identifier	"Wireless Mouse" # usb mouse with 8 buttons
	Driver        	"mouse"
#	Option 		"CorePointer"
	Option        	"Protocol"        	"evdev"
	Option        	"Dev Name"        	"Wireless Mouse Wireless Mouse"
	Option        	"Dev Phys"        	"usb-*/input0"
	Option        	"Device"        	"/dev/input/event1"
	Option        	"Buttons"        	"30"
	Option        	"ZAxisMapping"        	"4 5"
EndSection

and section layout:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Wireless Mouse"

EndSection

---

### Post by veelivar on 2005-12-08
Sorry I'm not answering your question here but I have a quewstion on hwta you have posted (it might help me out).

Are these entries specific to your mouse? or for usbmice in general?
```

Option "Protocol" "evdev"
Option "Dev Name" "Wireless Mouse Wireless Mouse"
Option "Dev Phys" "usb-*/input0"
Option "Device" "/dev/input/event1"

```

I have a new USB laser mouse that isn't working (my old usb infrared one does fine) It all seems to be picked up ok and recognised in my device settings through Gnome.  I was wondering if it wa how my xorg.conf was set up but don't really know enough about it.

Cheers,
Dan.

---

### Post by Jabone on 2005-12-10
Option "Protocol" "evdev"             
Option "Dev Name" "Wireless Mouse Wireless Mouse" 
Option "Dev Phys" "usb-*/input0"
Option "Device" "/dev/input/event1"

"Wireless Mouse Wireless Mouse", "usb-*/input0" and "dev/input/event1" is dependant for your mouse. see "cat /proc/bus/input/devices" for your mouse information.

Follow the link for help.
[http://www.ubuntuforums.org/showthread.php?t=65471](http://www.ubuntuforums.org/showthread.php?t=65471)

---

