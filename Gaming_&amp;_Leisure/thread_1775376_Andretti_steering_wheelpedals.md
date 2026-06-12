---
title: "Andretti steering wheel/pedals"
date: 2011-06-04
forum: Gaming &amp; Leisure
---

### Post by Garintsuk on 2011-06-04
I like driving games, and Torcs is good and playable with just the
keyboard arrow keys. I installed VDrift, but it is unplayable with
just the arrow keys, so thought I would try an old Andretti steering
wheel/pedals setup. It has both USB and gameport connectors, but needs
drivers for the gameport, which I very much doubt will be in existence 
for Ubuntu (the old Win98 drivers work with XP, and everything works fine
there).With the USB, the wheel is recognised:
$>lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1241:1111 Belkin Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0738:4420 Mad Catz, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

VDrift, or Torcs will not recognise the wheel, but when I was trying to
run jscal, the wheel and pedals, and buttons, reproduce the mouse 
movements and buttons! I have looked through what I can (I'm a linux
re-newbie, played around in the mid 90s with it, but only with 10.04
did I decide to use Linux as my main OS)but can't figure out if, or how,
to tell the machine they are 2 different devices, and hopefully let me use
them for playing.
Hoping one of the smart cookies on here will make it look easy (and me silly!)
Thanks!

---

### Post by rmattb on 2013-04-18
Mine's working, yay!
No special drivers were installed (just the Trigger Rally game beforehand).
jstest --normal /dev/input/js1
Driver version is 2.1.0.
Joystick (Ciponic Technology Mad Catz Andretti Racing Wheel) has 4 axes (X, Y, Hat0X, Hat0Y)
and 4 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn).
Testing ... (interrupt to exit)
Axes:  0: -1352  1:     0  2:     0  3:     0 Buttons:  0:off  1:off  2:off  3:off 

jscal -c /dev/input/js1
Just follow the steps, the pedals are positive and negative values on one of the axes.

And for the driving game Trigger Rally, per [http://manpages.ubuntu.com/manpages/hardy/man6/trigger.6.html](http://manpages.ubuntu.com/manpages/hardy/man6/trigger.6.html)
vi .trigger/trigger.config
Change the keyboard enable to no, and the joystick enable to yes
I also had to swap the  + and - for forward and reverse.

---

### Post by lisati on 2013-04-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

