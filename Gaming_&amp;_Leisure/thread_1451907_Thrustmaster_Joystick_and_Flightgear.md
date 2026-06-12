---
title: "Thrustmaster Joystick and Flightgear"
date: 2010-04-11
forum: Gaming &amp; Leisure
---

### Post by Alasta on 2010-04-11
Hello there 

I have A thrustmaster joystick which I am trying to use with FlightGear . unfortunately it needs calibrating . All of the posts I have found so far seem to date to 2007 and use something called jscalibrator .when I do "sudo apt-get install jscalibrator" I get "cant find package"

The sim sees the joystick , there seems to be no way of calibrating it though , or mapping the buttons.

Nay help greattly appreciated


Alastair

---

### Post by Alasta on 2010-04-11
Well I have jscal installed . it seems jscalibrator was removed

js_demo gives this :

alastair@Laburnum-desktop:~$ js_demo
Joystick test program.
~~~~~~~~~~~~~~~~~~~~~~
Joystick 0: "THRUSTMASTER Top Gun Afterburner"
Joystick 1 not detected
Joystick 2 not detected
Joystick 3 not detected
Joystick 4 not detected
Joystick 5 not detected
Joystick 6 not detected
Joystick 7 not detected
+--------------------JS.0----------------------+
| Btns Ax:0 Ax:1 Ax:2 Ax:3 Ax:4 Ax:5           |
+----------------------------------------------+
^C0000 +0.1 -0.1 +0.0 +1.0 +0.0 +0.0   .    .  |
alastair@Laburnum-desktop:~$ 



However I cant figure out jscal :


alastair@Laburnum-desktop:~$ jscal "THRUSTMASTER topgun afterburner" -c
jscal: can't open joystick device: No such file or directory
alastair@Laburnum-desktop:~$ 




Best regards

Alastair

---

### Post by Alasta on 2010-04-12
I see .Here are the prioritys ....

---

### Post by Alasta on 2010-04-14
I would appreciate any input at All here : )

---

### Post by dvk2 on 2010-07-22
On my system (Arch) it is 
jscal -c /dev/input/js0

Just browse in the /dev/input directory and look for something similar.

---

### Post by vfd000 on 2012-05-03
Thrust master usually does a good job of being auto detected in ubuntu. For a graphical layout of you're axis and buttons use jstest_gtk (you can get it either via terminal using sudo apt-get install jstest_gtk, or the software center.) to calibrate and configure it use joy2Key
    sudo apt-get install joy2key
in linux it's text driven so it can be a bit tricky but there are joy 2 key tutorials you can follow.

---

