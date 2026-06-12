---
title: "d-pad on tevion gamepad not working"
date: 2013-11-17
forum: Gaming &amp; Leisure
---

### Post by uncleBez on 2013-11-17
exactly like this closed thread: [http://ubuntuforums.org/showthread.php?t=1111849](http://ubuntuforums.org/showthread.php?t=1111849)
Sucks finding a thread related the exact same issue from 4 years ago, that has no reponses and has been closed. :(

Tevion gamepad, detected, everything works accept for the d-pad. use jstest and can see all buttons and movements of analog joysticks gives numbers
but the d-pad gives nothing.

Any help appreciated!

---

### Post by DanglingPointer on 2013-11-17
I had a similar problem with a Madcatz gamepad, it would automatically direct movement to the left.

I found that the M$ Xbox 360 controller works perfectly though.  If you have one of them lying around try that one instead.

---

### Post by uncleBez on 2013-11-17
Hey thanks.

I think i may have done my dosh ($30 for two controllers) so not much.
The dilong one I got doesn't work at all, doesn't even show in lsusb..

There is a shop downstairs from work that has logitic ones for $20 ($40 for wireless). I might just have to fork out again.

---

### Post by DanglingPointer on 2013-11-17
> **uncleBez said:**
> Hey thanks.

I think i may have done my dosh ($30 for two controllers) so not much.
The dilong one I got doesn't work at all, doesn't even show in lsusb..

There is a shop downstairs from work that has logitic ones for $20 ($40 for wireless). I might just have to fork out again.

Xbox 360's and her peripherals will be sold in the thousands soon if it hasn't already started (due to XBONE release).  You should be able to get a 360 controller for cheap! Try ebay.

I would say with the Linux Kernel, the 360 gamepad would've been the most tested controller thus the least amount of problems (even more than the new steam controller as of this time).  I have used the 360 controller with Metro LL, The Bards Tale, and Strike Suite Zero and all worked perfectly.

Which Kernel are you on?  What distro and version are you on?

---

### Post by efflandt on 2013-11-19
If the game does not have configuration for a gamepad, you may need to edit the text config file for it. I had to do that for my Logitech F710 in a steam space game called Salvation Prophecy. Everything on the controller worked except the d-pad. So I went to keyboard configuration in the game, pressed d-pad directions for some little or unused keyboard keys, looked at the keyboard config file to see how those registered, then went to the gamepad file and modified those movements to match. It was xml so there were input sections with following indented:

<device>Dpad</device> (was originally <device>JoyStick</device>)
<button>1</button> (was originally <button>13</button>)

That was UP. for other Dpad directions, button 16 was DOWN, 256 was RIGHT, and 4096 was LEFT.

Not sure why it did not work by default for Zoom up/down and left/right to select weapon slots, when it did work for 8 point circular menu. But modifying the xml file for Zoom and Weapon slot selection resolved that issue for me.

PS: I don't remember what the d-pad corresponds to in jstest, but if it does nothing in jstest then it is unlikely to register anything in a game.

---

