---
title: "Multi-button mouse under VMware"
date: 2008-09-30
forum: Desktop Environments
---

### Post by rfritz on 2008-09-30
If you are running Ubuntu Hardy Heron in a virtual machine, modify the mouse section of /etc/X11/xorg.conf to match the following to get your multi-button mouse, especially the scroll wheel, to work:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
        Option          "CorePointer"
        Option          "Buttons" "8"
        Option          "ZAxisMapping" "4 5 6 7 8"
        Option          "Device"        "/dev/input/mice"
EndSection
```

The number of buttons should match your mouse; a basic scroll wheel counts as three buttons; this fancy Logitech G5 has eight.

---

