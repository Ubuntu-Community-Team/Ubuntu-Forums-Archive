---
title: "Saitek P480 Rumble Pad controls"
date: 2013-02-08
forum: Gaming &amp; Leisure
---

### Post by bennypr0fane on 2013-02-08
Hello,
I'm trying to use this gamepad to play "Psychonauts" from GOG.com through Wine. The game runs without any issues using keyboard and mouse, except that I get carpal tunnel syndrome. :P
The Saitek wasn't recognized by Lubuntu 12.04 at first, but installing 
xserver-xorg-input-joystick
fixed that.
The problem is that one of the analog joysticks performs 2 actions at once - it moves the character *and* changes camera position, but only in the vertical axis - left/right movement leaves the camera alone.
So whenever I move forward, I get a frog view of the character, when moving backwards, bird view.
Enabling/disabling the in-game "smart camera" option doesn't change anything.
The other joystick changes camera position only.
I can use the d-pad for moving only, without the camera movement, but I want to reserve the d-pad buttons for ohter actions, so I can actually control all in-game action from the Saitek. Rightz Now I can't map the the d-pad to any other actions, pressing it reveals and moves the mouse pointer.
After I added xserver-xorg-input-kbd, the keys were mapped differently to the Saitek, but the joystick issue remained.

---

### Post by bennypr0fane on 2013-02-14
[http://pastie.org/6163250](http://pastie.org/6163250)

So this looks like the wrong driver is loaded: Lubuntu thinks this is the "Jess Tech Dual Analog Rumble Pad" (and low-speed usb).
It appears that model has some sort of z-axis on the same joystick (I found out trying to calibrate it in gtk-jscal), which my Saitek then just adds to the y-axis.

```
failed to execute '/lib/udev/mtp-probe' 'mtp-probe /sys/devices/pci0000:00/0000:00:02.0/usb4/4-3 4 4': No such file or directory
```

maybe if this action succeded, I would get it right?
I don't know what it means precisely, and how I might try to fix it. Any ideas?
I have managed to play the game once *without* this issue, so at one point there must have been a fitting driver loaded.

---

