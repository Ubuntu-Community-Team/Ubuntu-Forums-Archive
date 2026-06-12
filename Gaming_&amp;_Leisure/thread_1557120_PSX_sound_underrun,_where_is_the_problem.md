---
title: "PSX sound: underrun, where is the problem ?"
date: 2010-08-20
forum: Gaming &amp; Leisure
---

### Post by {Gray-Fox} on 2010-08-20
[LEFT]Hi!
I just installed PSX, I followed this tutorial:
[http://www.ubuntugames.org/us/emulator/38-psx-emulator](http://www.ubuntugames.org/us/emulator/38-psx-emulator)

When I get to step 2, gives me this error:

[IMG]http://img36.imageshack.us/img36/7829/psxsuondunderrun.png[/IMG]



and start PSX, but I can not click on anything, **crashes**!
**Why**?

[http://img641.imageshack.us/img641/8269/schermatav.png](http://img641.imageshack.us/img641/8269/schermatav.png)

ps. 

sorry for my bad English
 [/LEFT]

---

### Post by disturbedite on 2010-08-20
a lot of people report sound problems with pulseaudio & pSX on ubuntu. i use opensuse and have never had problems with pSX period.

so maybe this is a pulseaudio problem.

---

### Post by {Gray-Fox} on 2010-08-20
> **disturbedite said:**
> a lot of people report sound problems with pulseaudio & pSX on ubuntu. i use opensuse and have never had problems with pSX period.

so maybe this is a pulseaudio problem.


There is no solution to this problem???!

---

### Post by kirbyboy on 2010-08-20
I think you need to increase latency in sound tab under configuration, but if you can't select any menu, find the configuration file and try to change it from there, in the guide you saw, in the step 8 explains where are the latency values.
By the way, you don't need to use sudo to play the emulator, only to kill pulseaudio, try it too.
Can you really run pSX with "psx-emulator" instead of "./psx-emulator"?, if it's a script instead of a binary, can you write the code here?, because it's rare you need to use sudo.

---

### Post by {Gray-Fox} on 2010-08-21
Thanks!!
Today I updated ubuntu 9.10 to **ubuntu 10.04**, and now everything works out fine!
There is only a small problems with the audio! but not serious!! [COLOR=#000000]The audio stops sometimes!


[/COLOR]

---

### Post by kirbyboy on 2010-08-23
It's the same solution, increase sound latency, but it sound stops 1 second when you do a save state, that's normal.

---

