---
title: "FCE Ultra and Original XBox Controller D-Pad"
date: 2010-03-21
forum: Gaming &amp; Leisure
---

### Post by derrick81787 on 2010-03-21
Hello everyone,

I have modified an original XBox controller so that I can plug it into the USB port on my computer.  It works beautifully in SuperTux, but now I'm trying to get it to work in FCE Ultra.

I've run this command to configure the controls
```
fceu -inputcfg gamepad1 rom.zip
```

and it, almost works.  It allows me to set all my buttons, and I can set up, down, left, and right to the left joystick.  However, it's kind of weird playing Mario with a joystick, so I'd like to set those buttons to the d-pad.  Unfortunately, when I'm setting the controls, FCEU doesn't recognise the d-pad.

Has anyone here been able to use the d-pad with FCE Ultra?  On a less important side note, what about SuperTux2?  For some reason, it works in SuperTux, but I'm having basically the same problem in SuperTux2.

I appreciate any help anyone can offer.

Thanks,
Derrick

---

### Post by derrick81787 on 2010-03-21
Anybody?  Should this have gone in a different forum?

---

### Post by derrick81787 on 2010-03-29
It turns out, that FCEU's joypad support isn't very good at the moment, and that is the problem.  I got around it by using a program to map joystick/joypad buttons and axis to keyboard buttons.

I tried a few different programs, but the one that ended up working for my was QJoyPad.  I didn't really want to use a QT program since I run GNOME, but it is by far the best.

Check out [this thread]("http://ubuntuforums.org/showthread.php?t=971455&page=16") for more information.

- Derrick

---

### Post by Defrector on 2013-03-23
I am resurrecting this thread because I believe I've found a better solution:

First, make sure your controller is properly calibrated with the command:
```
jscal -c /dev/input/js0
```

In the same terminal session as that used to launch (g)fceu, set the SDL_JOYSTICK_DEVICE environment variable as follows:
```
export SDL_JOYSTICK_DEVICE="/dev/input/js0"
```
... this would seem redundant since it already appears to be finding the gamepad anyway, but for some godforsaken reason doesn't read it correctly unless the above is set.

Then run fceu:
```
fceu -inputcfg gamepad1 YourRomHere.nes
```
... or you could run gfceu and manually go into the controller configuration tab and start mapping your controller.

It literally should be typed 'gamepad1'.

Note that the controller configuration sequence is very quirky and you might have to try more than once for it to set up correctly: the slightest nudge, a breeze, or a ghost farting in the other room can move one of the joysticks by a value of 1 and that will make fceu think that is the 'button' you attend to bind.

...then it's a matter of automating the setting of this environment variable into your launch scripts or whatever.

---

