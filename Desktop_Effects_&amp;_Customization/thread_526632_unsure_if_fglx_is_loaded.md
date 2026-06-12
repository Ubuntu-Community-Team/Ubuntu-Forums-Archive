---
title: "unsure if fglx is loaded"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by pfwd.tech on 2007-08-15
I have installed fglrx for my ATI x550 card and are not sure if it is loaded correctly.
after typeing this (from [http://wiki.cchtml.com/index.php/Frequently_Asked_Questions](http://wiki.cchtml.com/index.php/Frequently_Asked_Questions))
```
less /var/log/Xorg.0.log
```
I get these errors:
```

(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from li
st!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from l
ist!


```

Is there something wrong with my fonts?

---

### Post by kellemes on 2007-08-15
What does "fglrxinfo" show?

---

### Post by pfwd.tech on 2007-08-16
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)

```
But nothing has changed in terms of the graphics.  The fonts still look fuzzy and everything seems a bit pixelated.

---

### Post by kellemes on 2007-08-16
Well, at least fglrx is running ;)

Have you chosen the best resolution, refreshrate and colordepth?
Can you post xorg.conf please?

Edit: By the way, as far as I know the errors in the log you can ignore..

---

### Post by pfwd.tech on 2007-08-16
Ok I'm away from my Linux box at the moment. I will post back in the morning with the answer.
What's the Bash script to check these preferences?  I haven't changed any of them so i guess they would be all set to default.

---

