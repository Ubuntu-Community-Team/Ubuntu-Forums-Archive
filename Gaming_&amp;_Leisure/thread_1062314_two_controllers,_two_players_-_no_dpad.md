---
title: "two controllers, two players - no dpad"
date: 2009-02-06
forum: Gaming &amp; Leisure
---

### Post by umicko on 2009-02-06
Hi everyone,

I've been setting up my mythbox and finally decided to get mupen64plus (latest release) running. Everything is working great and i love it.

But.

Two player seems to be broken and i can't find any info out on the net.
I'm using Mario Kart 64 for testing
I have two USB Logitech Precision Gamepads (cheapo's)
I have also installed my xbox 360 wireless controller
Ubuntu 8.10

All of the controls work ok when using the blight plugin to configure the gamepad i can get to the menu and select players with both controllers but when the game actually starts the second player can't steer the kart. The first player can still do everything and the second player can accelerate, brake etc its seems when two player is active the dpad is broken?

I've tried 1080 snowboarding with the same result.

Jscalibrator is able to calibrate both controllers, i also tried removing jscalibrator.

I've tried downgrading to mupen64plus 1.41 with the same result.

Any help would be greatly appreciated.

Cheers.

---

### Post by grossaffe on 2009-02-07
jscalibrator is supposed to be bad.  even removing it doesn't undo its problems.  I think you have to delete some kind of config file or whatever it leaves behind.  what you want to use is jstest

---

### Post by umicko on 2009-02-07
Hi, 

I removed jscalibrator and the .joystick file in ~/

sudo apt-get remove jscalibrator
sudo apt-get autoremove

Installed the joystick pacakge to get jscal and jstest

sudo apt-get install joystick

i can calibrate both the xbox controller and the logitech controller, another part i forgot to mention if i got to mupen64plus and change the player 2 controller to keyboard i get the same result, which i thought was weird? i was thinking maybe its an sdl problem? i could be way off though.

thank you.

---

