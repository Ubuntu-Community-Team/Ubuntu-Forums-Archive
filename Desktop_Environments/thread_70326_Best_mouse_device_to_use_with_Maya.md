---
title: "Best mouse device to use with Maya?"
date: 2005-09-29
forum: Desktop Environments
---

### Post by BIGtrouble77 on 2005-09-29
This device causes a pointer glitch in maya:
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

This one appears fine in Maya, but scroll wheel does not work at all:
Section "InputDevice"
    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ExplorerPS/2"
    Option "Device"     "/dev/input/mice"
EndSection

The glitch in maya is that when I use the scroll wheel the X cursor gets used as my main cursor, which is extremely annoying.  I have to navigate the program (and gnome) with a big X.

Are there other mouse devices I can try that support the scroll wheel?  Is there anyone here that uses maya that can send me their "InputDevice" section out of their xorg.conf?

BTW, I'm using a MX900 Bluetooth mouse.

Thanks,
-BT

---

### Post by q-ratz on 2006-03-30
Hi,

I have the same problem with the mouse cursor. Have you found a solution yet?
It really gets pretty annoying as i have to restart X to get the normal cursor back.

greetings,
q-ratz

---

### Post by ibabob on 2006-04-04
I have the same problem, very annoying indeed!

---

### Post by q-ratz on 2006-04-04
I have found a solution to this problem on this site:

[http://www2.bk.tudelft.nl/help/mayahelp/](http://www2.bk.tudelft.nl/help/mayahelp/)

the site also has a very nice introduction to maya, and solutions for other maya specefic problmes on different os's.
To solve the mentioned problem you have to add the following line to your Maya.env file, which is located in /home/USERNAME/maya/7.0
Just add:
MAYA_MMSET_DEFAULT_XCURSOR=1

That should do the trick.

---

### Post by BIGtrouble77 on 2006-06-29
q-ratz,
Thanks for the update.  I haven't had a chance to reinstall maya yet (using dapper64 now) but i'll definately give that a shot when I get my chroot up and running.  Didn't want to see this thread die without a resolution.

-BT

---

### Post by kiaran on 2007-04-03
MAYA_MMSET_DEFAULT_XCURSOR=1

Putting that in the Maya.env file worked perfectly! 
Thanks :)

---

