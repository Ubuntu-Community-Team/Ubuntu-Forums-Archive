---
title: "gdm stop issues"
date: 2006-11-08
forum: Desktop Environments
---

### Post by sarsparilla on 2006-11-08
I am having a problem when I use stop the gdm. I type ```
sudo /etc/init.d/gdm stop
``` and my laptop's monitor turns off. I can still input into the computer though because I was able to shutdown by typing my login info and ```
sudo shutdown -r now
``` I am using dapper and have a dell inspiron e1705 with nvidia 7800go if that info has any value to you. 

What do you think could be causing this?

EDIT: Also, when I restart x server with ctrl+alt+Backspace I get the same thing, as well as when I restart. When it scrolls through the list of actions that it is performing I just get a blank screen.

---

### Post by mssever on 2006-11-08
Do you also get the same problem if you try to switch to a virtual console (Ctrl+Alt+F1)? If so, then it sounds like your laptop screen is having trouble in text mode. Which is a hardware issue, I would guess.

---

### Post by sarsparilla on 2006-11-09
With your suggestion in mind I did a quick search of the forums and found this thread [http://ubuntuforums.org/showthread.php?t=247126&highlight=text+mode](http://ubuntuforums.org/showthread.php?t=247126&highlight=text+mode) where the user had the same issue. He was able to fix it by adding "vga=0" at the end of his /boot/grub/menu.lst. I'll try this tomorrow after school and report back with results.

---

### Post by sarsparilla on 2006-11-09
I tried the fix listed above and it does give me textmode, but it takes away my ability to use beryl as a window manager. Can you think of any other options available to allow me to get textmode working? 

This is my xorg.conf if it helps...
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "RenderAccel" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection


```

---

