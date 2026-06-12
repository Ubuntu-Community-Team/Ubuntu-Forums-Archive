---
title: "Parallel port and SNES v.Not Working"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by MarshyTheKid on 2007-07-22
Okay, so I'm trying to get my SNES pad to work. I have Zsnes installed. I followed an online tutorial on jumping with the paperclips. 

I followed this to get it working.
[http://ubuntuforums.org/showthread.php?t=30009](http://ubuntuforums.org/showthread.php?t=30009)
My computer sees the pad, but will not do anything about it. jstest returns this:```
 jstest /dev/js0
Driver version is 2.1.0.
Joystick (SNES pad) has 2 axes (X, Y)
and 8 buttons (BtnX, BtnY, BtnTL, BtnTR, BtnTR2, BtnSelect, BtnThumbL, BtnThumbR).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off 
```

When running zsnes from terminal, I get this:
```
zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Simple DirectMedia Layer output
Channels: 2
Rate: 32000

Device 0 SNES pad
  2 axis, 8 buttons, 0 hats, 0 balls


```
I don't know if it has anything to do with the read permissions on the input events. I tried running sudo zsnes, but the game still wouldn't use the pad.
Can anyone help me with this?

---

### Post by hikaricore on 2007-07-22
>  jstest /dev/js0
Driver version is 2.1.0.
[I][B]Joystick (SNES pad) has 2 axes (X, Y)
and 8 buttons[/B][/I] (BtnX, BtnY, BtnTL, BtnTR, BtnTR2, BtnSelect, BtnThumbL, BtnThumbR).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:Axes:  0: 

> [I][B]Device 0 SNES pad
  2 axis, 8 buttons, 0 hats, 0 balls[/B][/I]

Looking at the ZSNES output based on the jstest output, it very certainly is seeing the joystick.
The /dev/input devices shouldn't be an issue.

Have you attempted to configure the joystick in the ZSNES settings?

---

### Post by MarshyTheKid on 2007-07-22
Well on zsnes, all I have for devices are "None" and "Keyboard/Gamepad" I have it set up for Keyboard/Gamepad. When I click on 'Up' to set the key, I then push up on my snes controller, and it doesn't register.

---

### Post by MarshyTheKid on 2007-07-22
I tried out a second controller and it didn't work either, so either I have two SNES controllers that don't work, or its something else. I also double checked my jumpers with a friends and they're the same.

---

### Post by hikaricore on 2007-07-22
Your system is obviously seeing your controller.
And zsnes is obviously seeing your controller.
But it's just not working for some reason or another.

Have you tested it out with any other game/software to see that it's working?

---

### Post by MarshyTheKid on 2007-07-22
I just tried it with Mednafen and also on GFCE Ultra(Tried configuring the joystick)

---

### Post by MarshyTheKid on 2007-07-22
I'm having trouble finding any help on getting it to work at all.

---

### Post by MarshyTheKid on 2007-07-23
Can anyone shed some light? This is really a pain. I don't understand why I'm having these problems.

---

### Post by MarshyTheKid on 2007-07-23
I tried a reboot and, as expected, no change.

---

### Post by MarshyTheKid on 2007-07-24
Any help here?

---

### Post by MarshyTheKid on 2007-07-26
Anyone at all?

---

