---
title: "Blank maximized windows with compiz"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by Zxaos on 2007-09-19
Hey all, I'm running the version of compiz that shipped with feisty (I  believe it's compiz 0.3.6) however sometimes when I open a new window, it is blank or black until the window is un-maximized and then re-maximized.

I've searched and most of the other posts about problems with maximized windows deal with title bars not appearing - but those are fine for me, it's the actual window content that isn't there.

This issue is *really* inconsistent. I can go a whole day without it happening, and then it will happen five times in a row.  It seems to be mostly firefox that this issue affects, although I have seen it affect other programs too.

Has anyone else encountered this issue? If so, have any advice?

---

### Post by Forlong on 2007-09-19
Could you please tell us what graphics card you are using and which driver?

And you also might want to change that you're on Breezy in your profile ;)

---

### Post by Zxaos on 2007-09-19
(Ack, I completely missed that I hadn't updated that.)

I'm running an Intel GMA X3100.

The driver I have listed in my xorg.conf is simply 'intel'.

Edit: I also just realized I should probably include something else that might be related. Although X.org looks to me like it's running in 24-bit mode, I'm getting banding in gradients. Not sure if that's related at all, but if this whole thing is a driver issue...

---

### Post by kungfoofairy on 2007-09-20
mispost

---

### Post by nuclearj on 2007-09-22
I get the same black/blank screen too.  I belive I am using a nvida card with the built in driver.  Who do I find out exactly?

---

### Post by Forlong on 2007-09-22
> **nuclearj said:**
>  I belive I am using a nvida card with the built in driver.  Who do I find out exactly?
Post the output of this:
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by nuclearj on 2007-09-22
> **Forlong said:**
> Post the output of this:
```
grep -v ^# /etc/X11/xorg.conf
```

```
Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV11 [GeForce2 Go]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-70
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV11 [GeForce2 Go]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

Here you go!

---

### Post by nuclearj on 2007-09-22
So i figured out that emerald is what gives you all the skins for the windows and compiz gives you all those cool effects (like the airplane window flying in and then flying out-.  And you use "metacity --replace" do go back to the default...  GUI manager?

All this is really cool but my firefox browser screen turns to all black, and it almost always happens.  And some times it's okay, but it is only one window I can use.  Also when I bring up the terminal, its window is totally transparent.  I have a border with no window that I can see directly underneath!

I've looked on the forums and have not found anything yet so if someone has any ideas that would be cool.  I'll get a screen shot of what I'm talking about soonly.  Thanks!

UPDATE--------------
I noticed that the window turns black/blank once a certain size is reached, and then from there on up it stays blank.

---

### Post by Forlong on 2007-09-23
> **nuclearj said:**
> So i figured out that emerald is what gives you all the skins
Not quite. The "skins" are GTK-themes. Emerelad is only responsible for the window boarders (titlebars).
> **nuclearj said:**
> for the windows and compiz gives you all those cool effects (like the airplane window flying in and then flying out-. 
That's right.
> **nuclearj said:**
> And you use "metacity --replace" do go back to the default...  GUI manager?
*Window* manager, yes.
> **nuclearj said:**
> All this is really cool but my firefox browser screen turns to all black, and it almost always happens.
You are experience the infamous *black window bug* - it's finally fixed with latest Ndivia drivers. It will be included in Gutsy.
> **nuclearj said:**
> Also when I bring up the terminal, its window is totally transparent.  I have a border with no window that I can see directly underneath!
Open the terminal and got to  *Edit &#8594; Current Profile &#8594; Effects* and increase the setting at *Transparent background*.

---

### Post by Zxaos on 2007-09-23
> **Zxaos said:**
> I also just realized I should probably include something else that might be related. Although X.org looks to me like it's running in 24-bit mode, I'm getting banding in gradients. Not sure if that's related at all, but if this whole thing is a driver issue...

Update: Ok, it looks like that actually is a driver issue and is fixed in Gutsy.

Doesn't help with the blank windows problem, though. :(

---

