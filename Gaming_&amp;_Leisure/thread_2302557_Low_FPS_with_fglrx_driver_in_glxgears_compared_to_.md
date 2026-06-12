---
title: "Low FPS with fglrx driver in glxgears compared to intel"
date: 2015-11-11
forum: Gaming &amp; Leisure
---

### Post by Separ on 2015-11-11
Hello!

I have a Dell Latitude E6540 laptop running Ubuntu Gnome 15.10 and for some reason, the fglrx drivers don't perform anywhere near as well as the Intel integrated graphics. Running the following: ```
vblank_mode=0 glxgears
``` results in around 8k FPS with the intel chip but only around 700 with fglrx installed either via the Additional Drivers dialog or the latest from the AMD website.

I have used three different versions of Ubuntu (14.04, 15.04 and 15.10) on this laptop and it has been roughly the same performance in each. glxinfo also definitely shows the correct graphics processor being used.

System Specifications:

CPU: Intel Core i7-4810MQ
RAM: 16GB
Graphics: Hybrid Intel HD Graphics 4600 / AMD Radeon HD 8790M

---

### Post by mastablasta on 2015-11-12
have you tested it with some other progs? like glmark2 or one from the phoronix test suite?

---

### Post by Separ on 2015-11-12
I haven't tried that but the animation performance in Gnome is also a lot worse while using the AMD GPU :\

---

### Post by QIII on 2015-11-12
glxgears is not a good benchmarking tool.

Anyway, if you go to Catalyst Control Center and change all the quality settings to performace and make sure Tear Free is off, your reported FPS will skyrocket to unreasonable levels.

---

### Post by Separ on 2015-11-12
That may be true but it doesn't explain why Gnome is performing so badly with the hot corner and window animations with the default settings. Surely that won't stress the GPU that much?

---

### Post by mastablasta on 2015-11-15
> **Separ said:**
>  Surely that won't stress the GPU that much?

question is if the GPU is even used. if it is not all piped to CPU and some software mode enabled. 

not really directly connected but had similar experience when i used nomodest recently in live session (software accel.). once i managed to boot with normal mode it was all flying.

---

