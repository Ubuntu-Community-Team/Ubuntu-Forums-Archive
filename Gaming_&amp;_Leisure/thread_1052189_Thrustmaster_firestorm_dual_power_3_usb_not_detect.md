---
title: "Thrustmaster firestorm dual power 3 usb not detected"
date: 2009-01-27
forum: Gaming &amp; Leisure
---

### Post by ceminess on 2009-01-27
Hi, I've been a long time browser of the forums and I always pride myself in figuring out things myself but this one I cannot get to work.  I dunno maybe i'm just having a bad day.

I'm trying to get my Thrustmaster gamepad to work specifically using emulators ZSNES and GFCE.

it is a usb gamepad.  I have installed joystick and jscalibrator and ran sudo chmod 666 /dev/input/js0 which gave me no error but when I run cat dev/input/js0 it says no such device.  I have tried different usb ports, and js1,2 etc. but none seems to work.

Thank you!

---

### Post by I-User on 2009-01-28
I have the identical problem, and I can not find a single comprehensible answer in any of the forums. Like the user above I have a reasonable sense of self reliance and yet no amount of research seems to answer this simple problem.

I am so frustrated I feel like throwing the thing across the room.

While I have not been using Linux long (just under half a year) I am blown away by the simple problems that seem to become mountainous hurdles. I am trying to be patient with the learning curve but I really haven't got clue one as to where to start to just get things working.





CAN SOMEONE PLEASE HELP ME!





all I want is to use my game pad...or if that is not an option to understand why?

I have tried JScalibrator, it seemed to register input and snes9x seemed to even recognize that one of the buttons was there, that's as far as I got.


it shouldn't be THIS hard.



Please help me.

---

### Post by I-User on 2009-01-28
I have done some more research, and found what seems to be evidence that someone...somewhere knows how to accomplish the mysterious feat of getting a game pad to work on Ubuntu, unfortunately telling someone what to do is...

NOT THE SAME

As telling them how to do it. 


So, unfortunately I can do nothing to hook up a simple game pad.


 
please help me....I don't even care about the game pad anymore I just want to understand what I am doing wrong here so i can learn.

:(

---

### Post by sultanoswing on 2009-02-06
I have the exact same gamepad and it's previously worked in both Ubuntu and Arch. It stopped working for me with Arch, using the latest stock kernel (2.6.28-ARCH). Haven't yet tried it on Ubuntu (Intrepid Ibex, all updates).

Pad still works fine in Windows, so I'm thinking this is a regression in the kernel and/or module(s) for this device. I'm hoping it's part of an upcoming inclusion of the so far [EXPERIMENTAL] force feedback for these devices.

---

### Post by sultanoswing on 2009-04-21
Problem solved in the 2.6.29 kernels. Pad is working again, but annoyingly, there is no longer a Force Feedback driver in the kernel for this device (at least not that I have found). Oh well.

---

