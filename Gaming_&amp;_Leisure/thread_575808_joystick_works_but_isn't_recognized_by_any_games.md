---
title: "joystick works but isn't recognized by any games"
date: 2007-10-14
forum: Gaming &amp; Leisure
---

### Post by 1veedo on 2007-10-14
I know there are a million joystick threads but I have this gamepad thing that is recognized and works according jtest and joystickcalibration etc but none of my games seem to be able to find it (/dev/input/js0).

How do you specify your joystick device so games can recognize it?

---

### Post by acoustibop on 2007-10-14
The easiest way is just to put a symlink to /dev/input/js0 in /dev; that's where most games will be looking for js0.

If the games (you don't say what games you're trying to play) offer some sort of configuration option to locate your controller, you could use that; otherwise you may be able to find the game's configuration and change it there.  But the symlink in /dev is easiest and should work for everything that looks for your controller there.

**Edit:**  BTW if by"joystickcalibration" you mean jscalibrator, I'd advise removing it unless you're using Kubuntu (for some reason it apparently works fine there).  It has a tendency to disable the directional buttons of controllers, although they still show as being Ok in the calibration app.  Joystick, which includes jstest and jscal, seems to work Ok.

---

