---
title: "Gutsy + ATI 8.42.3 + dual head + different resolutions"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by leps on 2007-10-23
Hello.  I just manually installed the new ATI drivers in gutsy and they work great with the compiz eye candy effects.  One problem I have is that my laptop which is 1400x1050 and LCD which is 1600x1200.  It seems that the catalyst control center wants them to be the same resolution (1400x1050).  All the compiz effects do work with "big desktop" on but I'd like to set it up so that both LCDs can run in native mode.  I can't seem to convince the catalyst control center to bump up the resolution for my external LCD to anything over 1400x1050.  Is anyone else having this problem?

---

### Post by scoobySnack on 2007-10-24
any chance of posting your xorg.conf file? I've not even been able to get that far with big desktop (gdm works, but every time I login to gnome or kde the session just hangs and eventually exits back to gdm - tried creating a new home dir but no luck yet).

---

### Post by ebash on 2007-10-24
I'm also very interested in seeing your xorg.conf. I managed to have my dual head setting working but not with compiz.

If I enable XGL then I can't login to my account, the screen stays beige and GDM restarts after a while. The file ~/.xsession-errors displays:

```

Xsession: X session started for emmanuel at Tue Oct 23 09:08:58 CEST 2007
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
[0] couldn't create glitz drawable for window

Fatal server error:
no screens found
rm: cannot remove `/tmp/.X1-lock': No such file or directory
xmodmap:  unable to open display ':1'

```

 I realized the the problem is due to XGL, if I remove XGL then I can login, my dual head setting works and 3D applications can run, but not compiz.

I have attached my xorg.conf file, in case that it can help someone.

---

### Post by scoobySnack on 2007-10-24
Yep can confirm the same. Read a thread earlier (after my post above) where every poster was confirming the same issue:

[http://ubuntuforums.org/showthread.php?t=511869&highlight=ati+compiz+dual+head](http://ubuntuforums.org/showthread.php?t=511869&highlight=ati+compiz+dual+head)



Seems there's are inescapable issues with compiz, ati dual head and XGL. I tried to use Xinerama instead of the ATI big desktop and had sync/resolution issues with my monitors even with the same settings, I take it this would be the approach to compiz + dual head with an nvidia driver? But no luck in getting it to work with ati 8.42 drivers.

I've read that the new 8.42 drivers are compatible with  AIGLX, does this mean it would be possible to AIGLX instead of XGL and then get dual head working at all? I've not worked out how to do this yet, and not even sure if that is possible and makes sense.

As you may have worked out I'm new to all this Xorg snazzy 3d tech due to always having ati cards on my laptops, so I've not until now bothered to work out the differences between X windows 3d technologies.

time to read up...

---

### Post by scoobySnack on 2007-10-24
OK, found this thread which explain how to switch from XGL to AIGLX:

[http://ubuntuforums.org/showthread.php?t=588605&highlight=aiglx+xgl](http://ubuntuforums.org/showthread.php?t=588605&highlight=aiglx+xgl)

be warned though, as it looks like XGL uses a few short cuts including using your CPU to compensate for a low end gfx card, and lots of people are experiencing slowdown and choppyness after the move over to AIGLX.

This thread here has more info on the differences between XGL and AIGLX for those that (like me earlier) didn't know the difference:

[http://ubuntuforums.org/archive/index.php/t-159284.html](http://ubuntuforums.org/archive/index.php/t-159284.html) 

(search for a poster called "poofyhairguy" he seems to know what he's talking about)

Next thing to find out is that if using AIGLX can we get compiz working with dual head? My gfx card won't do AIGLX very well so I'm not too ken to try it out.

---

### Post by scoobySnack on 2007-10-24
This thread supposedly explains the difference between different dual head configuration. It looks like MergedFB may work with compiz on both screen, not much info on big desktop:

[http://ubuntuforums.org/showthread.php?t=221174&highlight=ati+big+desktop+compiz](http://ubuntuforums.org/showthread.php?t=221174&highlight=ati+big+desktop+compiz)

---

### Post by leps on 2007-10-24
Ok, I got it working using AIGLX and compiz with my laptop screen running 1400x1050 and the external LCD at 1600x1200 :)  One problem I noticed was performance.  The compiz effects are slowwww.  I don't think this is a hardware issue because I had dual desktop compiz running under XGL (but with the same resolutions) and it worked smoothly.  I will attach my xorg.conf.

---

### Post by leps on 2007-10-24
And it didn't attach... Here it is.  I am thinking there may be something I have in there that is hurting the driver's performance.  Let me know what you guys think.

```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
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
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc100"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 70.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal,reverse"
        Option "PairMode" "1400x1050+1600x1200"
        Option      "OverlayOnCRTC2" "1"
