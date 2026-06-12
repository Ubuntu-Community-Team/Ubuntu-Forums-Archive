---
title: "mobo speaker started beeping while logged in"
date: 2009-03-12
forum: General Help
---

### Post by IsmAvatar on 2009-03-12
Some background/hardware info (skip if you want). The computer is an emachines T3882 (I have a new one on the way, so don't complain. But for the duration, I'd like to keep it running). Still has the original mobo, cpu, heatsync/fans, and psu, and it's about 1-2 years old now, and haven't had any real problems with it (just limitations, being an emachines and all). I replaced the RAM with 1.4 gigs, added CD, Floppy, ATI x1300 vid card. I had windows for a while, but it finally succumbed so I replaced it with Ubuntu about a month ago.

Now for the actual problem. Just today, this started up. It randomly decided to have the mobo speaker beep at me. But it wasn't just 1 beep. It was a continuous steady stream of short beeps every half second, but the computer is still usable (although I'd personally prefer to not use it while it's doing this because those beeps are annoying).

Here's the kicker. I close all open windows, and it keeps going. I restart the X-server (ctrl+alt+backspace) (note, no reboot required) and it stops. I log back in, and a while later, it starts up again (maybe a half an hour in). This has happened 4 times so far, I think. The first time I had been logged in for several hours already.

After the second time, I knew something was going on, so I started to investigate. I checked my sensors, fans running at a good speed, cpu temp idles at a hot 48C, and gets up to 55, might be getting near time to reapply the heatsync gel, but I'm pretty sure that's not the problem, because I observed it start beeping at 47, and you'd think the computer would suddenly die if it overheated (as I've observed before).

The fact that it stops when I log out seems to indicate to me that it may be a software issue, however it would have to be a background process because closing all open windows doesn't stop it.

---

### Post by adult swim on 2009-03-12
try removing the pc speaker module
```
sudo modprobe -r pcspkr
```
if that works for you, make it permanent by running ```
gksudo gedit /etc/modprobe.d/blacklist
``` add ```
blacklist pcspkr
``` then save and close the file

---

