---
title: "Question reguarding Joystick"
date: 2006-02-14
forum: Gaming &amp; Leisure
---

### Post by thespazzz on 2006-02-14
Alright I have a Game Pad that Ubunty recognizes as /dev/js0

I want to use it to play with my SNES emulator but the problum is that even though the Joystick is recognized and everything works fine in jscalibrator when I try to map the keys inside ZNES or SNES9x the dumb thing won't recognize my Directional Pad.  It recognizes every single key but refuses to see the Directional pad.

Any thoughts?

---

### Post by thespazzz on 2006-02-15
*Bump* I'm still trying to get this thing to work.  Works fine in windows and jscalibration says it's all good.

I just can't get the axis controls to do anything in any programs.

---

### Post by thespazzz on 2006-02-16
Ok another update.

On a whim I tried running ZSNES under ROOT using a sudo command.

The joystick will work under these curcumstances.  Now the odd thing is that jscalibrator will calibrate the joystick fine under ROOT or my standard user.  But agian when I run any program under my standard user the buttons work but the AXIS controls wont.  So that would make me belive permissions are not the issue as my user account can clearly access the device.

---

### Post by pmj on 2006-02-16
I have a Saitek P880. It has two analog thumb sticks and one directional pad, and it works just fine in zsnes. It's actually the only program I've gotten the directional pad to work in without any messing around.

A while ago I wanted to use the directional pad in a game called REminiscence, and to do that I had to modify its source. It was actually hard coded to only use axis 0 and 1, which on my pad is the left thumb stick, and I had to change that to axis 5 and 6. I wouldn't be surprised if most games have poor pad/joystick support only because of lazy or stupid programming.

---

### Post by thespazzz on 2006-02-16
Every game though?

I've not found anything that this will work correctly in.  And the fact it works perfectly if I run any given game with ROOT priviliges makes me think that this isn't a matter of stupid programing.  Unless maybe there is some sort of common Unix Imput interface that they are all pulling from sort of like Microsofts Direct Imput.

But even still that dosen't explain why it works compleatly under root and only partialy under a standard user.  I'd normaly chalk it up to permissions but as I said before the standard account has access to the game pad, its just only the buttons will work.

---

