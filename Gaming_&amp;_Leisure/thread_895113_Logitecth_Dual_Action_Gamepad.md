---
title: "Logitecth Dual Action Gamepad"
date: 2008-08-19
forum: Gaming &amp; Leisure
---

### Post by sithpigeon on 2008-08-19
I just got a new logitech dual action gamepad and have been trying to install it. The buttons work fine but I can't get any directions to work. I've tried it in nexuiz and gfceu and gotten the same results. I have also tried using jscalibrator but have gotten no results. I read a lot of threads with this problem but can't seem to get mine working. Any ideas?

---

### Post by grossaffe on 2008-08-19
i'm pretty sure that pretty much everytime this problem comes up, its that jscalibrator is itself a problem.

---

### Post by FranMichaels on 2008-08-20
> **grossaffe said:**
> i'm pretty sure that pretty much everytime this problem comes up, its that jscalibrator is itself a problem.

Agreed. Who keeps recommending that?

Anyway, if the buttons work and not the d-pad, it's probably the left analog stick instead, press the little button above it that turns on the red led (that switches mode), and you should be golden.

---

### Post by sithpigeon on 2008-08-20
That fixed the problem with gfceu but nexuiz still won't pick up the direction controls.
I uninstalled jscalibrator too.

---

### Post by sithpigeon on 2008-08-20
I just tried calibrating it with jscal (I dont think it's the same as jscalibrator) and that didn't fix it. I tried using the controller with some other games and have gotten the same results. Oh, and the mode button just switches the d-pad and joystick. I also ran jstest and it picks up the joystick movements.

---

### Post by KillerKiwi on 2008-08-21
I used jscal to fix mine

```
sudo apt-get install joystick

jscal /dev/input/js0 -c
```

That works fine a good game to test with is supertux

I'm currently working on a simple joystick to key emulator (I couldn't find any decent easy to use linux based ones) as I use this on a mythbuntu box connected to the tv and I want a few basic games for the kids to play and not many games seem to support joysticks/gamepads and if they do support you still need a mouse/keys to work menus etc

games on the mythbuntu box so far
torcs
supertux kart
Armagetron
Powermanga
planet penguin racer
frozen bubble

---

### Post by sithpigeon on 2008-08-22
I have already calibrated my joystick using jscal and it works in jstest. I am just having problems getting any games to pick it up. I have already set up a sim link to /dev/js0 and that hasn't helped either.

As for the simple emulator, that's awesome because I know a lot of people have been looking for something like that. You should definitely post it when you're done.

Wait I just noticed that every time I boot up the computer my simlink to js0 is gone.

---

### Post by sithpigeon on 2008-08-22
I think my problem has something to do with the link dissappearing in my /dev folder. Anybody know why this is happening?

---

### Post by KillerKiwi on 2008-08-28
jkeys - [http://ubuntuforums.org/showthread.php?p=5683370#post5683370](http://ubuntuforums.org/showthread.php?p=5683370#post5683370)

---

### Post by Crafty Kisses on 2008-08-28
Post results of > lsusb

---

