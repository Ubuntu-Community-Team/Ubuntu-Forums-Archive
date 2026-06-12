---
title: "Help me throw out M$ Windows"
date: 2008-03-25
forum: Desktop Environments
---

### Post by KrGAce on 2008-03-25
After a very successful Ubuntu Feisty install on my Dell Latitude D830, and having everything work great, I want to end my relationship with Windows on my desktop at home.  My problem is I have two Acer 22" monitors and Ubuntu finds the monitors fine, however it is stuck in "cloned" mode, meaning I have two identical desktops.  What I would like is "spanned" mode where one desktop covers both monitors.  That is the only thing preventing me from keeping Ubuntu at home.  I also have an Nvidia card that is somewhaty new (less than two years and has 256MB memory on it).


Can anyone help get me going?  Should I wait for gibbon?


Any help to get me going is appreciated in advance.


AceMan

---

### Post by insane_alien on 2008-03-25
gibbon is out already, it is hardy heron that is coming out in april, it does support dual monitors better(i'm told) but you may still have to tweak the files manually to get what you want. but once it's done its done.

---

### Post by pseudo-random on 2008-03-25
I use Gutsy on a dell with dual monitors and an ATI card though I've had it working with NVIDIA.
There's plenty good guides out there and ways to do it.
Either learn to edit your xorg.conf in the  /etc/X11/ folder (please be careful!) or use the nvidia GUI,
called nvidia-settings-manager, it's pretty easy with that.

---

### Post by pseudo-random on 2008-03-25
Here's my Xorg.conf. This is only for reference, I can't guarantee this will work for your setup!

Section "ServerLayout"

        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load "dri"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal" # << here's the widescreen bit
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Modes    "3360x1050" "1680x1050" "1440x900" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

---

### Post by KrGAce on 2008-03-25
Sorry on the gibbon/heron error.  I knew what I was talking about just didn't type it.  I have tried to edit the X.org file and screwed things up, and I have used the Nvidia tool, and either it gets messy or it reboots and I get a blank screen (Ubuntu wallpaper) with a black vertical stripe (about 4" wide) down the left side of one of my monitors.

I would really love to get this working, but don't know how.


AceMan

---

### Post by KrGAce on 2008-03-25
Can I post my Xorg file? Would that help anyone to help me?  Just a thought, I really want to format and get rid of this Windows box.


Many thanks,


AceMan

---

