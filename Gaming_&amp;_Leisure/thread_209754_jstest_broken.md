---
title: "jstest broken"
date: 2006-07-05
forum: Gaming &amp; Leisure
---

### Post by NeoRazorX on 2006-07-05
Hello, i have a Creative Cobra 2 gamepad (USB). I installed joystick package and calibrate my gamepad, but when i run jstest y give a segmentation fault:

```

$ sudo jscal -c /dev/input/js0
Joystick has 3 axes and 12 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 2 is broken line, precision is 0.
Coeficients are: 14, 16, 41297762, 41297762

Calibrating precision: wait and don't touch the joystick.
Done. Precision is:
Axis: 0:     0
Axis: 1:     0
Axis: 2:     0

Move axis 0 to minimum position and push any button.
Hold ... OK.
Move axis 0 to center position and push any button.
Hold ... OK.
Move axis 0 to maximum position and push any button.
Hold ... OK.
Move axis 1 to minimum position and push any button.
Hold ... OK.
Move axis 1 to center position and push any button.
Hold ... OK.
Move axis 1 to maximum position and push any button.
Hold ... OK.
Move axis 2 to minimum position and push any button.
Hold ... OK.
Move axis 2 to center position and push any button.
Hold ... OK.
Move axis 2 to maximum position and push any button.
Hold ... OK.

Setting correction to:
Correction for axis 0: broken line, precision: 0.
Coeficients: 128, 128, -2147483648, -2147483648
Correction for axis 1: broken line, precision: 0.
Coeficients: 128, 128, -2147483648, -2147483648
Correction for axis 2: broken line, precision: 0.
Coeficients: 15, 15, 35790302, 33553408

neorazorx@sem3000:~$ sudo jstest /dev/input/js0
Driver version is 2.1.0.
Joystick (HID 041e:1003) has 3 axes (X, X, X)
Fallo de segmentación

```

Any idea?

---

### Post by NeoRazorX on 2006-07-05
Solved, i installed this package >> [http://ftp.debian.org/debian/pool/main/j/joystick/joystick_20051019-1_i386.deb](http://ftp.debian.org/debian/pool/main/j/joystick/joystick_20051019-1_i386.deb)

---

### Post by palsyboy on 2006-07-24
How did you do so?  I tried running dpkg -i on the package, and it didn't install.  Thanks!

---

