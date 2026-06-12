---
title: "Trackpad on a Thinkpad"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Molerat on 2005-10-22
I posted a thread about this earlier, just as Breezy was gearing for release, so it was lost in the shuffle.

I would like to know if there is something specific I need to do to change the settings for the trackpad on my Thinkpad (T41).  I can't get it to behave the same way it does under Windows, and it really is driving me insane.  It's the little things that matter, and my miscalibrated trackpad really kills the Ubuntu experience for me.

I know it's Synaptics, I think I have the special Synaptics software set up, and, with a USB mouse hooked up, I see three entries in /dev/input/ -- mouse0, mouse1, mouse2

But no matter what I do, all changes seem to effect the nibble and the nibble only.  I'm sure I'm just missing a setting in my xorg conf file or something, but I have no idea what it could be.  Could someone help me out?

---

### Post by snarkout on 2005-10-22
Post specific problems you're having, and you'll likely get a better response.

---

### Post by Molerat on 2005-10-23
My specific problem is that I can't get mouse settings to apply to the trackpad, they only effect the keyboard nibble.

I'd post configuration files, etc., but I do not know what is relevant.

---

### Post by Molerat on 2005-10-23
Okay, maybe I was a little light on detail.  I'll give you everything I know, because this is incredibly frustrating!

I have an IBM ThinkPad, T41.  It has three mice:

1) Keyboard nibble,
2) Trackpad,
3) USB mouse

Of the three, I actually prefer to use the trackpad; however, it is too sensitve for me.  Tapping works fine, scrolling works fine, it's just too sensitive.  I would like to change that.  Unfortunately, when I go to System > Preferences > Mouse to change things, on (1) and (3) are effected.  (2), the trackpad, seems to have its own settings.

I've done some digging on the forums.  The first thing seems to be to confirm that I do, in fact, have a Synaptics touchpad.  According to /var/log/Xorg.0.log:

```

root@nixon:~# cat /var/log/Xorg.0.log | grep synaptics
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
(--) Synaptics Touchpad synaptics touchpad found
(--) Synaptics Touchpad synaptics touchpad found
(--) Synaptics Touchpad synaptics touchpad found
(--) Synaptics Touchpad synaptics touchpad found

```

The next thing is to make sure Xorg.conf is set up right.  Here's what is has to say:

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
        Option          "SHMConfig"             "on"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
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

I've seen some threads that suggest that the SHMConfig option has something to do with something, but it is enabled, so I don't think that's it.

The only thing that jumps out at me is that there are two InputDevices:  a "Configured Mouse" and a "Synaptics Trackpad."  If I had to guess, and that's all it is, I would say that the nibble and USB mouse are covered under the "Configured Mouse" section, and that is what the Mouse Preferences applet changes.

So my question, which I think is about as specific as I can get:

How can I change the settings of the trackpad?  Can I make the Mouse Preferences applet adjust the trackpad settings?  I don't really know WHAT settings I want to update on the trackpad, I'd like to have a GUI to play with.  Does this help clarify my question?  Are there other details I can provide?

---

### Post by gillion on 2005-10-23
You can set the maximum tap time to zero in your **xorg.conf** file like so...

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "MaxTapTime"            "0"
        Option          "SHMConfig"           "true"
EndSection

```

or you can download and install this application.

[http://gnomefiles.org/app.php?soft_id=956](http://gnomefiles.org/app.php?soft_id=956)

[quote="About Gsynaptics"]
A GUI setting tool for Synaptics touchpad driver.
 
Set scrolling and taping preferences.
 
Requirements
This application requires GTK+ version 2.6.x. Other dependencies include:
GConf. 
[/quote]

[img]http://gsynaptics.sourceforge.jp/images/gsynaptics2.png[/img]

I already use ksynaptics on my SuSE 9.2 install and the xorg.conf on my ubuntu laptop (r40)

---

### Post by Molerat on 2005-10-26
Thank you for this.  My situation is much improved.

I'm still having some issues with acceleration (or some other parameter).  I think I'll have to trudge through /usr/share/doc/xorg-driver-synaptics for full details.  Ugh!

Edit - All right, i think I've got it.  Using synclient, I set some parameters, and it looks about like this:

```

    MinSpeed             = 0.04
    MaxSpeed             = 0.12
    AccelFactor          = 0.0001

```

I may tweak a little more, but this is pretty good.

---

### Post by kroiz on 2005-10-28
[QUOTE=Molerat]
Edit - All right, i think I've got it.  Using synclient, I set some parameters, and it looks about like this:

```

    MinSpeed             = 0.04
    MaxSpeed             = 0.12
    AccelFactor          = 0.0001

```

I may tweak a little more, but this is pretty good.[/QUOTE]
Thanks Molerat.
I got ibm t41 too, can you please specify where to put these valuse? somewhere in xorg.conf ?

---

### Post by kroiz on 2005-10-29
here is the only section I changed in /etc/X11/xorg.conf. 
and it works great for me.
 
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
# taken from http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad
        Option          "LeftEdge"      "1700"
        Option          "RightEdge"     "5300"
        Option          "TopEdge"       "1700"
        Option          "BottomEdge"    "4200"
        Option          "FingerLow"     "25"
        Option          "FingerHigh"    "30"
        Option          "MaxTapTime"    "180"
        Option          "MaxTapMove"    "220"
        Option          "VertScrollDelta" "100"
        Option          "MinSpeed"      "0.09"
        Option          "MaxSpeed"      "0.18"
        Option          "AccelFactor"   "0.0001"
        Option          "SHMConfig"     "on"
EndSection

```

---

