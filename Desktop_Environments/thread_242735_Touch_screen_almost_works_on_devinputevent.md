---
title: "Touch screen almost works on /dev/input/event*"
date: 2006-08-24
forum: Desktop Environments
---

### Post by skcoyote on 2006-08-24
Howdy all,                                                            
                                                                      
Please don't let the long post scare you off. I'll cut straight to my question:
    
**Is there a canonical procedure for configuring a generic touch screen using /dev/input/event* in Ubuntu?**

Hopefully I'm missing something simple, but I've already invested a few solid hours scouring Google results.

Here's a detailed description of what I've tried today:

I have a USB touch screen that detects as "USB Touchscreen 0eef:0001", outputs sane data on /dev/input/mouse1 (useless relative movements), /dev/input/ts1 (reasonable absolute coordinates), and /dev/input/event2 (which works fine with evtest--output near the end of this post).

It looks like the /dev/input/event2 device is working fine and outputting usable data. I haven't been able to configure xorg to (properly) use this device, though.

For my intended application, I only need the basics... Touch/Reset, and the Absolute coordinates. I've already hacked up a trivial 20 line C program that accurately gets all the data I would need from /dev/input/ts1, so I know the screen can work, but I'd much rather let X handle the input.


evtest /dev/input/event2 output:

```
Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0xeef product 0x1 version 0x100
Input device name: "USB Touchscreen 0eef:0001"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
    Event code 3 (Absolute)
  Event type 1 (Key)
    Event code 330 (Touch)
  Event type 3 (Absolute)
:    Event code 0 (X)
      Value    280
      Min        0
      Max     2047
    Event code 1 (Y)
      Value    499
      Min        0
      Max     2047
Testing ... (interrupt to exit)
Event: time 1156400532.394902, type 1 (Key), code 330 (Touch), value 1
Event: time 1156400532.394912, type 3 (Absolute), code 0 (X), value 1151
Event: time 1156400532.394921, type 3 (Absolute), code 1 (Y), value 928
Event: time 1156400532.394931, type 0 (Reset), code 0 (Reset), value 0
Event: time 1156400532.398895, type 1 (Key), code 330 (Touch), value 0
Event: time 1156400532.398905, type 0 (Reset), code 0 (Reset), value 0 
```

C program output (reads /dev/input/ts*)

```
ts(X) 00000001 x =  19, y =  16 # upper right
ts(X) 00000000 x =  19, y =  16
ts(X) 00000001 x = 116, y = 128 # middle
ts(X) 00000000 x = 116, y = 128
ts(X) 00000001 x = 215, y = 264 # lower left
ts(X) 00000000 x = 215, y = 264
```

I've tried the following InputDevice config:
    
```
Section "InputDevice"
        Identifier "evtouch screen"
        Driver     "evtouch"
        Option     "Device"           "/dev/input/event2"
        Option     "ReportingMode"    "Raw"
        Option     "SendCoreEvents"
EndSection
```

With this config, I get more-or-less absolute clicks/jumps when I tap the screen, but the range is limited (no matter what I set (Min|Max)[XY] to), and there seem to be overflow issues... for example, once I get to a certain Y coordinate towards the bottom of my screen, the cursor jumps to the extreme top of the screen. I'm guessing I need to specify a different Protocol/Driver, but I spent an hour or so trying different permutations, with no more luck (not to mention a few spectacular failures).

I should also note that this is a 4 display system--the touch screen, plus three other monitors--and, with this InputDevice config, the cursor seems stuck on Screen 0 (which is NOT the touch screen... that's Screen 3).

Somewhat interestingly, if I use /dev/input/mouse1 and the "mouse" Driver, I get relative motion that will span adjoining displays. (So, good test, but it's relative motion, which is next to useless for touch input).

evdev.ko is loaded:

```
  pts/2 skcoyote@localhost:/etc/X11 $> lsmod | grep evdev
  evdev                   9088  2


```Relevant bits from Xorg.0.log:
```

(II) LoadModule: "evtouch"
(II) Loading /usr/X11R6/lib/modules/input/evtouch_drv.o
(II) Module evtouch: vendor="Kenan Esau (rc1)"
        compiled for 4.3.99.902, module version = 0.8.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
[...]
(**) Option "Device" "/dev/input/event2"
evdev device opened successfully
QUERY HARDWARE
(**) Option "DeviceName" "touchscreen"
(**) Option "SendCoreEvents"
(**) touchscreen: always reports core events
(II) XINPUT: Adding extended input device "touchscreen" (type: TOUCHSCREEN)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)

```


[B]Any ideas as to how I could configure X, here, would be greatly appreciated!
[/B]


- skcoyote

---

### Post by florizs on 2006-11-23
I have a touchscreen which has the same problems. except it outputs to /dev/ttyS3 instead of /dev/input. Would your script be usable for my problem?
thanks in advance

---

