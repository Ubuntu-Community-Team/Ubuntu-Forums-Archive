---
title: "jscal save calibration"
date: 2007-03-23
forum: Gaming &amp; Leisure
---

### Post by tshannon on 2007-03-23
I've got my gamepad working on my mythbox using jscal.  I actually have two gamepads (so me and the wife can be Mario together), and the only way they work is when I calibrate them with jscal.

This is all well and good, until I have to reboot the machine, then I seem to lose all the calibration, and the gamepads act as if I've just plugged them in.

Is there anyway to save this calibration to a file or something, so I don't have to recalibrate them ever time I start the machine, or is this something I'll just have to live with.

thanks for your help.

---

### Post by gigaferz on 2007-04-11
Hello, SAme thing here.

i have jscal, and jscalibrator.

With jscalibrator, the axis are inverted.

It just ocurred to me , I will calibrate the xbox pad with jscal.
Then open JScalibrator and  I will save the calibration registered .I m trying this right now.

At least the gamepad was detected this time, and it did not change the id (js0 to js1)

I launched xmame , and the d pad is inverted, the rest of buttons worked fine.
On th Zsnes, when i am setting the keys, it freezes whn I have to set the select key.

I have not tried the joysticks yet

Well, nevermind this, It did changed from js0 to js1 again(giving problems),  i guess the only other option is to make a script that sets up the gamepad at Satrt up, or at least with one single click.

---

### Post by Michael_TSM on 2008-01-31
I found this here [http://listas.apesol.org/pipermail/sdl-libsdl.org/2003-November/039472.html](http://listas.apesol.org/pipermail/sdl-libsdl.org/2003-November/039472.html) it may be useful to solving your problem. I've modified it appropriately.

For most joysticks you won't need any manual calibration, since the
joystick should be autocalibrated by the driver automagically. However, with
some analog joysticks, that either do not use linear resistors, or if you
want better precision, you can use the jscal program

        jscal -c /dev/input/js0

 included in the joystick package to set better correction coefficients than
what the driver would choose itself.

  After calibrating the joystick you can verify if you like the new
calibration using the jstest command, and if you do, you then can save the
correction coefficients into a file

        jscal -p /dev/input/js0 > /etc/joystick.cal

  And add a line to your rc script executing that file

        source /etc/joystick.cal

  This way, after the next reboot your joystick will remain calibrated. You
can also add the jscal -p line to your shutdown script.

---

### Post by acoustibop on 2008-01-31
I've always found jscalibrator to be a problematic program: the version that comes pre-installed in Kubuntu is, apparently, Ok, but the version installed from the repositories tends to disable controller buttons, most commonly the directional controls, while still reporting them as working.

My advice would be to remove it, along with its configuration files and use jscalc.  As Michael_TSM says, you don't really need to calibrate your controller anyway, but if you do need to, you can save jscalc's calibration as he describes.

---

