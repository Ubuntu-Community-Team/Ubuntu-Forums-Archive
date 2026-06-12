---
title: "USB DVD can not write faster than 6x"
date: 2006-09-18
forum: Desktop Environments
---

### Post by barranco on 2006-09-18
I've been really looking for an answer in previous posts and googling, but this I just can't figure out.

I know I should enable DMA for my optical drive if its connected via IDE, but what about USB drives? mine won't burn DVD over 6x, how can I tell if its using USB 1?

could it be the mass storage controller or something?


this is driving me nuts!

---

### Post by LotsOfPhil on 2006-09-18
Type:

cat /proc/bus/usb/devices | grep Spd

You should get something like:
T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2

If you have a Spd=480 line, I think you have USB 2. Spd=12 means USB 1.1. This isn't perfect, but it's the best I've got.

6x is ~ 8 MB per second. I think you have USB 2.

---

### Post by barranco on 2006-09-19
I think I do have USB 2.0

```

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0

```

Still, don't know whats its keeping my drive to perform at fullspeed.

---

### Post by LotsOfPhil on 2006-09-19
The bottleneck could be the media you are using. What kind of drive do you have and what kind of disks are you using?

How fast can you read data? If that is only 6x then the bottleneck could be your cable (somehow).

---

### Post by barranco on 2006-09-19
I'm using Memorix 16x DVD-R discs, if I unplug the drive from the linuxbox and plug it to my laptop which have windows installed, it all works fine, I might run a VM with windows inside the linuxbox and see if I can burn at 16x with windows on that computer, maybe it's hardware related

thanks

---

