---
title: "External Monitor Help Please"
date: 2010-09-05
forum: Desktop Environments
---

### Post by bluTaz on 2010-09-05
OK, so I just bought a 31.5" HDTV and have it connected to my laptop as a monitor. My laptop monitor is cracked and pretty much useless so I would like to be able to keep it turned off and stick with my new monitor. So far, I have managed to accomplish all of this, just one problem, I will need to go through too long a process for every login to set it all up again. I'm hoping someone can help me simplify this and have everything done automatically while Ubuntu is booting or even right after login.

Process:

```
$ cvt 1366 768 60
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```
```
$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```
```
$ xrandr --addmode "HDMI1" "1368x768_60.00
```"
```
$ xrandr --output HDMI1 --mode 1368x768_60.00
```

I then must go into "Monitors" and switch the laptop monitor off, and everything is pretty much near perfect.

Now, as far as I have read so far, I'm imagining that I must go into xorg.conf and change some stuff there, only I'm not sure how to go about it.

Current xorg.conf:
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "extmod"
	Load  "glx"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile GM965/GL960 Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```
Is there anyway that I can have everything done automatically?
Any help will be appreciated guys, and thanks ahead of time.
ohh, in case you ask, using Intel graphics. Ubuntu 10.04

---

### Post by djinnkeeper on 2010-09-05
forgive me for responding with a question, but is there any way a script could just run at startup to do all of that stuff?  You're probably right to assume that xorg is the key to the lock.

---

### Post by bluTaz on 2010-09-05
was thinking a script could help, only I'm not sure how I would go about setting it all up. Any suggestions would be much appreciated.

---

### Post by bluTaz on 2010-10-17
I do now have a working script to have most of my intentions applied, however, I am hoping that perhaps someone can lead me to a better way of doing this, as I find it as more of a workaround than an actual solution.

```

#!/bin/bash
# Sets display up for use with HDTV.

cvt 1366 768 60 &&
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync &&
xrandr --addmode "HDMI1" "1368x768_60.00" &&
xrandr --output HDMI1 --mode 1368x768_60.00

sleep 10 &&
    gnome-display-properties

```

I have the Monitors dialog start at login so that I can turn off the laptop monitor, leaving only the HDTV running as a monitor. Although this works, I was hoping someone can lead me to a way to have these steps applied in the script so that I do not have to do it manually everytime I login.

Any suggestions are welcome guys. Thanks.

Also, I would really like a way for this all to take effect immediately at startup.

Description of monitor state during boot:

**poweron**- monitor does not display
**grub-** monitor does not display
**splash-** monitor displasy splash but splash is slightly offset, then it automatically corrects the aspect ratio and displays perfectly
**login-screen-** display is working, but aspect ratio is not correct; displayed correctly, but does not use fullscreen
**logged-in**- same as login-screen, from here above script is called

I would really like the monitor to atleast be functional once grub loads. Also, during the splash, it does display perfect once it corrects itself. So something during boot is displaying the HDTV correctly, and then once the login-screen is displayed, it gives the wrong aspect ratio.

Well, if I can't get it to function completely during boot, I atleast want it perfect once I login. So if anyone has some suggestions on improving my script to  do everything automatically, without the use of the Monitor dialog, I would really appreciate them. And if someone can point me in the right direction to get everything going during boot, that would be great as well. Thanks everyone.

**Distro Update:** Ubuntu 10.10 (Maverick)

---

### Post by bluTaz on 2011-01-04
this is still something that bothers me, although I have everything to be set right as soon as I login through a script. If anyone figures out how to get my monitor working during startup, it would be a great help. Also note, hdtv connected with hdmi cable.

---

### Post by bluTaz on 2011-04-12
Just thought Id update this thread and post my solution in case someone else is looking for something similar.

I did manage to get the entire boot process to display on the HDTV, however, I took a whole other route to do this. I followed the documentation on the Dell website to remove my laptop monitor completely (not an issue since it was useless anyways). So I have a laptop without the monitor and just have it sitting on a laptop cooler and acting as a desktop. After doing so, the bootup process recognizes my HDTV as its primary screen and everything displays from poweron.

Editing /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="video=1366x768-32"
```
... fixed grub and splash, however, I decided to disable the splash.

Editing /etc/gdm/Init/Default:
paste before: /sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
```

cvt 1366 768 60 &&
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync &&
xrandr --addmode "HDMI1" "1368x768_60.00" &&
xrandr --output HDMI1 --mode 1368x768_60.00 && 
xrandr --output LVDS1 --off

```.... fixed the GDM and everything afterwards.

Now onto getting all this working with Arch Linux ....

---

