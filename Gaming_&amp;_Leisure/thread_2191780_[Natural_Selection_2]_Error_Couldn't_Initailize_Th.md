---
title: "[Natural Selection 2] Error: Couldn't Initailize The Render Device"
date: 2013-12-04
forum: Gaming &amp; Leisure
---

### Post by android4682 on 2013-12-04
I bought the game Natural Selection 2 but I can't start the game on my Ubuntu 13.10 64 bit.
I'm already posting on the forum of that game but it takes for ever to approve my topic -.-
The log file says this:

```
Date: 12/03/13
Time: 17:09:41:
--------------------------------------------------------------
Build 260
Ubuntu 13.10 x86_64
Steam initialized
Num displays: 1
Error: OpenGL version 3.1 is required
Error: Couldn't initialize the render device.
```


I download some packages (mesa-utils and mesa-utils:i386 because I read online that that had opengl) but this didn't fix the problem.
Here is my [sysinfo]("http://pastebin.com/0FjjnFZ4")


How can I install the right opengl or get this game to work on another way?


Thanks,
Android

Btw: At the system settings I don't have a button Additional Drivers so I can't install any experimental drivers.
Also Team Fortress 2 and Garry's Mod works fine without any problems.

---

### Post by dannyboy79 on 2013-12-04
could you post what graphics card you're using as well as which driver please. can't help without that info

---

### Post by android4682 on 2013-12-04
> **dannyboy79 said:**
> could you post what graphics card you're using as well as which driver please. can't help without that info

Didn't you follow the sysinfo link? There stands everything about my PC.

---

### Post by dannyboy79 on 2013-12-04
sorry, didn't see that. it lists your GFX card as GeForce 610M but not the driver you're using. this is a laptop with both an intel built in gpu and a discrete nvidia card? look into bumblebee I believe

---

### Post by android4682 on 2013-12-04
> **dannyboy79 said:**
> sorry, didn't see that. it lists your GFX card as GeForce 610M but not the driver you're using. this is a laptop with both an intel built in gpu and a discrete nvidia card? look into bumblebee I believe

I will give bumblebee a try.. Tomorrow because it's night here now.

---

### Post by android4682 on 2013-12-05
> **dannyboy79 said:**
> sorry, didn't see that. it lists your GFX card as GeForce 610M but not the driver you're using. this is a laptop with both an intel built in gpu and a discrete nvidia card? look into bumblebee I believe

I installed Bumblebee and my lightdm didn't crash but NS2 still doesn't launch.
The log file said exactly the same as in the beginning.


So what do I do next?

---

### Post by android4682 on 2013-12-05
I fixed it.
My solution is here: [http://forums.unknownworlds.com/discussion/comment/2171402]("http://forums.unknownworlds.com/discussion/comment/2171402#Comment_2171402")

Thanks for everything guys! :D

---

### Post by dannyboy79 on 2013-12-06
awesome, mark the thread as solved using the thread tools

---

