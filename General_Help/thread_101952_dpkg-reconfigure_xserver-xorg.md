---
title: "dpkg-reconfigure xserver-xorg"
date: 2005-12-11
forum: General Help
---

### Post by fontosaurus on 2005-12-11
So, in messing around with dpkg-reconfigure xserver-xorg, I've gotten the laptop to recognize that 1280x800 is the resolution I want to be running at.  The problem is, I have to go through this routine every time I boot up, and it's getting moderately to completely tiresome.

I'm using the following:
sudo dpkg-reconfigure xserver-xorg

And after I get to the very end, it asks me if I want to autodetect my video card.  I do so, and it reverts to the command line, only to offer up the login screen a moment later with the resolution fixed.

I cannot, for the life of me, figure out why this is.

---

### Post by aysiu on 2005-12-11
It's not something that can be solved with something so simple as System > Preferences > Screen Resolution and checking the box at the bottom, is it?

Or maybe System > Preferences > Sessions and saving session at logout...?

---

### Post by fontosaurus on 2005-12-11
[QUOTE=aysiu]It's not something that can be solved with something so simple as System > Preferences > Screen Resolution and checking the box at the bottom, is it?[/QUOTE]

Alas, no.  It's not an option in the Screen Resolution preferences until after I manually update it from the command line, as detailed above.

[QUOTE=aysiu]Or maybe System > Preferences > Sessions and saving session at logout...?[/QUOTE]

That didn't seem to work, either.  

At this point, I got nothin'.

---

### Post by dcstar on 2005-12-11
[QUOTE=fontosaurus]So, in messing around with dpkg-reconfigure xserver-xorg, I've gotten the laptop to recognize that 1280x800 is the resolution I want to be running at.  The problem is, I have to go through this routine every time I boot up, and it's getting moderately to completely tiresome.

I'm using the following:
sudo dpkg-reconfigure xserver-xorg

And after I get to the very end, it asks me if I want to autodetect my video card.  I do so, and it reverts to the command line, only to offer up the login screen a moment later with the resolution fixed.

I cannot, for the life of me, figure out why this is.[/QUOTE]
Post your /etc/X11/xorg.conf file for people to have a look at.

---

### Post by fontosaurus on 2005-12-11
[QUOTE=dcstar]Post your /etc/X11/xorg.conf file for people to have a look at.[/QUOTE]
Here you go:

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
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
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "DPMS"
        #Modeline       "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by Ocxic on 2005-12-11
when asked to auto-detect try saying NO and set it up manually, see if that works.

---

### Post by az on 2005-12-11
I think you are booting and starting X, but failing.  You may have the Xserver running while you run dpkg-reconfigure xserver-xorg and that sometimes can cause misconfigurations.

Try booting into recovery mode and reconfiguring.


Then, to switch to desktop mode run
init 2

See if that puts you right.

---

