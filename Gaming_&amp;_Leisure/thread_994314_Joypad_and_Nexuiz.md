---
title: "Joypad and Nexuiz"
date: 2008-11-26
forum: Gaming &amp; Leisure
---

### Post by ZERO16LIVES on 2008-11-26
:cry: im sorry if this is a stupid question but i want to know if there is a way to use a joystick to turn instead of the mouse
any help is appreciated

---

### Post by detrate on 2008-11-27
I thought this was supported out of the box.  Have you tried it?

---

### Post by crazyfuturamanoob on 2008-11-27
Try joy2key to convert joystick/gamepad events to key presses, then set the controls in Nexuiz's in game options, and play.

---

### Post by ZERO16LIVES on 2008-11-27
what i meant was the joystick works fine in the game but turning and looking up/down is done with the mouse and there is no setting to change that.
thanks for the responses though.

---

### Post by niaz13 on 2008-11-27
oystick works fine in the game but turning and looking up

---

### Post by detrate on 2008-11-29
If you're using an older joystick, it may not be properly support.  If you tell us more (what kind of joystick), we can assist you further.

---

### Post by afroman10496 on 2009-09-08
Ok sorry for the bump but I have the same problem too. I have a Logitech Dual Action.

---

### Post by RabidWeezle on 2009-09-09
not to sound mean, but never bring a gamepad to a mouse fight? I would think you would get slaughtered VS. the mousers. Only thing I would use a gamepad for is like emulators. But have you checked out the /bind commands in nexuiz, like /bind <key> <command>

---

### Post by mkngl84 on 2013-02-26
This is quite an old thread but to answer the question with the new and improved Xonotic (previously Nexuiz) you can reference this thread to setup joysticks:
[http://forums.xonotic.org/showthread.php?tid=3044](http://forums.xonotic.org/showthread.php?tid=3044)

In the console, look for cvars that start with "joy_" by typing that and pressing tab. You're looking for:

joy_axisforward
joy_axisside
joy_axispitch
joy_axisyaw

Entering a number after this will set the axis to use.

---

