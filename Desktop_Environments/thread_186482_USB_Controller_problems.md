---
title: "USB Controller problems"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Termina on 2006-06-02
I'm running x86 Dapper (Athlon XP 3000+, 2GB RAM, etc.)

I'm trying to get mupen64 to work, with a USB convertor, so I can use a real N64 controller.

The controller works, except that no matter how hard I press on the joystick, I cannot 'run' in any game.

jscalibrator is installed, and I calibrate it. After doing so, everything works in the test window of the jscalibrator program.

Trying jstest, however, doesn't work.

> 
will@risen:~/Desktop/mupen64-0.5$ sudo jstest /dev/input/js0
Driver version is 2.1.0.
Joystick (HID 6666:0667) has 4 axes (X, X, X, X)
Segmentation fault


I've seen that 'jscal -c /dev/input/js0' can help me, but I have no clue which directions axis0-3 represent. Anyone know?

Can anyone help me get this working? It worked just fine in Slackware.

---

