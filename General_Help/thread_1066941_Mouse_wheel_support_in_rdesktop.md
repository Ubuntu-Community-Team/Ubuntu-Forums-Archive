---
title: "Mouse wheel support in rdesktop"
date: 2009-02-11
forum: General Help
---

### Post by cynoclast on 2009-02-11
I cannot get my mouse wheel to work both in Ubuntu and rdesktop windows.

Here are the pertinent parts of my xorg.conf
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Microsoft Wireless Mobile Mouse 3000" "CorePointer"
EndSection
```

```
Section "InputDevice"
    Identifier     "Microsoft Wireless Mobile Mouse 3000"
    Driver         "mouse"
    Option         "Name" "Microsoft Microsoft Notebook Receiver v2.0"
    Option         "Dev Phys" "usb-0000:00:1d.2-1/input0"
    Option "Protocol" "IMPS/2"
    Option "ZAxisMapping" "6 7"
    Option "Emulate3Buttons" "true"
EndSection
```

With these settings my mouse wheel works fine in linux, but does not work in terminal windows.

If I change
```
    Option "ZAxisMapping" "6 7"
```
to 
```
    Option "ZAxisMapping" "4 5"
```
It **ceases** to work in linux, but **does** work within rdesktop windows.

How can I fix it so that my mouse works both in linux and in rdesktop windows?

---

### Post by cynoclast on 2009-03-30
Anyone?

---

