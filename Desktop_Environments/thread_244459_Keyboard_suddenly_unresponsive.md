---
title: "Keyboard suddenly unresponsive?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Ygramul on 2006-08-26
I have a new install of Ubuntu up and running.  Everything was going fine.  I installed Wine, got all my hardware working, all my shares mounted, etc.  

I went to reboot, and when it reloaded, my keyboard (PS/2) wasn't working.  The keyboard light was powered on, and my mouse worked, but I couldn't type anything at all.  

I tried rebooting a couple more times, nothing.
I tried replugging the keyboard in, nothing.
I tried messing with the keyboard options in the Preferences panel, nothing.

I know the keyboard works because the light is on, and I can access the BIOS during post.  

As far as I know, I wasn't doing anything prior to the reboot that dealt with my keyboard settings.  I had edited the fstab to auto-mount my other hard drive, and I had copied over all my old files from a Windows share.  

I can ssh to the machine from my laptop, so if I need to edit some config files or something, I believe I can do it that way (I can, right?).  

Any ideas?

---

### Post by Pragmatist on 2006-08-26
> **Ygramul said:**
> I have a new install of Ubuntu up and running.  Everything was going fine.  I installed Wine, got all my hardware working, all my shares mounted, etc.  

I went to reboot, and when it reloaded, my keyboard (PS/2) wasn't working.  The keyboard light was powered on, and my mouse worked, but I couldn't type anything at all.  

I tried rebooting a couple more times, nothing.
I tried replugging the keyboard in, nothing.
I tried messing with the keyboard options in the Preferences panel, nothing.

I know the keyboard works because the light is on, and I can access the BIOS during post.  

As far as I know, I wasn't doing anything prior to the reboot that dealt with my keyboard settings.  I had edited the fstab to auto-mount my other hard drive, and I had copied over all my old files from a Windows share.  

I can ssh to the machine from my laptop, so if I need to edit some config files or something, I believe I can do it that way (I can, right?).  

Any ideas?

Yes, ssh is a good idea and should work.

Please post the contents of  **/etc/X11/x.org **

---

### Post by Ygramul on 2006-08-26
I did another reboot, and it started working again, although I had done nothing else to it.  Very strange.

Here's the output of xorg.conf

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
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
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
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

```

---

### Post by Pragmatist on 2006-08-26
> **Ygramul said:**
> I did another reboot, and it started working again, although I had done nothing else to it.  Very strange.

Here's the output of xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
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
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc104"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "SyncMaster"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
    Driver      "ati"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
    Monitor    "SyncMaster"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
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

```

Looks normal to me.  I have the exact same entry for my keyboard.  It may have been something strange that won't come back.  I would definitely make sure my system was fully up to date.

If it happens again, if you can ssh into the machine, and you want to fiddle around, then try killing  X and the gdm processes.  If you consistently get the problem, you could try booting into a text-only environment (you set the default runlevel in /etc/inittab to 3 I think)  Then try starting X without gdm.

---

### Post by Ygramul on 2006-08-26
Hopefully it was just a fluke.  

Thanks for your help though.  It is greatly appreciated!

---

