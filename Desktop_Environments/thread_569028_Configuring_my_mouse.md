---
title: "Configuring my mouse"
date: 2007-10-06
forum: Desktop Environments
---

### Post by chrishoeppner on 2007-10-06
Hi there!

I know there are similar posts. I have gone through all of them.

The deal is: I have a Logitech mx 610 mouse, and would like to get it working. There's always something wrong, though I don't get what.

It's already setup to work with evdev, and runs very smooth. But then, it interprets the thumb buttons as keyboard left and right keys, the wheel's tilt as the thumb buttons, and the wheel up and down let's me awesomely navigate back and forth in firefox and nautilus.

As xev says, wheel is 6 up and 7 down, but putting it into ZAxisMapping does nothing. Any clues what might have gone wrong? I had this working before... but it seems like some update messed it.

Thanks everyone!

---

### Post by JBAlaska on 2007-10-06
I have a mx 500 running under evdev, it should be similar to yours with the exception of wheel tilt. My side buttons work correctly in firefox and nautilus. 

Here's the pertinent sections of my xorg.conf:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection


Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Name"  "B16_b_02 USB-PS/2 Optical Mouse"
EndSection

```

Since I went to evdev I no longer have to use "ZAxisMapping"

This is a good tut for **your** mouse If you haven't seen it;
```
http://ubuntuforums.org/showthread.php?t=332256
```

---

