---
title: "CPU usage around 100%"
date: 2009-01-24
forum: Gaming &amp; Leisure
---

### Post by pme 72 on 2009-01-24
I am new to games. When I start SuperTuxKart my CPU usage goes to about 100%. Is this normal? I have played the game for extended periods of time and have not noticed any ill effects with the machine.

CannonSmash usually draws between 85-95%.

---

### Post by gjoellee on 2009-01-24
1. Please give me the output of this command:
```
uname -p
```2. While having the game open, can you go to your "System Monitor" and show me your top 3 CPU usage tasks.

---

### Post by khelben1979 on 2009-01-24
Revealing what hardware configuration you have over there might give us a better understanding in order to judge if the cpu usage is normal or not for that game.

Also, with bad graphic drivers the cpu will haveto work harder.

---

### Post by pme 72 on 2009-01-24
peter@peter-desktop:~$ uname -p
unknown

When game is opened:
SuperTuxKart ~28%
PulseAudio ~ 15%
Gnome System Monitor ~11%

With the game running (not playing):
SuperTuxKart ~58%
PulseAudio ~ 15%
Gnome System Monitor ~11%

---

### Post by pme 72 on 2009-01-24
khelben1979, thank you for the reply.

System specs: Compaq Presario SR1675CL, AMD64 3500+ (2.2), 250GB HD, 3 GB ram, ATI Radeon Xpress 200 integrated graphics.

---

### Post by pme 72 on 2009-01-29
SuperTuxKart seems to be OK. It is running the CPU in the 70-90% range during play. Turning off the System Monitor might drop that even further. 

CannonSmash causes the CPU to spike to 100% when the game starts and it stays there. In System Monitor the top three drains on the CPU are:

CSmash 90%
Sys Monitor 4-10%
Pulse Audio 2-8%

I am running 8.10 with the Open Source drivers for my video card. Am I doing potential damage to the CPU by playing a game that causes the CPU to peg at 100%?

---

### Post by eragon100 on 2009-01-29
> **pme 72 said:**
> SuperTuxKart seems to be OK. It is running the CPU in the 70-90% range during play. Turning off the System Monitor might drop that even further. 

CannonSmash causes the CPU to spike to 100% when the game starts and it stays there. In System Monitor the top three drains on the CPU are:

CSmash 90%
Sys Monitor 4-10%
Pulse Audio 2-8%

I am running 8.10 with the Open Source drivers for my video card. Am I doing potential damage to the CPU by playing a game that causes the CPU to peg at 100%?

No, your CPU can handle that. It's designed to be able to run at full speed without getting too hot. It only gets dangerous once you overclock it, i.e. run it at more than 100% :wink:

---

