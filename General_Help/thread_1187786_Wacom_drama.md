---
title: "Wacom drama"
date: 2009-06-15
forum: General Help
---

### Post by Demi13 on 2009-06-15
Ok so I have Jaunty installed on my ps3 and for some reason it is not detecting my intuos3 wacom tablet. I have reinstalled hal, xserver-xorg-input-wacom, and wacom-tools through package manager with no luck. 

The output of xinput --list (with obvious lack of reference to wacom)

```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=2    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"USB Mouse"    id=3    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Logitech Logitech USB Keyboard"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
```

If anybody can think of a reason why this would not be working do let me know and thanks in advance! I've messed around with fedora more than ubuntu so definitely not a pro. Speak slowly and use short words if possible. ;-)

---

### Post by Favux on 2009-06-15
Hi Demi13,

I'm going to assume you know the Intuos3 works and that the PS3 isn't introducing hardware issues.  The Intuos3 is usb, correct?

Since Xinput isn't detecting your tablet it may be that your wacom.ko (the usb kernel driver) isn't active.  Some setups seem to require adding the module to "/etc/modules".  One way to do this is described in post #3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I guess another possibility is that for whatever reason the 10-wacom.fdi isn't being installed.  It should be in "/usr/share/hal/fdi/policy/20thirdparty/".  You could check and see if it is there.

Good luck!

---

