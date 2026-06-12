---
title: "MX Revolution not detected as usb device"
date: 2008-02-28
forum: Desktop Environments
---

### Post by novana on 2008-02-28
I cant get the thumb buttons on my Mx Revolution to respond.

It looks like Ubuntu Gutzy cant detect the mouse as usb device.
How can I make it do that?

Btnx does only detect left, right and scroll button.
Btnx doesnt detect the mouse as MX Revolution.

In /etc/x11/xorg.conf there is nothing about "Logitech usb reciever"

I check device entities by doing cat /proc/bus/input/devices and got these relevant mouse attributes:
Name="Machintosh mouse button emulation"
Phys=
Name="ImPS/2 Generic Wheel Mouse"
Phys=isa0060/serio1/input0

Thx

---

### Post by DavidSrbija on 2008-05-05
Answer to your question is in [Thread]("http://ubuntuforums.org/showthread.php?p=2727025")
:)

---

