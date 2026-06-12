---
title: "Mapping unknown keyboard scancodes"
date: 2014-03-07
forum: Desktop Environments
---

### Post by joostw on 2014-03-07
Hey guys,

recently I got this shiny new ThinkPad T440s, which works amazingly well with Linux. Now I am trying to solve a minor nuisance regarding the function keys.
The extra functions on the keys F1 to F8 work out of the box and have the correct mapping/function.
But I have no desktop response and in fact can not set any shortcut to the function side of F9 to F12 because GTK/Unity/X.org can not resolve the four different buttons, which are all mapped to the same keyocde.

evtest gives me this (first pressing the correctly mapped F7, then F9 to F12):

```

No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:      Lid Switch
/dev/input/event1:      Sleep Button
/dev/input/event2:      Power Button
/dev/input/event3:      AT Translated Set 2 keyboard
/dev/input/event4:      Video Bus
/dev/input/event5:      HDA Intel HDMI HDMI/DP,pcm=8
/dev/input/event6:      HDA Intel HDMI HDMI/DP,pcm=7
/dev/input/event7:      HDA Intel HDMI HDMI/DP,pcm=3
/dev/input/event8:      ThinkPad Extra Buttons
/dev/input/event9:      HDA Intel PCH Headphone
/dev/input/event10:     HDA Intel PCH Mic
/dev/input/event11:     SynPS/2 Synaptics TouchPad
/dev/input/event12:     Integrated Camera
/dev/input/event13:     TPPS/2 IBM TrackPoint
Select the device event number [0-13]: 8
Input driver version is 1.0.1
Input device ID: bus 0x19 vendor 0x17aa product 0x5054 version 0x4101
Input device name: "ThinkPad Extra Buttons"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 113 (KEY_MUTE)
    Event code 114 (KEY_VOLUMEDOWN)
    Event code 115 (KEY_VOLUMEUP)
    Event code 142 (KEY_SLEEP)
    Event code 148 (KEY_PROG1)
    Event code 152 (KEY_SCREENLOCK)
    Event code 190 (KEY_F20)
    Event code 191 (KEY_F21)
    Event code 194 (KEY_F24)
    Event code 205 (KEY_SUSPEND)
    Event code 212 (KEY_CAMERA)
    Event code 224 (KEY_BRIGHTNESSDOWN)
    Event code 225 (KEY_BRIGHTNESSUP)
    Event code 227 (KEY_SWITCHVIDEOMODE)
    Event code 228 (KEY_KBDILLUMTOGGLE)
    Event code 236 (KEY_BATTERY)
    Event code 238 (KEY_WLAN)
    Event code 240 (KEY_UNKNOWN)
    Event code 372 (KEY_ZOOM)
    Event code 466 (KEY_FN_F1)
    Event code 475 (KEY_FN_F10)

   Event code 475 (KEY_FN_F10)
    Event code 476 (KEY_FN_F11)
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 5 (EV_SW)
    Event code 3 (SW_RFKILL_ALL)
Properties:
Testing ... (interrupt to exit)
Event: time 1394216428.210851, type 4 (EV_MSC), code 4 (MSC_SCAN), value 06
Event: time 1394216428.210851, type 1 (EV_KEY), code 227 (KEY_SWITCHVIDEOMODE), value 1
Event: time 1394216428.210851, -------------- SYN_REPORT ------------
Event: time 1394216428.210944, type 4 (EV_MSC), code 4 (MSC_SCAN), value 06
Event: time 1394216428.210944, type 1 (EV_KEY), code 227 (KEY_SWITCHVIDEOMODE), value 0
Event: time 1394216428.210944, -------------- SYN_REPORT ------------
Event: time 1394216434.146090, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1c
Event: time 1394216434.146090, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 1
Event: time 1394216434.146090, -------------- SYN_REPORT ------------
Event: time 1394216434.146173, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1c
Event: time 1394216434.146173, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 0
Event: time 1394216434.146173, -------------- SYN_REPORT ------------
Event: time 1394216435.273005, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1d
Event: time 1394216435.273005, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 1
Event: time 1394216435.273005, -------------- SYN_REPORT ------------
Event: time 1394216435.273082, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1d
Event: time 1394216435.273082, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 0
Event: time 1394216435.273082, -------------- SYN_REPORT ------------
Event: time 1394216435.677415, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1e
Event: time 1394216435.677415, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 1

Event: time 1394216435.677415, -------------- SYN_REPORT ------------
Event: time 1394216435.677498, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1e
Event: time 1394216435.677498, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 0
Event: time 1394216435.677498, -------------- SYN_REPORT ------------
Event: time 1394216436.024706, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1f
Event: time 1394216436.024706, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 1
Event: time 1394216436.024706, -------------- SYN_REPORT ------------
Event: time 1394216436.024792, type 4 (EV_MSC), code 4 (MSC_SCAN), value 1f
Event: time 1394216436.024792, type 1 (EV_KEY), code 240 (KEY_UNKNOWN), value 0
Event: time 1394216436.024792, -------------- SYN_REPORT ------------

```


Of course what's striking is that F9 to F12 give the same keycode (240 KEY_UNKNOWN), but with a different MSC_SCAN (1c to 1f).

How can I map these scancodes to keys which get recognized further up to X.org/Unity?

Thanks for any help,

Joost

---

### Post by phidia on 2014-03-09
The [setkeycodes command]("http://manpages.ubuntu.com/manpages/hardy/man8/setkeycodes.8.html") might give you part of a solution or the start to one hopefully.

---

