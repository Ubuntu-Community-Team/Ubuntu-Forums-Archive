---
title: "Dualshock 3 issues in Karmic"
date: 2009-11-18
forum: Gaming &amp; Leisure
---

### Post by rabish12 on 2009-11-18
Well, I'm a near-complete newbie to Linux, but after having a monumental failure with Vista that forced me to reformat my hard drive I decided to switch over.  Things are going pretty well for the most part, but I'm having some major issues with using a Dualshock 3 with the OS.  The controller's being detected by the OS just fine, and going by jstest it's detecting button presses and the sticks with no problem, but there's some really major issues beyond that.  Basically, it's detecting at least one axis or button that doesn't actually exist as always being tilted/pressed (ZSNES picks it up as "J19" first, which I'm guessing is a button, but I remember other programs picking up an axis instead), which makes it impossible for me to actually configure the others in any program (and as a result makes it impossible to use the controller with anything).

I've already tried the obvious thing of trying to calibrate it with jscal, but if I even attempt "jscal -c /dev/input/js0" it spits this out (or something similar - usually the first sixteen axes are broken line like the rest and have coefficients rather than being none with precision 0, but the different outputs from jscal don't really change the results of trying to use it for inputs in any way):

```
Joystick has 28 axes and 112 buttons.
Correction for axis 0 is none (raw), precision is 0.
Correction for axis 1 is none (raw), precision is 0.
Correction for axis 2 is none (raw), precision is 0.
Correction for axis 3 is none (raw), precision is 0.
Correction for axis 4 is none (raw), precision is 0.
Correction for axis 5 is none (raw), precision is 0.
Correction for axis 6 is none (raw), precision is 0.
Correction for axis 7 is none (raw), precision is 0.
Correction for axis 8 is none (raw), precision is 0.
Correction for axis 9 is none (raw), precision is 0.
Correction for axis 10 is none (raw), precision is 0.
Correction for axis 11 is none (raw), precision is 0.
Correction for axis 12 is none (raw), precision is 0.
Correction for axis 13 is none (raw), precision is 0.
Correction for axis 14 is none (raw), precision is 0.
Correction for axis 15 is none (raw), precision is 0.
Correction for axis 16 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 17 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 18 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 19 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 20 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 21 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 22 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 23 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 24 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 25 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 26 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 27 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751

Calibrating precision: wait and don't touch the joystick.
Segmentation fault
```
So there's a segfault coming up there and I have no idea why.  I've searched everywhere and found no evidence of anyone else having this issue or any way of fixing it.  I might be able to get it solved if I could find an alternative calibrator for my controller, but no luck there either.  Also, probably worth noting the fact that jscal thinks my controller has 112 buttons.  I'd appreciate some help with this - it's kind of hard to play quite a few of the games I have without a controller.

---

### Post by tuppe666 on 2009-11-18
I can confirm I have the same issue. Sorry I could not de more help. Its a shame because its a perfect controller apart from rumble not working.

---

### Post by AndreLeComte on 2010-01-09
I have the exact same issue with a Honcam HC-MU001 joystick. I did have it working fine in ZSNES, but now I can't remember how I set it up.

---

### Post by Xenphor on 2010-07-02
I'm having this exact same issue in Lucid. Does anyone know how to fix it?

---

### Post by treat on 2010-08-26
For DualShock 3 disable the accelerometers with [QtSixA]("http://qtsixa.sourceforge.net").

```
sudo add-apt-repository ppa:falk-t-j/qtsixa
sudo apt-get update
sudo apt-get install qtsixa
```

Tested with a DualShock 3 connected over bluetooth on Lucid. ZSNES works great. Also pressing the button you want in ZSNES really fast works to =)

Edit:
Just tested using the controller over usb and the "button axes" seems to be the problem they report and absolute value of -32767 when depressed i guess ZSNES expect a value of 0. As is the case when using the controller over Bluetooth. So i guess the fix is to use bluetooth or someone needs to fix the usb driver.

---

### Post by yilmi on 2013-03-03
Accelerometers are overriding any other input you try to set.

See qtsixa manual :
- sixad-raw
 Registers a new joystick using a sixaxis hidraw interface, useful to get accelerometers working on USB mode.

---

### Post by oldos2er on 2013-03-03
Old thread closed, please don't bump old threads.

---

