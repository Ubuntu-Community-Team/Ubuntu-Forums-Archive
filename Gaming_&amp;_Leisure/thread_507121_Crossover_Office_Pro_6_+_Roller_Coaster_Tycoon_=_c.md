---
title: "Crossover Office Pro 6 + Roller Coaster Tycoon = choppy graphics &amp; bad performance"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by dshuck on 2007-07-22
From all the reading I have done, including at looking at the supported Wine game list, it sounds like Roller Coaster Tycoon should be running fine.   The machine has an Nvidia Geforce 5950 Ultra, which is a pretty decent video card using the nvidia drivers, so hardware shouldn't be the problem. Games like Supertux have very fluid graphics.  However, running Roller Coaster Tycoon 2 under Crossover Office Pro, the game is *extremely* slow with about 1-2 frames per second.

Does anyone have any suggestions as to what might be causing that or suggestions on what I might be able to do to fix it?  Thanks in advance.

---

### Post by hikaricore on 2007-07-22
> **dshuck said:**
> From all the reading I have done, including at looking at the supported Wine game list, it sounds like Roller Coaster Tycoon should be running fine.   The machine has an Nvidia Geforce 5950 Ultra, which is a pretty decent video card using the nvidia drivers, so hardware shouldn't be the problem. Games like Supertux have very fluid graphics.  However, running Roller Coaster Tycoon 2 under Crossover Office Pro, the game is *extremely* slow with about 1-2 frames per second.

Does anyone have any suggestions as to what might be causing that or suggestions on what I might be able to do to fix it?  Thanks in advance.

Have you properly installed the video drivers for your NVIDIA card?  And if so, how did you install them?

Are they working properly?  Check the output of:

```
glxinfo | grep rendering
```

And also make sure you are not trying to run anything in WINE (aka crossover)  while running Beryl/Compiz as your window manager.

---

### Post by dshuck on 2007-07-22
Thanks for the reply.  I installed the drivers from these instructions (using Edgy on this machine):
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-1549d676e3de65ec1342cf2c8e25df0d9745b5a7](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-1549d676e3de65ec1342cf2c8e25df0d9745b5a7)

The output of the grep is:
$ glxinfo | grep rendering
**direct rendering: Yes**

---

### Post by dshuck on 2007-07-23
*bump*

---

