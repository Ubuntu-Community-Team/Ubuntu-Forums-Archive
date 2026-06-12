---
title: "Gamepad problem with Mupen64"
date: 2009-07-31
forum: Gaming &amp; Leisure
---

### Post by santiagocajiao on 2009-07-31
Hi all.

Well I've searched in several forums about this problem without getting a possible solution.  Hope to someone can help me :)

Recently I bought 2 gamepads and I've installed Mupen64 in my PC (Ubuntu 9.04).  I've tested the gamepads in other NES and ZSNES without any problem, but when I try to use them in Mupen even after mapping the keys in the plugin options, when I play the analog Right & Down axis fail!  it's very weird because I go back to the plugin conf window and I set the values again to ensure that all is well done, but these values reset when I play :s

If someone knows please help me!!!!!!!

PS: I also have a Xbox Wireless guitar working and no compatibility issues were found between the guitar and the gamepads.  I have installed the JScalibrator as well...everything works good but Mupen64.

---

### Post by BoyOfDestiny on 2009-07-31
Try [mupen64plus]("http://code.google.com/p/mupen64plus/") instead, as mupen64 is out of date.

---

### Post by efikkan on 2009-07-31
Wich controller plugin do you use in Mupen64?

---

### Post by dfreer on 2009-07-31
> I have installed the **JScalibrator** as well...everything works good but Mupen64.

This could also be your problem, although your error isn't exactly the same.
[https://www.linuxquestions.org/questions/linux-hardware-18/usb-joystick-problem-on-debian-sarge3.1.....-375650/](https://www.linuxquestions.org/questions/linux-hardware-18/usb-joystick-problem-on-debian-sarge3.1.....-375650/)

I would try uninstalling jscalibrator completely, making sure to remove all files including that ~/.joystick file and see if that helps. Beyond that, try a different controller plugin.

---

### Post by santiagocajiao on 2009-08-01
Thank you all for your help.  I've uninstalled JScalibrator and everything seems to be working, at least a couple games worked very well.  What i've noticed is that some N64 games just make the gamepad settings crash by changing the X and Y axis values to "+".  Now I think that this could happen because I have two gamepads of the same type and the emulator sometimes recognize them as 1. Could it be possible?

---

### Post by santiagocajiao on 2009-08-02
**UPDATE:  **After several tries I've discovered the problem and I think it's the Blight's SDL Input Plugin in Mupen64.  What I did was to install Project 64 v1.6 using Wine and then map my joysticks with the NRage Input Plugin.  Everything is working now! no conflicts, no axis problems...

Thanks for you help :)

---

