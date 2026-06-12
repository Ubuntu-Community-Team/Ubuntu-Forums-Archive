---
title: "Playing with 2 original XBox controllers at the same time"
date: 2011-01-15
forum: Gaming &amp; Leisure
---

### Post by JRBASTIEN on 2011-01-15
I'm trying to play games on Ubuntu (tested on Karmic and Lucid) with a original Microsoft XBox controller (with USB adapter) and a clone of it made by Mad Catz. 

I have no problem using one (I did not installed any driver, it was recognized and running out of the box).  But I can't play 2 players game because, the buttons of the second controller are detected like if they were pressed on the first controller.

I have installed jstest and it confirms that both controllers work fine.  Pressing buttons and moving the joystick does not show events on the wrong controller (/dev/input/js0 or /dev/input/js1).

Perhaps the problem is with the games?  I have tested with Mupen64plus and SuperTuxKart.  I had the same issue in both games.  In SuperTuxKart, I suceeded to have one player playing with the keyboard and another one with a controller.

Here is the output of jstest:

~$ jstest --event /dev/input/js0
Driver version is 2.1.0.
Joystick (Microsoft X-Box pad v1 (US)) has 8 axes (X, Y, Z, Rx, Ry, Rz, Hat0X, Hat0Y) and 10 buttons (BtnX, BtnY, BtnZ, BtnTL, BtnTR, BtnTL2, BtnThumbR, ?, ?, BackBtn).
Testing ... (interrupt to exit)

~$ jstest --event /dev/input/js1
Driver version is 2.1.0.
Joystick (Mad Catz Control Pad Pro) has 8 axes (X, Y, Z, Rx, Ry, Rz, Hat0X, Hat0Y) and 10 buttons (BtnX, BtnY, BtnZ, BtnTL, BtnTR, BtnTL2, BtnThumbR, ?, ?, BackBtn).
Testing ... (interrupt to exit)

Anybody has an idea how I could use both at the same time with no interference?

---

### Post by JRBASTIEN on 2011-01-25
I was able to play SuperTuxKart 0.7 with the help of a very kind gentleman:  Ingo Ruhnke.

The game incorrectly assumes that a trigger in neutral position is an axis moved to one of the extreme positions and thus registers it as movement, which confuses the GUI. Turning triggers into buttons works around that bug. 

The second issue is that is that it doesn't seem to have internal deadzone handling.  The signal noise in one controller will be registered as movement by SuperTuxKart and then screw up the input configuration for the other controller

The default driver (XPAD) does not provide way to workaround these bugs, so I installed XBOXDRV from Ingo.  

Follow the instructions provided here:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

And start your controllers with these options:

```
xboxdrv -i 0  --name "Joystick 1" --deadzone 8000 --trigger-as-button
xboxdrv -i 1  --name "Joystick 2" --deadzone 8000 --trigger-as-button 
```


Now if I could have the same success in Mupen64plus, this would be very good.  If anybody has been able to play multiplayer SuperMario Kart with original XBox controllers, please let me know.

---

