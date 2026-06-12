---
title: "razer copperhead"
date: 2006-08-31
forum: Desktop Environments
---

### Post by larsemil on 2006-08-31
anyone know how to get the sidebuttons working?

when cheking i xev the buttons are numbered 8 and 9 and the wheel 4 5

my xorg looks like
```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Buttons" "9"
	Option	    "ButtonMapping" "1 2 3 8 9"
EndSection

```

anyone have a clue?

edit: i have some idea that the buttons are working but not properly, in firefox for instance, they are reacting as button 1, u can click with them.  i did not notice them in any other program so...

---

### Post by Scythe!? on 2006-08-31
Type sudo gedit /etc/X11/xorg.conf
in your mouse config (the section you posted)
delete your mouse config and paste this in its place.
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "Resolution" "2000"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection
```

---

### Post by larsemil on 2006-08-31
> **Scythe!? said:**
> Type sudo gedit /etc/X11/xorg.conf
in your mouse config (the section you posted)
delete your mouse config and paste this in its place.
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "Resolution" "2000"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection
```
well that did not help at all. no difference what so ever.

---

### Post by chammy on 2008-01-13
> **Scythe!? said:**
> Type sudo gedit /etc/X11/xorg.conf
in your mouse config (the section you posted)
delete your mouse config and paste this in its place.
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "Resolution" "2000"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection
```

Works great, thanks! I used this for the device line though:
```

    Option         "Device" "/dev/input/by-id/usb-Razer_Razer_Copperhead_Laser_Mouse-mouse"

```

Note that the two side buttons on the right adjust the DPI in the hardware if you aren't using the official Razer drivers. The two on the left work like normal, though.

---

### Post by Kokanee-YYZ on 2008-01-26
I pulled the Razer Copperhead config listed below from the forums.  My buttons are mapped as such in Firefox:

two left = go back one page in browser history
two right = go forward one page in browser history
scroll wheel = middle button

---start---

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "Resolution"            "2000"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse" "CorePointer"
EndSection

---stop---

Exactly what I needed :) .  Hope this help you!

>K<

---

