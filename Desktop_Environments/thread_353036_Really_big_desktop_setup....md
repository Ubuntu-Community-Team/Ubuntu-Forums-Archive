---
title: "Really big desktop setup..."
date: 2007-02-04
forum: Desktop Environments
---

### Post by Snille on 2007-02-04
HI all,
I have for the tow last weeks been searching around for a solution to get my really big desktop up and running, the fact is that the only thing that's keeping me still on Windows is the ability to work with multiple screens.

Current Windows setup:
Using a REALLY big desktop spanning over all 5 screens plus the projector (6 screens).
What I use:
1. ATI Radeon 9800 Pro AGP (BusID PCI:1:0:0) Dual head - Giving the tow main screens (2x21" CRT 1600x1200)
2. ATI Radeon 7000 PCI (BusID PCI:2:9:0) Dual head - Giving tow more screens (2x19" CRT 1600x1200) on top of the main screens.
3. ATI Radeon 7000 PCI (BusID PCI:2:10:0) Dual head - Giving one 17" CRT 1280x1024 and one 800x600 LCD Projector. The projector is on top in the middle of the 19" monitors, and the last 17" is to the left of the main left 21" monitor.

The dream would be to get the same setup using Ubuntu, Gnome and Beryl.
This is probably not possible. So, if I have to cut back. The 4 main screens (2x21" and 2x19") are the ones that's really important. If it is possible to get those 4 to work with Gnome and Beryl I would be really happy! :) After all, if I get Beryl i can let 2 screens slip. :)

I have really been trying to figure out how the xorg.conf should look. But I have not even gotten the tow 21" screens to work as one. 

Then above this I also have a "TV-Card" that I have not even begun to install yet. I don't know if i interfere somewhere but I don't thin so, I'll take one step at the time. :)

So, what to include? Here is the lspci log:
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT]
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:09.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:0a.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:0b.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 04)
02:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
```

I'm for the moment using ATIs driver (ati-driver-installer-8.33.6-x86.x86_64).
I have a fresh install of Ubuntu 6.10 Edgy Eft, with XGL working on one screen with Beryl installed. 
But I'm willing to do (almost) anything to get it all to work. :)

Is anyone up to the challenge? I have been for quite some time, but constantly failing... Probably most because I'm not so familiar with Linux yet.

If you are have problems "grasping" my setup, have a look at this picture, here you see all screens in there correct places.

---

### Post by gradedcheese on 2007-02-04
How comfortable are you with the format of /etc/X11/xorg.conf ?  Have you checked its contents to see if each card is there and how it's set up?  My guess is you just have to check there, turn on xinerama, and you should be all set.

Incidentally, why a setup like this?  I can only imagine the sheet amount of heat and radiation that produces, not to mention the current draw.  Does that really help you work more efficiently?  Have you considered a couple large LCD screens instead? :)

---

### Post by Snille on 2007-02-04
Hi there,
I'm fairly comfortable. I grasp the "function" (Device, Screen, Monitor and how they relate). But I don't know all the "options" and what to put where.

I have gotten "mirrors" to work, (21" mirroring each other). But I think that some kind of "default". And I have gotten the "login" screen to stretch over 2 screens (giving the login screen at one screen and it is possible to drag the mouse over to the other screen. But when I then login some error comes up and the only "session" that works is "Gnome Safe....". Also, as it it now, I have one screen fully working, and the one right of that one is just "black" but i can drag the mouse over to it and when I do the pointer becomes a "X". (I have note even tried to start the PCI cards, they are note in the xorg.conf file yet.). Here it my current xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
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
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
                                               # /dev/input/event
                                               # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"          # Tablet PC ONLY
EndSection

Section "InputDevice"
                                               # /dev/input/event
                                               # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"          # Tablet PC ONLY
EndSection

Section "InputDevice"
                                                # /dev/input/event
                                                # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"          # Tablet PC ONLY
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option      "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Screen      0
	BusID       "PCI:1:0:0"

#	Option      "AGPMode" "8"
#	Option      "EnablePageFlip" "on"
#	Option      "RenderAccel" "on"
#	Option      "DynamicClocks" "on"
#	Option      "BIOSHotkeys" "on"
#	Option      "MergedFB" "true" #Enable MergedFB function
#	Option      "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
#	Option      "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
#	Option      "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
#	Option      "OverlayOnCRTC2" "true"
#	Option      "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor.
#	Option      "MetaModes" "1600x1200-1600x1200" #Monitor Resolutions for Primary-Secondary monitors 
#	Option      "MergedXineramaCRT2IsScreen0" "true"#
#	Option	    "DesktopSetup" "horizontal" #Enable Big Desktop
#	Option	    "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
#	Option	    "Mode2" "1600x1200" #Resolution for second monitor
#	Option	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
#	Option	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option      "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Screen      1
	BusID       "PCI:1:0:0"

#	Option	    "DesktopSetup" "horizontal" #Enable Big Desktop
#	Option	    "Mode2" "1600x1200" #Resolution for second monitor
#	Option	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
#	Option	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection


Section "Monitor"
	Identifier  "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen      1  "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
#	Option         "+xinerama"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection
```

