---
title: "Gamepad calibration (or something like that)"
date: 2008-10-21
forum: Gaming &amp; Leisure
---

### Post by mumuson on 2008-10-21
There's a problem with Logitech Precision Gamepad (046d:c21a). The up and left buttons are always "pressed" (until you don't really press them). Running jstest immediately after reboot shown the following:
```
edwin@edwin:~$ jstest /dev/input/js0
Driver version is 2.1.0.
Joystick (Logitech Logitech(R) Precision(TM) Gamepad) has 2 axes (X, Y)
and 10 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4).
Testing ... (interrupt to exit)
Axes:  0:-32767  1:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 

```
Can anybody help me? I'm using Ubuntu 7.10.
Problem is not critical, but annoying...

---

