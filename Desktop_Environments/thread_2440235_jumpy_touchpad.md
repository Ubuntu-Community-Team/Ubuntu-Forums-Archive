---
title: "jumpy touchpad"
date: 2020-04-07
forum: Desktop Environments
---

### Post by danielsender on 2020-04-07
This is quite strange. I have two identical machines (Latitude E6430ATG), both running 18.04 with the latest updates. One of them has no problem with the touchpad, while the other jumps when I touch the pad at the same time has the body of the machine. I ran 'xinput --list' on both machines getting the same output on both:
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=12   [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad          id=16   [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint Stick             id=17   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=10   [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                     id=11   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=14   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=15   [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                     id=18   [slave  keyboard (3)]
    &#8627; UVC Camera (046d:081a)                    id=13   [slave  keyboard (3)]

```

So I ran 'xinput -list-props 16 17', getting:

```
Device 'AlpsPS/2 ALPS DualPoint TouchPad':
    Device Enabled (175):    0
    Coordinate Transformation Matrix (177):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Tapping Enabled (329):    1
    libinput Tapping Enabled Default (330):    0
    libinput Tapping Drag Enabled (331):    1
    libinput Tapping Drag Enabled Default (332):    1
    libinput Tapping Drag Lock Enabled (333):    0
    libinput Tapping Drag Lock Enabled Default (334):    0
    libinput Tapping Button Mapping Enabled (335):    1, 0
    libinput Tapping Button Mapping Default (336):    1, 0
    libinput Natural Scrolling Enabled (311):    1
    libinput Natural Scrolling Enabled Default (312):    0
    libinput Disable While Typing Enabled (337):    1
    libinput Disable While Typing Enabled Default (338):    1
    libinput Scroll Methods Available (313):    1, 1, 0
    libinput Scroll Method Enabled (314):    1, 0, 0
    libinput Scroll Method Enabled Default (315):    1, 0, 0
    libinput Middle Emulation Enabled (318):    1
    libinput Middle Emulation Enabled Default (319):    1
    libinput Accel Speed (320):    0.000000
    libinput Accel Speed Default (321):    0.000000
    libinput Left Handed Enabled (325):    0
    libinput Left Handed Enabled Default (326):    0
    libinput Send Events Modes Available (296):    1, 1
    libinput Send Events Mode Enabled (297):    0, 0
    libinput Send Events Mode Enabled Default (298):    0, 0
    Device Node (299):    "/dev/input/event8"
    Device Product ID (300):    2, 8
    libinput Drag Lock Buttons (327):    <no items>
    libinput Horizontal Scroll Enabled (328):    1
Device 'AlpsPS/2 ALPS DualPoint Stick':
    Device Enabled (175):    0
    Coordinate Transformation Matrix (177):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Natural Scrolling Enabled (311):    0
    libinput Natural Scrolling Enabled Default (312):    0
    libinput Scroll Methods Available (313):    0, 0, 1
    libinput Scroll Method Enabled (314):    0, 0, 1
    libinput Scroll Method Enabled Default (315):    0, 0, 1
    libinput Button Scrolling Button (316):    2
    libinput Button Scrolling Button Default (317):    2
    libinput Middle Emulation Enabled (318):    0
    libinput Middle Emulation Enabled Default (319):    0
    libinput Accel Speed (320):    0.000000
    libinput Accel Speed Default (321):    0.000000
    libinput Accel Profiles Available (322):    1, 1
    libinput Accel Profile Enabled (323):    1, 0
    libinput Accel Profile Enabled Default (324):    1, 0
    libinput Left Handed Enabled (325):    0
    libinput Left Handed Enabled Default (326):    0
    libinput Send Events Modes Available (296):    1, 0
    libinput Send Events Mode Enabled (297):    0, 0
    libinput Send Events Mode Enabled Default (298):    0, 0
    Device Node (299):    "/dev/input/event7"
    Device Product ID (300):    2, 8
    libinput Drag Lock Buttons (327):    <no items>
    libinput Horizontal Scroll Enabled (328):    1
```

being the two outputs identical.

I'll appreciate any help.

---

### Post by danielsender on 2020-04-08
Any ideas? Perhaps I should post this in a different forum?

---

