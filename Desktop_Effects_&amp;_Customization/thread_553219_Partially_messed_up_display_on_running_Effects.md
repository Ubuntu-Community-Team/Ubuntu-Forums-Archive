---
title: "Partially messed up display on running Effects"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by germclown on 2007-09-17
Hi, My ubuntu + fusion install worked perfectly on my desktop box, but my lappy is having issues. Everything's fine until I enable either desktop effects (pre-Fusion) or compiz (post-Fusion install) then:
- right third of screen gets distorted and noised-out
- all existing windows can be moved into the broken area where they distort, but they return to normal as I pull them out
- all buttons/icons disappear along with the panels (but only in the affected area)
- disabling effects does not fix it; cannot re-enable after disabling

No guides seem to even mention this, so I'm stumped

I'm using a Compaq Evo n610c (Radeon m7500) with a fresh install of Feisty (apart from Fusion)

Any help is appreciated, though my Linux skills are minimal

---

### Post by Forlong on 2007-09-17
Do you use the fglrx driver with Xgl for your ATI card?
And did you install the latest driver from ATI yourself (or with envy)?

---

### Post by germclown on 2007-09-18
Hmm... worth a try, but the guide I used said Feisty should have given me the necessary driver. I'll post the results.

---

### Post by germclown on 2007-09-18
Okay, after looking around and trying a few things:
- Envy won't work 'cause it's for newer ATI cards (9000 series + or something, anyways, newer than mine)
- For the same reason, apparently, I can't use the fglrx drivers
- I've found guides for Beryl (specific to my card) that I thought, might work, but no change at all. These guides involved non-Xgl solutions (I can't find anything for Xgl)

So many people seem to have my card or my laptop, I'd have thought this would be more common...

---

### Post by Forlong on 2007-09-19
> **germclown said:**
> Hmm... worth a try, but the guide I used said Feisty should have given me the necessary driver. I'll post the results.
Oh God, no... those were just *questions*, not recommendations!

So please tell us how you installed Compiz and post the output of
```
grep -v ^# /etc/X11/xorg.conf
``` in the terminal (please use the forum's CODE tags for that)

---

### Post by germclown on 2007-09-19
Here's the xorg.conf

*****

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
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
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

*****

Compiz-Fusion is currently installed as per your own recommendations, except for the automatic startup part (ie. I still have to run "compiz --replace" each time). SexyPython is in, but no Emerald.

And oops on the over-eagerness. If you think any serious action like a re-install is necessary, let me know.

Btw... Thanks for your time so far

---

### Post by germclown on 2007-09-19
Hmm... just realized that the effects actually work (after another attempt at starting it up). The animations are running smoothly and properly. I can switch desktops and everything. I just can't see the window frames (but I can manipulate them), and the desktop itself looks white except for the black or distorted bar on the right. Interestingly, the edge of the panels and the edge of the white part have been given a shadow.

---

### Post by Forlong on 2007-09-19
Try adding
```
Option "XaaNoOffscreenPixmaps" "1"
```
to the *Section "Device"*

---

### Post by germclown on 2007-09-19
The only noticeable difference is that left 100 pixels or so now gets duplicated on the right edge of the screen, but only after switching desktops (I'm using default compiz-fusion settings right now).

Another note: windows I open *after* I run compiz look fine, but the old windows keep their blanked-out borders. I don't know if that is new or not, though.

---

### Post by weizilla on 2007-09-19
I have the same exact problem as you only my video card is an ATI Mobility 9000 on an IBM T40 laptop. I made a thread about this but unfortunately no one answered :(. 

Just for reference (and screenshot of problem): [http://ubuntuforums.org/showthread.php?t=549482](http://ubuntuforums.org/showthread.php?t=549482)

I hope someone solves this problem because I really like all the cool desktop effects.

---

### Post by germclown on 2007-09-20
This seems to be a video card problem, so I'm gonna try starting this up in the other forum.

---

### Post by nikoPSK on 2007-09-20
try envy that worked for me... exept if you have an ATI card try... iunno my compiz has been having problems lately too...:(

---

### Post by Pathfinder_ on 2007-09-22
I don't know if u solved the problem but if you haven't, try changing your depth to 16-bit instead of 24. It worked for me, so hopefully it'll work for you.

---

### Post by weizilla on 2007-09-22
> **Pathfinder_ said:**
> I don't know if u solved the problem but if you haven't, try changing your depth to 16-bit instead of 24. It worked for me, so hopefully it'll work for you.

edit: changed the wrong setting at first. after changing the correct one to 16, it worked !!! :D :D

am i going to notice any difference in how things look between 16 and 24 bit?

---

### Post by Pathfinder_ on 2007-09-22
I, perosnally, don't notice any difference on my laptop and congratz on getting it work. i had the same issie and it took me long hours of googling to find the solution.

---

### Post by nikoPSK on 2007-09-23
Srry, actually envy has ATI drivers too:KS

---

