---
title: "question about PS2 controller, hooking it through a USB Adapter to computer, no luck"
date: 2006-08-16
forum: Gaming &amp; Leisure
---

### Post by tbay007 on 2006-08-16
Ok, so i can't find this anywhere on the forum.  I did searches, i can't go every thread unfortunatly.

My problem is this, i am trying to use a Super Nintendo Emulator with Ubuntu-Linux which THAT is fine.  But when it comes to trying to calibrate my PS2(Playstation 2 controller) to work with it, the buttons won't even read. 

What i mean is, my Mad Catz Dual Force 2 Pro PS2 controller is going through a PS2 to USB adapter (produc name is:  BSN USA) it won't read.  Power is going through my controller cause i can hit the analog to digital button and it lights up.  Linux with teh joystick cal program and the joystick drive does not work for some reason either at reading my buttons hits.

How would i go about solving this issue?

Please reply back ASAP because i like my old school super nintendo games.  Brings back my middle school years.

---

### Post by Sandlst on 2006-08-18
I had a similar problem with a logitech gamepad, as I recall the emulator was looking for a joystick at /dev/js*, and I believe ubuntu places it at /dev/input/js*, to see if this is the case, paste this in a terminal ```
sudo ln -s /dev/input/js0 /dev/
``` Then try the emulator.  Good luck! Post back if you have any problems.

---

### Post by Toxicity999 on 2006-08-24
Also just so you know I'm pretty sure usb devices are powered through non software meaning they steal power from the lowest level so a light doesn't indicate an insane amount. (Correct me if I'm wrong.)

---

