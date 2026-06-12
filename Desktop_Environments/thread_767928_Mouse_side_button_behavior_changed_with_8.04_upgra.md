---
title: "Mouse side button behavior changed with 8.04 upgrade"
date: 2008-04-26
forum: Desktop Environments
---

### Post by Explodinglemur on 2008-04-26
In 7.10, when I clicked the side button on my mouse it would act as the Back button in Firefox.  With the 8.04 upgrade, the side button no longer works in this way.

Relevant section of xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"       "6"
        Option          "ButtonMapping" "1 2 3 6"
EndSection
```

This appears to be correct...the mouse has two primary buttons, a wheel with a button underneath, and the side button.  The left/right and middle clicks work properly, as well as the scroll wheel.

---

### Post by mrazster on 2008-04-26
I don't know wht kind of mouse you're using....but I'm using a Logitech G7..and this xorg settings works for me:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option          "Device"                "/dev/input/mice"
    Option          "Protocol"              "ExplorerPS/2"
    Option          "Emulate3Buttons"       "false"
    Option          "Buttons"               "7"
    Option          "ZAxisMapping"          "4 5"
    Option          "ButtonMapping"         "1 2 3 6 7"
    Option          "Resolution"            "100"
EndSection
```

---

### Post by Explodinglemur on 2008-04-26
I'm using a Logitech MouseMan Dual optical mouse.  Settings are almost identical to yours, except this is a 6-button mouse, not 7.

I just watched /dev/input/mice (with cat) and did see stuff happen when I clicked the sixth button, so the button press is being captured by the mouse driver.  I don't know why it's not being picked up by X appropriately.

---

