---
title: "Ubuntu 14.04 xinput_calibration problem"
date: 2016-03-30
forum: Desktop Environments
---

### Post by vnv on 2016-03-30
Hi all,

I am trying to use 90 degrees clockwise rotated touch screen from elo (ET1509L-8UWA).
Settings in Ubuntu rotated it without problems but after xinput_calibrate axes seem inverted.

xinput list returns: 

> 
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB  id=10   [slave  pointer  (2)]
&#9116;   &#8627; PixArt HP USB Optical Mouse               id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; NOVATEK USB Keyboard                      id=12   [slave  keyboard (3)]
    &#8627; NOVATEK USB Keyboard                      id=13   [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                            id=14   [slave  keyboard (3)]



> 
xinput_calibrator --output-type xinput
        Setting calibration data: 0, 4095, 0, 4095
Calibrating EVDEV driver for "Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB" id=10
        current calibration values (from XInput): min_x=0, max_x=4095 and min_y=0, max_y=4095

Doing dynamic recalibration:
        Swapping X and Y axis...
        Setting calibration data: 3616, 3569, 1154, 1158
        --> Making the calibration permanent <--
  Install the 'xinput' tool and copy the command(s) below in a script that starts with your X session
    xinput set-int-prop "Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB" "Evdev Axis Calibration" 32 3616 3569 1154 1158
    xinput set-int-prop "Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB" "Evdev Axes Swap" 8 1





Could somebody help with this please?

---

### Post by vnv on 2016-04-01
Following link solved the issue: [https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation)

---

### Post by mörgæs on 2016-04-01
Good, please mark the thread 'solved'.

---

