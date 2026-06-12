---
title: "Gamepad stick for mouse"
date: 2012-09-19
forum: Gaming &amp; Leisure
---

### Post by ElCheapo on 2012-09-19
yes, I know u10.4 is old but thats what I'm running

Logitec F310 usb game controller
> (II) config/udev: Adding input device Generic X-Box pad (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Generic X-Box pad (/dev/input/event15)
(**) Generic X-Box pad: Applying InputClass "joystick catchall"
(II) LoadModule: "joystick"

Pad tests GREAT operating, all axis & buttons work right with
*jstest /dev/input/js0* 
(jstest on event15 fails)

I searched and saw another thread that had a decent xorg for the pad, and using that as a base the Dpad works just fine to give WASD keyhits from its "axis" setup, and the trigger buttons map to keyhits just fine.


Problem-
When I try to map a stick (axis) to run the mouse,
the different axis modes yield results from NOPE to Works-funky.
The mode used in the other thread was Relative-
```
       Option "MapAxis4"	"mode=relative axis=x deadzone=5000"
       Option "MapAxis5"	"mode=relative axis=y deadzone=5000"
```
but that just slams the cursor into the corner when I touch the stick.

I tried the other modes
```
       #Option "MapAxis4"	"mode=absolute axis=x"
       #Option "MapAxis5"	"mode=absolute axis=y"
       #Option "MapAxis4"	"mode=accelerated axis=x"
       #Option "MapAxis5"	"mode=accelerated axis=y"
```
Accelerated was junk and Absolute 'kinda' worked:
Stick to the left would jump the cursor to the right end of the screen and THEN properly track just *How Far Left From Rightend* as I worked the stick more and more to the left. Mirror results for that stick right: Jump the cursor to left end of the screen and then properly track how far from the left as I went more & more right.
Nice, but unusable.


Why is the RELATIVE mode putting the cursor up in the corner,
and maintain a shove to the corner the mouse cant overcome,
considering that *jstest* shows the stick values went back to center


Theres a java game with a bunch of mining and crafting
that I would love to sit back on the couch and play by Dpad-Stick-Triggers
instead of keyboard & mouse at the desk

---

