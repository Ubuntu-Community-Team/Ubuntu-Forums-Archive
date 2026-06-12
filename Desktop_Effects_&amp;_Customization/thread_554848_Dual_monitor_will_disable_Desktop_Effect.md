---
title: "Dual monitor will disable Desktop Effect"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by keenlearner on 2007-09-19
Hello, I am using dual monitor and I notice/think that Desktop Effect depends on my configuration of /etc/X11/xorg.conf , so I think I have modified something that make the desktop effect on dual monitor not possible. If I used single monitor it works really nice, just found it today. This is my xorg.conf (I only show the section that I have made changes for dual monitor). Thank you.

> 
Section "Device"
	Identifier	"0 Intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
    Option        "MonitorLayout" "CRT,LFP"
    Screen        0
        Option          "DRI" "false"
EndSection

Section "Device"
	Identifier	"1 Intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
    Option        "MonitorLayout" "CRT,LFP"
    Screen        1
        Option          "DRI" "true"
EndSection

Section "Monitor"
	Identifier	"0 Generic Monitor"
	Option		"DPMS"
	#HorizSync	28-51
	#VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"1 Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
	 Modeline       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"0 Default Screen"
	Device		"0 Intel"
	Monitor		"0 Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800@60" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"1 Default Screen"
	Device		"1 Intel"
	Monitor		"1 Generic Monitor"
	DefaultDepth	24
	
	SubSection "Display"
		Depth		24
		Modes		"1280x1024@60" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "0 Default Screen"
	Screen		1 "1 Default Screen" RightOf "0 Default Screen"
	Option        "Xinerama" "On"
	Option          "Clone" "off"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by keenlearner on 2007-09-19
Hello, this might be my third post of my first 4 posts                                                       in ubuntuforums.org that nobody answers. So I spent hours already trying to get things right myself. But not luck....anybody ? Thank you.

---

### Post by cdekter on 2007-09-19
Hi,

This is only a hunch but... On your first display adaptor ("0 Intel"), you have  DRI disabled. As I understand it, DRI is used by OpenGL which means if you disable it, OpenGL will probably not work. OpenGL being used for desktop effects. Try setting both display adaptors to 'Option "DRI" "true"'

Chris

---

### Post by keenlearner on 2007-09-19
Thanks so much as long as you reply. It does not work either when I make DRI to true.
When I enable my desktop effect for dual monitor, my second(external LCD monitor) shows  up but my notebook screen show half white and half black horzontally. When I pressed ALT + TAB , I can see the square boxes moving, but not picture. When I open a window and see it in my external LCD monitor, the window does not have title bar. 
May I know does, the spacing in xorg.org matter ? such as it might, should be TAB instead of SPACE.

Thanks...

---

### Post by keenlearner on 2007-09-20
Anybody got ideas ? I have spent so much time on this to get it right. But can't help. Thanks.

---

### Post by JustAboutRealJAR on 2007-11-09
hey... sorry I don't have an answer for you as I am having the same problem. However, I do know that whitespace is insignificant in xorg.conf (ie. spaces, tabs are the same)

---

### Post by smithman89 on 2007-11-09
Hi, ok, so i had the same problem, though it was because i switched monitors.  My first observation is that screens and graphics likes to overwrite important stuff in your xorg.conf file.  In my case, it overwrote my prefs for my nvidia card.  So you should look for a backup xorg.conf file (xorg.conf.backup)  and compare it to your current one.  If the graphics card info is different, this is your problem.  the compiz desktop effects are set to your old card setting, and therefore wont run with the new ones.  Now here is my uncertainty:  If you change your vid card info back to the one that was in the backup, i dont know if the dual screen will work.  So if anyone can branch off my idea, that would be helpful.

---

### Post by JustAboutRealJAR on 2007-11-11
> **smithman89 said:**
> Now here is my uncertainty:  If you change your vid card info back to the one that was in the backup, i dont know if the dual screen will work.  So if anyone can branch off my idea, that would be helpful.

I know for sure that if you change the info back to the way it was in the backup you will lose dual monitor.

X still uses the xorg.conf file for interface config info, and the screens and graphics utility is just a graphical frontend for the xorg.conf file.

---

### Post by wilem on 2007-11-11
[http://forum.compiz-fusion.org/showthread.php?t=4859&highlight=dual+monitors](http://forum.compiz-fusion.org/showthread.php?t=4859&highlight=dual+monitors)

I did that and it fixed my issue.

---

### Post by Chen Jun on 2007-11-23
I got the same issue. :-(

I use same driver setting xorg.conf, the destop effect works for single monitor, as long as I put the config for second monitor, the desktop effect broke. 

I am using Gutsy, by the way.

---

### Post by mrmiserable on 2007-11-23
i can do this on ati card but not sure on intel but here is my xorg 

perhaps you can find something in it 

also i had to change resolution problem in preferences and set default then my card ran compiz

Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.

does this area when you run compiz fail when you type compiz in terminal

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "fr"
	Option	    "XkbVariant" "oss"
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
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "second Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 80.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "true"
	Option	    "AllowGLXWithComposite" "true"
	Option	    "AccelMethod" "XAA"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1024x1024+1024x1024,0x0+0x0"
	Option	    "EnableMonitor" "tmds1,crt1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "2048x1024" "1280x1024" "1024x768"
	EndSubSection
EndSection

```

---

### Post by Chen Jun on 2007-11-28
If you are use intel driver instead of "i810", you should be able to see all monitors attached, Here is my example:

jun@SG-J-CHEN:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected (normal left inverted right)
   1280x1024      60.0 +   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right) 304mm x 190mm
   1280x800       59.9*+   60.0     59.9* 
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
TV disconnected (normal left inverted right)

Unfortunately, my intel driver give me maximum resolution of 1280x1280, so I can't do a dual head with intel driver at all. If you are able to get a bigger maximum resolution with Intel driver, you may look into this link for solution:

[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

---

