---
title: "Logitech MouseMan M-BD53 USB does not work on boot, but does after replugging in."
date: 2005-12-08
forum: Desktop Environments
---

### Post by VenomousGecko on 2005-12-08
I have a weird kind of problem.  When I first boot my system, my mouse does not work.  I do have the optical light on and the mouse seems to be detected properly upon boot up as shown by this dmesg output:

dmesg | grep Logitech
[4294681.371000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00: 10.0-1
[4294681.391000] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:10.0-2
[4294681.431000] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:10.0-2
[4295189.283000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00: 10.0-1

Even still, the mouse does not work.  Now, if I simply unplug and replug it back into the system in the same USB port it works fine.  I have a dual boot system and it works fine in WinXP.   I have filed a Hardware report with Ubuntu but was curious if anyone else had seen or experienced anything similar and if there was a work around.

Thanks in advance,

Gecko

---

