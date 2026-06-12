---
title: "ATI dual head setup: not boot without 2nd monitor, no gnome, no compiz"
date: 2008-12-28
forum: Desktop Environments
---

### Post by antroid on 2008-12-28
hi linux folks. these are my first steps into linux. i got some trouble with my dual head configuration and would like to ask you for a solution. i got this notebook and an external TFT with a bigger resolution. if its not connected and enabled the log-on screen doesnt appear on boot. i used aticonfig to get it working with xinerama: ```
sudo aticonfig --initial=dual-head --desktop-setup=vertical --vs=on --resolution=0,1280x800 --resolution=1,1680x1050 --screen-layout=above --add-pairmode=1280x800+1680x1050 --overlay-on=1 --force
```
the configuration without xinerama looks more beautiful and maybe ill like it better having two sessions. but without the xinerama line gnome doesnt start at all. i can move the mouse around and on the 2nd screen the cursor changes to an X... what does it mean?

heres my conf.
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" Above "aticonfig-Screen[0]-0"
	Inputdevice "stylus" "SendCoreEvents"
	Inputdevice "eraser" "SendCoreEvents"
	Inputdevice "touch" "SendCoreEvents"
	Option	    "Xinerama" "1"  #### without this more beautiful, but no session started.
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier "stylus"
	Driver "wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option "Type" "stylus"
	Option "USB" "on" # USB ONLY
	Option "Screen_No"  "0"
EndSection

Section "InputDevice"
	Identifier "eraser"
	Driver "wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option "Type" "eraser"
	Option "USB" "on"# USB ONLY
	Option "Screen_No"  "0"
EndSection

Section "InputDevice"
	Identifier "touch"
	Driver "wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
	Option "Type" "touch"
	Option "USB" "on"# USB ONLY
	Option "Screen_No"  "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "DesktopSetup" "vertical"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x800+1680x1050" #### had to be added manually because of aticonfig failing. :(
	Option	    "OverlayOnCRTC2" "1"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection
```

on connect and disconnect (on lid close also) id like the notebook to react correctly, moving the windows to the active screen each time. id like to use compiz fusion also. but it fails starting up and i dont understand why. :( the terminal often outputs this error message, maybe thats a hint.```
Xlib:  extension "RANDR" missing on display ":0.0".

```

thank you for any advice.

EDIT:
when i enter the command compiz --replace he outputs:```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
Xlib:  extension "RANDR" missing on display ":0.0".
```

---

### Post by CHaoSlayeR on 2009-01-10
Hi there,

your problem seems to be that the second monitor is required for the X server, not optional. Reading your experiences I think the fglrx driver is not that flexible.

What graphics card do you have?

If it is some type of Radeon Xxxx cards it should be safe to use the open source 'radeon' driver (not 'radeonhd') as I got that one up and running at work with KDE4, all effects, very smooth, 3D acceleration and X-Video acceleration. Although it's not a laptop using an open source driver may things much easier.

C]-[aoZ

---

