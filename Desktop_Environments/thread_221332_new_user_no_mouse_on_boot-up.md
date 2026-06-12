---
title: "new user no mouse on boot-up"
date: 2006-07-22
forum: Desktop Environments
---

### Post by dotcomdz on 2006-07-22
No power to my mouse first time trying linux based system... any help.
I run a:
MSI k7n2-delta
Amd athlonxp 3200+
3gig of ram 
 radeon graphics board   older 9250
Everything loaded fine the ubuntu desktop loaded but no mouse. 
Any help??
:-k

---

### Post by scxtt on 2006-07-22
try to open a terminal and view your /etc/X11/xorg.conf looking for something similar to the following:
```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection
```

---

### Post by dotcomdz on 2006-07-22
ok rebooted from xp but still no mouse and i'm lost on the terminal thing because the keyboard did nothing.

---

### Post by theconley on 2006-07-22
Look for that same portion of code and try adding
```
Option "HWCursor" "off"
```
and restarting X.

I had the same problem in FC5, that worked for me.

~Conley

---

