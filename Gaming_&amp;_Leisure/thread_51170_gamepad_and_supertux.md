---
title: "gamepad and supertux"
date: 2005-07-22
forum: Gaming &amp; Leisure
---

### Post by spacemonkey on 2005-07-22
I'm having trouble getting my new game pad to work with super tux.  It's just a generic USB gamepad with 12 buttons, a D pad, and two analog sticks.  i've got it working great with zsnes, tuxnes, tuxracer, and pretty much anything else I use a gamepad for, but for some reason it won't work with supertux.  When I start supertux in a terminal, this is the output:

Datadir: /usr/share/games/supertux
open /dev/sequencer: No such file or directory
Warning: Could not open joystick -1.
The Simple DirectMedia error that occured was:
There are 1 joysticks available

It seems like it's finding my joystick, but I can't seem to use it at all....  Any suggestions?

---

### Post by spacemonkey on 2005-07-22
Also, if anyone has any suggestion on getting my gamepad to work with Wolfenstein ET, that would be great to.  I think there is some argument you have to use at the command line to make it use a joystick, I tried joystick as an argument, but that didn't seem to work.

---

### Post by mhancoc7 on 2005-11-03
I just got my new gampad to work with SuperTux. It is a [Logitech Dual Action Gamepad]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=11,CONTENTID=6951"). 

To get the buttons setup to be similiar to that of the SNES gamepad simply start SuperTux with the following command.

supertux --joystick /dev/input/js0 --joymap 4:5:2:1:3

Just make sure that the path to your js0 file is the correct. Mine was /dev/input/js0.

You can even add an icon to your panel and just put the command in and no need to type it ever time.

Also in terminal you can type supertux --help for more info.

I hope this helps.

Jereme

---

### Post by bernardfrancois on 2007-01-19
Here it doesn't work. The X and Y axisses don't work. I calibrated the joystick using jscalibrator (wich worked fine). How do I know which number to assign to the X and Y axisses? Or maybe it's a sensitivity problem.

[edit] I have the same problem with frozen bubble 2 (option -ji)  planet penguin racer[/edit]

---

### Post by nixphoeni on 2007-02-17
> **bernardfrancois said:**
> How do I know which number to assign to the X and Y axisses? Or maybe it's a sensitivity problem.

Use the program jstest from [http://atrey.karlin.mff.cuni.cz/~vojtech/input/]("http://atrey.karlin.mff.cuni.cz/~vojtech/input/") to figure out which axes and buttons seen by the driver are being relayed from your joystick.  For example, I just did ```
jstest /dev/input/js0
``` because my joystick is at /dev/input/js0 .

---

### Post by adam0509 on 2007-02-17
All you need to know about gamepad :

[http://www.ubuntuforums.org/showthread.php?t=338457](http://www.ubuntuforums.org/showthread.php?t=338457)

---

### Post by qrazi on 2007-11-05
I also have the problem that the axis do not work in supertux. I checked the config file, and noticed a dead zone which was set to 1000 for both x and y axis.

With JSCalibrator I already found out that the dead zone for my gamepad is 128 (Logitech precision gamepad USB). the minimal value for the axis is 1, and the maximum is 255. When I put a value of something between 254 and 128 for the y axis, I can control down, but not up. With the x axis I can go right, but not left. When I lower the dead zone to 127 or lower, the axis continually go down or right.

I suspect this problem has something to do with the definition of the axis and the dead zone in the config. When I simply delete the whole dead zone, it reappears the moment I run Supertux.

Any siggestions as to why this doesnt work? I'm running 7.04 feisty 32-bit btw.

---

