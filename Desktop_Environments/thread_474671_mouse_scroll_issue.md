---
title: "mouse scroll issue"
date: 2007-06-15
forum: Desktop Environments
---

### Post by w7kmc on 2007-06-15
Hi,
I'm running kubuntu on an old AMD 500 Mhz...and made a few desktop changes. (btw it works great!)

I now  have a mouse issue where whenever i "scroll-up" a desktop  menu now appears...or the app menu... It also seems te be activating a cut and paste feature when I scroll up when using KATE.  I searched around keyboard-short-cuts,and mouse settings, etc to see if I can turn this"feature"off...because it is very annoying. 

Anyone have any ideas?
Thanks!
kmc

---

### Post by wolfsta on 2007-09-15
I have the same issue any one have any ideas...

I am using a logitech mouse m-BP82 it is a usb mouse but is running through a KVM switch via ps2.

this is the xorg.conf mouse section

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection
```

Cheers

Wolfsta

---

### Post by wolfsta on 2007-09-15
Ok seemed to have fixed the problem when i was trying to fix my screen resolution...

finally found the sync range for my compaq 7500 from this post

[http://ubuntuforums.org/showthread.php?t=35137](http://ubuntuforums.org/showthread.php?t=35137)

and when I changed the sync range i no longer have the issue of scrolling up thinking its a right click.. 

dunno why but thats what happened

Cheers :)

Wolfsta

---

