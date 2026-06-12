---
title: "EPSXE padjoy and omnijoy problem, Input device problem."
date: 2008-11-17
forum: Gaming &amp; Leisure
---

### Post by linux32_user on 2008-11-17
After doing a lot a search on emulating PS games on linux using epsxe I have configured everything but cannot configure omnijoy plugin it gives the error : "Error opening device /dev/js0" , I have tried everything /dev/Input/ts0 and /dev/ts0, nothing seems to work, I also tried chmod a+r /dev/input/js0 as root but it says, Cannot open /dev/.... No such file or directory exists. I also tried checking the permissions, by ls -l /dev/input/js0, it(terminal) gives an error "cannot access /dev/input/js0: No such file or directory", so please help!!!, the game runs fine, i.e. good graphics sound etc. but no controls!!!, please help.

The same thing is with padjoy plugin, I read the whole FAQ on ammoq site, but no success, please help.

And also I am trying to configure my keyboard not a joystick.

---

### Post by linux32_user on 2008-11-17
Please help, my system specs are

Intel 3.0 GHz processor, NVidia GeForce series 5, Logitech Keyboard and Mouse.

---

### Post by wingnux on 2008-11-17
You can configure your keyboard just fine by using the internal plugin, the omijoy pad plugin is, as the name implies, for configuring gamepads on epsxe for linux.

---

### Post by disturbedite on 2008-11-17
if you'd like to try an emulator that doesn't require messing with plugins, try pSX.

afaict, most ppl consider pSX the best playstation emulator.

---

### Post by wingnux on 2008-11-17
You can never beat the visuals that some shaders can produce on ePSXe ;) For me it'll always be the best psx emulator around.

---

### Post by axm on 2008-12-12
try /dev/stdin.

---

### Post by Vvar hero on 2008-12-16
can any one help me with my pcsx i don't get the howto readme file that came with it sigh :confused::confused::confused:

---

### Post by strongfan on 2009-01-01
Hmm... when I downloaded omnijoy, all it came with was the source!  It didn't even have the compiled product!

---

