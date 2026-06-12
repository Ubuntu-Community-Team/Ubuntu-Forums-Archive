---
title: "Wacom tablet- cannot adjust and is a device joystick"
date: 2020-04-02
forum: Desktop Environments
---

### Post by buntu_hugenewbie11 on 2020-04-02
I am trying to use a WACOM INTOS BT on Kubuntu 18.04.
Through usb the device is seen lsusb:
Bus 001 Device 006: ID 056a:0378 Wacom Co., Ltd 


And xsetwacom --list devices returns:

Wacom Intuos BT M Pen stylus            id: 12  type: STYLUS                                                                                                                                                                                                                                                                               
Wacom Intuos BT M Pen eraser            id: 13  type: ERASER                                                                                                                                                                                                                                                                               
Wacom Intuos BT M Pen cursor            id: 27  type: CURSOR                                                                                                                                                                                                                                                                               
Wacom Intuos BT M Pad pad               id: 28  type: PAD   

But in system settings it shows a joystick and I cannot adjust anything.
I have 3 monitors connected and the stylus is super sensitive and it spans all three monitors when I just want it mapped to one.
It makes it really difficult to draw or sketch in krita or gimp because it is so sensitive.
I have tried to set the area of the stylus to be smaller.
But it has not helped at all change anything.
---
xsetwacom get "Wacom Intuos BT M Pen stylus"  area
0 0 21600 13500

I change to 
xsetwacom set "Wacom Intuos BT M Pen stylus"  area 0 0  7200 13500

And nothing changes.

My top priority is to at least change the area so it at least I can sketch and write.
Right now 4cm area on the tablet maps to almost my entire screen.

When I connect through BT the system does see a BT device and connects but does not view the tablet as an input device.
Please any direction would be useful.

---