Option "DesktopSetup" "LVDS,AUTO"
#       Option "VideoOverlay" "on"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
#               Modes    "1400x1050"
                Viewport 0 0
                Depth 24
                Virtual 1600 1200
        EndSubSection
EndSection

```

---

### Post by scoobySnack on 2007-10-25
I think AIGLX with compiz running slow is a know issue, it certainly depends heavily on hardware, especially so with an ATI card. You also said you're running on a laptop and all the but most very high end laptops have pretty low spec video cards that use main memoery instead of dedicated onboard memory which seriously hampers performance.

XGL takes a few shortcuts and hammers your cpu (just check the output of top at the command line and move a wobbly window around) to make up for lack of acceleration hardware.

from what I can work out AIGLX needs some time to mature and get full hardware support.

This is conjecture though at this point, what video card do you have?

---

### Post by Aramil Moonmist on 2007-10-25
i just (for the first time ever) got aiglx working. it was a touch slower than xgl, and less buggy by far. only problem is the firefox scrolling

and until i rebooted, had compiz, aiglx, and big desktop working smoothly on gutsy, radeon x1300, gig of ram. now it has the virtual space of the second monitor, it just isnt showing on it. but the point is it was working smoothly

heres the xorg.conf that worked (and without any changes, stopped working)
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Option	    "XkbLayout" "us"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SHMconfig" "on"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseFastTLS" "2"                 #BD
	Option	    "Capabilities" "0x00000800"      #BD
	Option	    "DesktopSetup" "horizontal"      #BD
	Option	    "PairMode" "1280x800+1280x1240"  #BD
	Option      "Mode2" "1280x1024"              #BD
	Option	    "EnableMonitor" "crt1,lvds"      #BD
	Option	    "ForceMonitors" "crt1,lvds"      #BD
	Option      "EnablePrivateBackZ" "yes" #BD Enable 3d support <= May Not Work
#        Option      "OverlayOnCRTC2" "1" #BD test
	BusID       "PCI:1:0:0"
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

Section "DRI"
	Mode         0666
EndSection

#Section "Extensions"
#	Option	    "Composite" "Disable"
#EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection

```

***EDIT*** after following someones tip: [http://ubuntuforums.org/showthread.php?t=386841&highlight=_NET_NUMBER_OF_DESKTOPS](http://ubuntuforums.org/showthread.php?t=386841&highlight=_NET_NUMBER_OF_DESKTOPS)
deleting ~/.gnome ~/.gnome2 ~/.gconf

now big desktop is working perfectly again

---

### Post by leps on 2007-10-30
It's an ATI x1300

> **scoobySnack said:**
> I think AIGLX with compiz running slow is a know issue, it certainly depends heavily on hardware, especially so with an ATI card. You also said you're running on a laptop and all the but most very high end laptops have pretty low spec video cards that use main memoery instead of dedicated onboard memory which seriously hampers performance.

XGL takes a few shortcuts and hammers your cpu (just check the output of top at the command line and move a wobbly window around) to make up for lack of acceleration hardware.

from what I can work out AIGLX needs some time to mature and get full hardware support.

This is conjecture though at this point, what video card do you have?

---

