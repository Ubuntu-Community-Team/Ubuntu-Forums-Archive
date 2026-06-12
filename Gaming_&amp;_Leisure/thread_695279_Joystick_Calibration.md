---
title: "Joystick Calibration"
date: 2008-02-12
forum: Gaming &amp; Leisure
---

### Post by ketzerei on 2008-02-12
Okay, after much tweaking, I got my logitech joystick to work with Flightgear. All the axes respond and so do the buttons. However, when I increase the throttle with the little button on my stick, my plane slides to the left and I have to hold the stick to the right to keep it straight. So, my question to you all is how do I calibrate my joystick properly? I've already run "jscal -c /dev/input/js0' and run through it all, but everytime I do it I still have some kind of calibration error. Help appreciated.

---

### Post by Sockerdrickan on 2008-02-15
install jscalibrator

---

### Post by acoustibop on 2008-02-15
I have to say I've always found jscalibrator a problem - it tends to disable the directional controls, although it still reports them as working.  The version that's native to Kubuntu is, apparently, Ok, but otherwise...

Incidentally, if you do install it and have problems, make sure you also remove the configuration when you uninstall it.  Otherwise the problem may continue, even when it's gone. :(

---

### Post by Sockerdrickan on 2008-02-15
My logitech joystick doesn't work in flight gear :(

---

### Post by Sockerdrickan on 2008-02-15
Thanks it worked after I removed jscalibrator

---

### Post by disturbedite on 2008-02-15
i've read about a lot problems caused by jscalibrator too.

its kinda funny, i read all these horror stories about ppl trying to calibrate their joysticks/pads (with & without jscalibrator) but i have an xbox s controller (regular xbox controller) & i have universal usb hub that i plug it into and i have never ever had to calibrate it.
could it be that ppl are trying to calibrate joysticks/pads not realizing that they don't have to?  (at least some of the time, of course there are cases where it is necessary).

---

### Post by Sockerdrickan on 2008-02-15
Yes that might be it. It was for me anyways.

---

### Post by acoustibop on 2008-02-15
I think you're probably correct, disturbedite.  When I started using Ubuntu (think that was Edgy), I tried jscalibrator, ran into the inevitable problems and switched to joystick.  However, I guess because it didn't actually make any difference, I stopped using it and, like you, don't bother calibrating controllers any more.

---

### Post by disturbedite on 2008-02-16
well, i know that is the case with an xbox controller at least cuz ubuntu's kernel is compiled with the xbox controller module, so its "included" by default, you don't have to install any driver.
and i have what looks to be an off-brand universal usb hub with ports for xbox, gamecube, & ps1/ps2 controller that i plug my xbox controller into, and i didn't even need drivers for the hub!  i just plug it in & its detected like a normal usb hub.
when i started out with this stuff i never expected it to be that easy...

---

### Post by acoustibop on 2008-02-17
I've only ever used one controller at a time, disturbedite, but, of several 'no name' controllers, a USB Gamepad Pro, Logitech DualAction and Rumblepad 2 controllers, and a Playstation controller connected via a 'no name' adapter, all have worked straight away, and none have needed calibration.  The only controller I ever had to install and get working was an old gameport Gravis Gamepad Pro.

---

### Post by trlkly on 2008-12-23
I wasn't sure whether to add a new thread or just add to this one. I'll do this first, and the other if I don't get any replies.



Anyways, my problem with my Joystick is that, though I use the KDE Joystick program, (jscalibrator doesn't work for me, either) unfortunately, the calibration won't stick. It only works for the current session.

Just in case you're wondering, I have to calibrate my joystick because its axes don't use the full range of motion. In other words, it moves too slowly.

---

### Post by trlkly on 2009-04-18
Just in case anyone cares, the solution is to use jscal. Yes, it must be run from a terminal, but it outputs the configuration settings. Keep these settings handy, and you can calibrate your joystick with a single command. Now to make a script that'll work only when the appropriate joystick is plugged in...

P.S. Gotta love backquotes (`).

---

