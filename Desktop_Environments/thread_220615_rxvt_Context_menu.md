---
title: "rxvt: Context menu?"
date: 2006-07-21
forum: Desktop Environments
---

### Post by zergberg on 2006-07-21
rxvt is a wonderful terminal emulator for running irssi in, but there is the slight problem that I can't copy and paste from it. As an xfce4 user, I appear to be without the nice middle-click copy/paste functionality provided by other desktop environments. As such, is there any way to get some sort of context menu--or any alternate copy/paste method into rxvt?

Thanks.

---

### Post by taurus on 2006-07-21
If you are not using a three-button mouse, you can press both buttons down for paste or use the track in the middle of your mouse to paste!!!

---

### Post by zergberg on 2006-07-21
XFCE does not have support for mousebutton copy/paste :(

---

### Post by taurus on 2006-07-21
The cut 'n paste function has nothing to do with what window manager you are using!  It's in /etc/X11/xorg.conf!!!  Do you have these lines in your /etc/X11/xorg.conf?

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

---

### Post by zergberg on 2006-07-21
I have 
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mx700" 
EndSection

```

As per the Logitech mice thread. However, I had the normal setup earlier, and still could not use copy/paste in this manner.

---

### Post by taurus on 2006-07-21
Where's the 

```

"Option          "Emulate3Buttons"       "true"

```
Try adding that line after "Option          "Device"        "/dev/input/mx700" okay!!!

---

### Post by zergberg on 2006-07-21
> **taurus said:**
> Where's the 

```

"Option          "Emulate3Buttons"       "true"

```
Try adding that line after "Option          "Device"        "/dev/input/mx700" okay!!!
Nope. No effect.

---

### Post by taurus on 2006-07-21
You did reboot or restart X, right!!!

---

### Post by zergberg on 2006-07-22
Yes, of course.

---

