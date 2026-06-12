---
title: "One-time joystick calibration?"
date: 2006-09-29
forum: Desktop Environments
---

### Post by psYchotic on 2006-09-29
Is there a way to save the calibration for a joystick somewhere, and have it loaded everytime said joystick is plugged in? The reason I'm asking this is because I have a joystick, and every now and then it gets unplugged either by accident or because I need to use other USB devices, and whenever I plug it back in, I have to go through the whole calibration stage again, which is a pain when you have to repeatedly do it.
Thanks in advance =)

---

### Post by ringmaster on 2006-10-19
Hi from Spain,
I have the same problem, if there is someone to help us out...
I don't know if this is a problem with kde config or with the Linux kernel itself, I will see if this "bug" is filled anywhere (Launchpad, kdebugs and kernel bugs).

It could be solved by "remembering" calibrations, and when the joystick with the same "id" (if there is a system to recognize it the same joystick is attached) reasign the calibration.
I am not a true programmer, but the easy solution would be to make a list and when a Joystick is attached then let the possibility to select which calibration is related to it.

---

### Post by jsandys on 2006-10-19
Saving the joystick calibration is described in the linux documentation, section 2.6.
[http://www.charmed.com/txt/joystick.txt](http://www.charmed.com/txt/joystick.txt)
This worked for me but my joystick is attached to the gameport.

---

