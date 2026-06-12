---
title: "how do I install usb gampad"
date: 2011-09-17
forum: Gaming &amp; Leisure
---

### Post by chezza on 2011-09-17
Im not sure if this should bne posted here or in the beginners section

I bought a cheap joypad from ebay jsut to use with some emulators - if it helps it is a dilong joypad (cheap chinese) there is a drever install disc but it is a windows .exe

Its not auto detected by ubuntu (natty)

I tried following this guide

[http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-or-gamepad](http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-or-gamepad)

step 1

 sudo apt-get install joystick

and I get

[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
joystick is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/PHP]
which I guess is fine as in a different attmept top get it working I installed joystick from the software centre

step 2

sudo apt-get install jscalibrator

I get 

[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package jscalibrator
[/PHP]

I then tried following this guide 

[http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

 The manual method

.... but I dont really understand it nor do I know what modules I need

what should I try next? 

cheers

---

### Post by GWBouge on 2011-09-17
jscalibrator doesn't seem to be in the repo's anymore, but joystick comes with some helpful stuff, like jstest and jscal.  See if you have any joystick devices:

```
ls /dev/input/js*
```

You should have a jsX for any input devices, like a wheel, flight stick, etc.  If it comes back with anything, test them.  If you have more than one, it shouldn't take long to figure out which one is your new gamepad.  For example:

```
jstest /dev/input/js0
```

Just shows a bunch of numbers, but push some buttons, move some sticks around, see if any of the numbers change.  Stop that with Ctrl+Z.

---

