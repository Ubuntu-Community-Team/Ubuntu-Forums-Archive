---
title: "Wacom issues"
date: 2007-06-08
forum: Desktop Environments
---

### Post by swizec on 2007-06-08
Hello all, 

I'm new to this distro (using kubuntu) having migrated from gentoo today and I have some issues with my wacom (Intuos 3). It works well as a mouse pointer and all the buttons and sliders on it work like they're supposed to.

The problem is that when I try drawing with it in Photoshop7 it doesn't detect pressure. If pressure sensitivity is turned off in the brush settings then I can draw with it, but otherwise there are no marks. If anyone can provide any help I'd be grateful.

This is the relevant part of my xorg.conf
```

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "USB" "on"                 # USB ONLY
        Option      "Mode" "Absolute"           # other option: "Absolute"
        Option      "Vendor" "WACOM"
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "USB" "on"                  # USB ONLY
        Option      "Mode" "Absolute"            # other option: "Absolute"
        Option      "Vendor" "WACOM"
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "USB" "on"                  # USB ONLY
        Option      "Mode" "Absolute"            # other option: "Absolute"
        Option      "Vendor" "WACOM"
EndSection

Section "InputDevice"
        Identifier  "pad"
        Driver      "wacom"
        Option      "Type" "pad"
        Option      "Device" "/dev/input/wacom"
        Option      "ButtonsOnly" "off"
        Option      "USB" "on"
EndSection
.
.
.
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "pad" "SendCoreEvents"
EndSection

```

If there's any other relevant configuration I'll post it.


I may have posted this before in a wrong place ...

---

