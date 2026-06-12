---
title: "Logitech Controller"
date: 2011-06-10
forum: Gaming &amp; Leisure
---

### Post by mpace965 on 2011-06-10
I'm trying to use a Logitech Dual Action controller with Mednafen. However, it is not appearing in /dev/input at all.

I tried ```
$ dmesg | grep Logitech
``` and here was the output:

```
[  206.247318] input: Logitech Logitech Dual Action as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12
[  206.247603] generic-usb 0003:046D:C216.0002: input,hidraw1: USB HID v1.11 Joystick [Logitech Logitech Dual Action] on usb-0000:00:1d.0-1.1/input0

```

Also when I start an emulation with Mednafen, when it says "Initializing Joysticks," nothing appears under it. I assume it normally says "Joystick 0" or something similar if it is working.

I am running Ubuntu 11.04 32-bit.

---

