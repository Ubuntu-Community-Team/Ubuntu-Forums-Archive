---
title: "Jerky/sticky mouse in FPS"
date: 2008-01-13
forum: Gaming &amp; Leisure
---

### Post by TCDude on 2008-01-13
I have been trying to play Urban Terror and Assault Cube and I seem to have the same problem with each regarding my mouse. When I am not moving the mouse works fine but when I start running the mouse freezes and I cannot turn. I have to stop in order to turn. Once in a while it will move but it will jump and turn me around 90 or 180 degrees. I am running these on a MacBook Pro with a 2 GB processor with 256 mb of memory. Is this a memory issue? Thanks for any help!

Edit: After looking at it more closely, I noticed that I cannot fire or use any button on the mouse when I use the keyboard and vice versa. It is as if only one or the other can be used at one time.

---

### Post by jackflap on 2008-01-14
Damn, that's a tough one. 

Could you try a different mouse and see if it still happens? Is your mouse usb? Try a ps2 one, if it's ps2, try a usb one.

Alex

---

### Post by FurryNemesis on 2008-01-14
Can you post the relevant sections of your xorg.conf and tell us what model keyboard/mouse you're using? Your input devices section might be improperly configured for your hardware

---

### Post by TCDude on 2008-01-14
Thanks for the responses! Well my Macbook pro is a laptop so the keyboard is just the one on the laptop. It was a usb mouse as that is the only connection ports I have for a mouse. I think the problem might be with my touchpad that is my "mouse" when I do my normal work. When I play with the touchpad everything is fine. Perhaps I need to disable the touchpad when using the usb mouse?

Here's the relevant snippets:
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "Emulate3Buttons"       "false"
        Option          "MaxDoubleTapTime"      "1"
        Option          "MaxTapTime"    "0"
EndSection

---

### Post by wana10 on 2008-01-15
just had this problem...mine was caused by a program called mouseemu which should only be used for apples, a simple sudo apt-get remove mouseemu solved my problem. ymmv but good luck!

---

