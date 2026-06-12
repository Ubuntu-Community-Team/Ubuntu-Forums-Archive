---
title: "Unable to enable 3D graphics"
date: 2007-10-23
forum: Desktop Environments
---

### Post by gutsyuser on 2007-10-23
I have ATI Radeon X600 128 MB video card. I dont know whether compiz fusion supports with this video card in Ubuntu 7.10 Gutsy Gibbon.
When I try to enable 3D graphics from System->Preferences->Appearance->Visual Effects, it says "Desktop Environment could not be enabled."
Can anyone help me out.

---

### Post by stixguy on 2007-10-23
Can you provide me with two pieces of information?

What monitor do you have (brand and model)?

And, the output of:

```
cat /etc/X11/xorg.conf
```

I"ll be happy to see if I can help.

---

### Post by mythloaf on 2007-10-24
hi Me Desktop Environment could not be enabled."

Im using ati RV300 with Dell 17" monitor.

---

### Post by gutsyuser on 2007-10-24
Hi stixguy,
I have a Dell 1901FP monitor (flat screen)

Do I have to change anything in Section "Extensions"

the xorg file is:

Section "Files"
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
        Identifier      "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
        Driver          "ati"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL 1901FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
        Monitor         "DELL 1901FP"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "1"
EndSection

---

### Post by stixguy on 2007-10-25
I would try adding this to the "Monitor Section" so yours looks like this:

```
Section "Monitor"
Identifier "DELL 1901FP"
HorizSync     30-80 
VertRefresh  56-76
Option "DPMS"
EndSection
```

Let me know what that does.

FYI: The HorizSync and VertRefresh rates are from [http://support.dell.com/support/edocs/monitors/1901FP/en/specs.htm]("http://support.dell.com/support/edocs/monitors/1901FP/en/specs.htm")

---

### Post by stixguy on 2007-10-25
> **mythloaf said:**
> hi Me Desktop Environment could not be enabled."

Im using ati RV300 with Dell 17" monitor.

Can you cut and paste the output of:

```
cat /etc/X11/xorg.conf
```

Also, can you specify the model number of your monitor?

Thanks!

---

### Post by gutsyuser on 2007-11-03
hi stixguy, sorry for being late..
anyway, that didn't change even after adding the code u gave me for monitor section. It is still showing: "Desktop effects couldn't be enabled."

---

### Post by chuchan on 2007-12-30
hey it worked 4 me... thnx.....

---

