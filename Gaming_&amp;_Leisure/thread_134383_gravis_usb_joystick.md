---
title: "gravis usb joystick"
date: 2006-02-21
forum: Gaming &amp; Leisure
---

### Post by n_hendrick on 2006-02-21
I've been trying to get ubuntu to recognize my joystick.....
I installed mupen 64 and initially my joystick worked....
After a reboot I can't get ubuntu to even recognize that the joystick is 
plugged in. (The lights won't even come on). Mupen won't load the joystick config panel now, the program just terminates....and snes9x won't detect a joypad either. 
I've tried to re install the joystick by installing the package "joystick".
It seemed to work, it gave me the js0 device in dev and created a js0 
link from input. I rebooted and the link disappeared and there was no longer
a reference to js0 in the input directory. I tried to manually install the js0
with "mknod js0 c 13 0" in input and create the link in dev, but still no go...
The software still closes out when attempting a configuration. I've messed something  up with ubuntu because initially the joypad was being detected...
Any Ideas?

---