And for your questions why, well, because I could (in Windows). It's not about being more or less effective, it's about possibilities and limits. So, I mostly use the tow main screens when i program, testing on one screen coding on the other. The one above the main screen is mostly used for mail and file management, sometime just displaying help text and stuff during programming. The top right screen i use as a "monitor monitor". Monitoring CPU, Mem, network traffic on my main machine, the tow servers, the firewall, the wireless router and also displaying the latest (RSS) news from various news sites, the most left one (17") is mostly for release news (RSS) from various sites. I have made a small PHP script that parses selected RSS feed and format it the way i want it to be able to use it as a part of an "active desktop".

And the question about LCD instead of CTR, yes I'm all for LCD. When you can find one that can handle a MINIMUM of 1600x1200 for a realistic price. 500 euro is not a realistic price when you want to buy 5 screens... :)

Let me know if you have any other questions. :)

---

### Post by gradedcheese on 2007-02-04
It's been a while since I've owned a desktop PC (and thus needed to do this) but as I recall you need to enable xinerama, which is the piece that does the multi-display X stuff.  I see that xinerama is commented out in the one place it appears... there's also a ServerFlags entry that should be there.  However you should probably start by searching for xinerama-specific help, to see what the options are, etc.  

[http://www.systhread.net/texts/200506extendedX.php](http://www.systhread.net/texts/200506extendedX.php)

more:
[http://www.google.com/search?hl=en&q=xinerama+xorg&btnG=Search](http://www.google.com/search?hl=en&q=xinerama+xorg&btnG=Search)

I'm not going to argue with you about the extra monitors, but I've found that in Linux, the multiple desktops are just as useful.  You can use Control+Alt+Arrow (where arrow is Right or Left on the keyboard arrow keys) to switch between them quickly, and you can have as many as you want.  I usually use one for my text editor(s), one for compiling/running, one for looking at output files, etc.  My file became much more pleasant the day I got rid of the desktop PC, monitors, and other gadgets and replaced everything with a laptop and one big LCD screen :)

---

### Post by Snille on 2007-02-04
Ok, got 2 screens up now (the ones on the Radeon 9800) without XGL running... 
That's at least one step further. :)

Now I'm trying to start up the second video card (02:09.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE])... It is a "dual head card" but I cant see the "second" monitor in the lspci (as I do with the Radeon 9800 card). I don't know is this matters but this is what i "thought" the xorg.conf should look like. How ever, it don't work... :(

```
 -- cut --
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option      "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Screen      0
	BusID       "PCI:1:0:0"

#	Option      "AGPMode" "8"
#	Option      "EnablePageFlip" "on"
#	Option      "RenderAccel" "on"
#	Option      "DynamicClocks" "on"
#	Option      "BIOSHotkeys" "on"
#	Option      "MergedFB" "true" #Enable MergedFB function
#	Option      "MonitorLayout" "LCD, CRT" # Use LCD and CRT even if you have 2 LCD's or CRT's
#	Option      "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
#	Option      "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
#	Option      "OverlayOnCRTC2" "true"
#	Option      "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor.
#	Option      "MetaModes" "1600x1200-1600x1200" #Monitor Resolutions for Primary-Secondary monitors 
#	Option      "MergedXineramaCRT2IsScreen0" "true"#
#	Option	    "DesktopSetup" "horizontal" #Enable Big Desktop
#	Option	    "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
#	Option	    "Mode2" "1600x1200" #Resolution for second monitor
#	Option	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
#	Option	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option      "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Screen      1
	BusID       "PCI:1:0:0"

#	Option	    "DesktopSetup" "horizontal" #Enable Big Desktop
#	Option	    "Mode2" "1600x1200" #Resolution for second monitor
#	Option	    "HSync2" "65" #This sets the horizontal sync for the secondary display. 
#	Option	    "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Device"
	Identifier  "aticonfig-Device[2]"
	Driver      "fglrx"
	Option      "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Screen      2
	BusID       "PCI:2:9:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[3]"
	Driver      "fglrx"
	Option      "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Screen      3
	BusID       "PCI:2:9:0"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[2]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier  "aticonfig-Monitor[3]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
        Virtual 1600 1200
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
        Virtual 1600 1200
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[2]"
	Device     "aticonfig-Device[2]"
	Monitor    "aticonfig-Monitor[2]"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
        Virtual 1600 1200
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[3]"
	Device     "aticonfig-Device[3]"
	Monitor    "aticonfig-Monitor[3]"
	DefaultDepth     24
	SubSection "Display"
#		Viewport   0 0
		Depth     24
        Virtual 1600 1200
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen      1  "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	Screen      2  "aticonfig-Screen[2]" Above "aticonfig-Screen[0]"
	Screen      3  "aticonfig-Screen[3]" Above "aticonfig-Screen[1]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"	 
    Option "Xinerama" "On"	 
EndSection
 -- cut --
```
I have added my xorg.0.log to the post as well.

It looks like it dos not find the second video card?
Do you have any god suggestions? :)

---

