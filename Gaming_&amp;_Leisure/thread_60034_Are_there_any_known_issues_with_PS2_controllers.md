---
title: "Are there any known issues with PS2 controllers?"
date: 2005-08-26
forum: Gaming &amp; Leisure
---

### Post by the_it on 2005-08-26
I have DL USB ps2 controller that I use for xmame.  To my understanding such controllers are treated as joysticks.

To use a joystick I need to install joystick and jscalibrator from our apt sources.  I installed it without a hitch.  I also heard that one might have to change the permissions on the /dev/input/js0 to chmod 666.

I get to use the controller with no problems until sometime in the middle of a fight, when one button seems to think it's being pressed when it isn't.  I haven't been able to reproduce the error intentionally, but it always pops up in the middle of a gaming session.

One visual symptom of this is that the controller's analog light blinks furiously (it should either be steady ON or steady OFF).  At this point the controller will keep pressing button 1 (I think).  I cannot get it to stop pressing button 1 until I unplug it, quit xmame.SDL, and replug it and restart.  Suffice it to say that's quite annoying.

the controller has a turbo and a slow button.  However, I cannot reproduce the error by pressing any combination of the turbo and slow buttons.  I can only ask if we have any known issues (and workarounds) with PS2 controllers.

---

### Post by Mishura on 2005-08-26
I got a Radio Shack USB adapter for PS2 controller, and I got a plain DualShock2 hooked up.  No problems, and no extra programs needed for it to work.  (True plug and play.)

I was able to use it with Zsnes, FCE Ultra, Descent 3 Linux, TuxRacer, and a few others.  It even works in Wine games like Battlefield 1942.

To get the controller to work in games that don't have joystick support, I use QJoyPad (Search KDE-Apps.org).  I can map keys to controller buttons, as well as turn digital movement controlls into analog-like axises for my analog or digial pads.

I'm not sure if Linux fully supports Turbo/Macro buttons.  I tried a MadCatz controller that had a macro function, but it was borked in Linux AND Windows.  I guess the USB drivers don't know want to make of it.

---

### Post by astyanax on 2006-03-06
How did you get it working for FCE Ultra?  Is there some parameters that you need to pass to fceu at the command line so that the gamepad works?  I'm trying the same exact setup as you have with a dualshock PS2 controller and PS2 controller to USB converter cable.  I have it working for ZSNES inside MythTV and I'm trying to get it to work for FCE in MythTV as well.

I tried starting FCE with this command:
```
fceu -opengl 0 -fs 1 -joy1 1
```

FCE starts fine, but the gamepad doesn't work.

Any ideas?

---

### Post by astyanax on 2006-03-06
Nevermind.  I found it here:
[http://www.ubuntuforums.org/showthread.php?t=16961&highlight=fceu+gamepad](http://www.ubuntuforums.org/showthread.php?t=16961&highlight=fceu+gamepad)

```
fceu -inputcfg gamepad1 rom.zip
```

---

