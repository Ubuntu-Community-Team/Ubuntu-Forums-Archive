---
title: "Logitech Dual Action + gxmame xmame-sdl"
date: 2006-11-14
forum: Gaming &amp; Leisure
---

### Post by electroconvulsive on 2006-11-14
Hi Im running gxmame 3.5b over xmame-sdl on dapper. I ma using a logitech dual action gamepad and gxmame will not recognise it. This gamepad works well with zsnes and no config was needed. I also had it working on another box running gxmame on fedora. 

In the default options under controllers. I have tried every setting but am unsure what the correct string is to use in the box that says Joystick Device Prefix: Currently it is set to /dev/js. I dont know if this is right or how to find the proper input string to enter there. I looked in hal-device-manager and the correct string isnt listed in there either. Does anyone know why this isnt working for me and how I can sort it out.

---

### Post by electroconvulsive on 2006-11-14
OK figured it out from info given at this thread [http://ubuntuforums.org/showthread.php?t=86449&highlight=path](http://ubuntuforums.org/showthread.php?t=86449&highlight=path)
The correct path for the joystick in Joystick Device Prefix: is /dev/input/js not the default which is /dev/js.

Thanks me

---

