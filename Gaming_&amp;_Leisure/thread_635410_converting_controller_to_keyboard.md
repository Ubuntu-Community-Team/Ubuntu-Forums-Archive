---
title: "converting controller to keyboard"
date: 2007-12-08
forum: Gaming &amp; Leisure
---

### Post by FoxHappy on 2007-12-08
Okay, I'm sort of dumb on this subject, but I'm just trying to play my emulator games with my controller.

I downloaded joy2key but I can't figure it out. I know my controller is working and I can calibrate it with joy2key in my terminal, but it doesn't work. Does anyone know how to successfully use this software, or, know anything more user friendly?

---

### Post by Jugix on 2007-12-11
Same here. Joy2key seems to be one tricky program. Here is where I have gotten to. (BTW, I use ubuntu 7.10 and it is running on my Playstation3.)

AFAIK, to get joy2key to see my joystick I need to point it to /dev/input/js0 with -dev option. > joy2key -dev /dev/input/js0
Ok, then I have my amiga emulator up and running a game so I need my joystick button presses to be translated to that specific X-window. I use -X option.  > joy2key -dev /dev/input/js0 -X

Here is when my finger starts scratching my head. When I press enter I have to calibrate my joystick axises. There are 28 different axis in my PS3 SIXAXIS controller that is connected via BT interface. Everytime I calibrate it joy2key says:"Save these to .joy2keyrc so you dont need to calibrate anymore. Entering main loop. Press ctrl^c to quit"

It does not save calibration data automatically to anywhere. Everytime the same and no go...

I may be just stupid but how do I save calibration data to a file? How do I configure different buttons to send different ascii letters to E-UAE?

I keep trying. :lolflag:

---

