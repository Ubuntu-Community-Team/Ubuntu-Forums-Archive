---
title: "Stuck Brightness on Asus computer"
date: 2012-12-04
forum: Desktop Environments
---

### Post by muttstuffle on 2012-12-04
Alright, I've seen this plenty a time on these forums but none of the fixes I have seen have worked for me, so I will give as specific details as possible.  My brightness won't change on my computer and the back-light is practically blinding, I can't look at it unless I'm in a very bright room or area.  My computer is an Asus g74-sx A1, with ubuntu 12.04 LTS sideloaded onto the computer.  My video card is a nvidia GeForce GTX 560m and the driver I am using is the NVIDIA accelerated graphics driver [version current](Recommended)  How would I go about fixing the problem of my brightness being stuck? Any help is greatly appreciated.

---

### Post by Toz on 2012-12-04
Hello and welcome to the forums.

Since you have the nvidia drivers installed, does adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Devices section of /etc/X11/xorg.conf fix the problem for you?

If that doesn't work, you may want to have a look at the nvidiabl backlight driver at: [https://github.com/guillaumezin/nvidiabl]("https://github.com/guillaumezin/nvidiabl")

---

### Post by muttstuffle on 2012-12-09
Thank you so much, your fix worked!  Something tells me I'm going to be dealing with xorg.conf quite often from this point forward :P

---

