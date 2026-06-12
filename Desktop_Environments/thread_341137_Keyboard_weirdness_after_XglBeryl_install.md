---
title: "Keyboard weirdness after Xgl/Beryl install"
date: 2007-01-18
forum: Desktop Environments
---

### Post by blueglow on 2007-01-18
Hello,

I'm pretty much a noob with Ubuntu/linux but I'm finding my feet ok so far.

I have a Sony Vaio laptop running Edgy and I installed the ATI Fglrx driver and my 3d performance is now a load better. I then installed Xgl and Beryl, created a new session for it and logged in according to a bunch of different guides. The Beryl/3d/swoobyness is fine, but my keyboard is being weird! - the Ctrl keys no longer work! Everything else appears fine and is set to the GB locale.

On session login I get a message saying my X keyboard settings differ from the Gnome and which to use (101 key GB vs 105 key US - a very confusingly worded dialog box IMO, plus it makes no difference which option I choose). Beryl starts and everything appears ok.

When I press ctrl, the boxes/diamonds mouse pointer highlight works fine so I know the keypresses are being received and the keyboard is working. Ctrl-v just types a "v" on the screen.

Here is my xorg.conf in case that helps.> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	Option	    "AIGLX" "true"
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
	Option	    "XkbLayout" "gb"
	Option	    "XkbOptions" "lv3:ralt_switch"
	Option      "XkbOptions" "ctrl:ctrl_aa"      <--- I just added this but it didn't help.
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
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Radeon Mobility X600"
	Driver      "ati"
	Option	    "XAANoOffscreenPixmaps"
	BusID       "PCI:3:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
#	Option "UseInternalAGPGART" "no"
#	Option "KernelModuleParm" "agplock=0"
EndSection

Section "Screen"
	Identifier "Sony Xbrite Display"
	Device     "Radeon Mobility X600"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1920x1200"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1920x1200"
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

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

As I said, all else works fine. Any suggestions/help would be great.

Thanks in advance,

Jim

---

### Post by souki on 2007-01-18
you say you use XGL but your config shows AIGLX
I have the same video card (ati mobility radeon x600) on a vaio, it's working very well
I've followed this howto [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

if you want my config files, I will watch this thread

~cheers

---

### Post by blueglow on 2007-01-18
Hello Suki, thanks for getting back to me.

I hadn't noticed the AIGLX option at the top, but the in the "Driver" section for the selected "aticonfig-Device[0]" graphics card shows **Driver "fglrx"** so I'm not sure. If you could send me/attach your xorg.conf file that would be great! Any other guidance greatly appreciated.

Also, is there a tool, or just some common knowledge that I'm missing, that lists the scripts that are run when one logs into an X/Gnome session? It's almost like the keyboard is being set twice...

Thanks again,

Jim

---

### Post by CowzRule on 2007-01-18
Change```
Option "AIGLX" "true"
```to```
Option "AIGLX" "false"
```
Try changing```
Option "XkbModel" "pc105"
```to```
Option "XkbModel" "pc104"
```Hope it helps.

---

### Post by blueglow on 2007-01-18
**CowzRule:** I made those changes, no dice. Beryl now no longer starts and the keyboard is still odd.

**Suki:** That link is the same one I used to install... it didn't work 100% so I googled around and found others, though when it has worked I've always had to manually start the beryl-manager cos it won't automatically. 



The more I log in/out and bounce X, the more I get the impression that my sessions are screwed up; if I change something in one, it changes the other, or sometimes not. It's not right either way.

What's the best way to get the sessions/X/XGL back to normal and start again? The ATI driver is fine, as is the Beryl install *when* the session works right. I'm unsure about Xgl and the sessions themselves. I have a load of backup xorg.conf files.

I feel it's a .sh file or .conf file problem, but I can't be sure - should I remove/reinstall everything from Xgl up and start again or try to fix?

If I can post any files to help, please just ask.

Thanks guys, really appreciate this.

Jim

---

### Post by CowzRule on 2007-01-18
Sorry my suggestions didn't work. :( 

It is my understanding that XGL is an overlay to your Gnome desktop. Think of XGL as more of a desktop manager rather than a separate session. When you log in to your normal Gnome session, any changes you do should be seen when you log into your XGL session and vise versa.
I could be way off on that, but that is the way I see it.

---

### Post by souki on 2007-01-18
hello again,

I remember having the same kind of trouble with keyboard, but I don't know how to fix it

try to start from un new account and see if it works

here is my xorg.conf :

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

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "fr"
    Option        "XkbVariant"    "latin9"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
    Driver        "fglrx"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1440x900"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1440x900"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1440x900"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1440x900"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1440x900"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1440x900"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
    Option "Composite" "disable"
    #Option "Composite" "enable"
EndSection

```/usr/bin/startxgl.sh

```

#!/bin/sh  

#this can fix keyboard problem 
#xmodmap /usr/share/xmodmap/xmodmap.fr

Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1

# Shutdown and reboot buttons in GNOME
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

exec gnome-session

```/usr/share/xsessions/xgl.desktop

```

[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```I don't use the gdm.conf-custom method

---

