---
title: "Nexuiz / OpenArena jump to windowed mode...."
date: 2007-11-03
forum: Gaming &amp; Leisure
---

### Post by Mishura on 2007-11-03
I've recently upgraded to Ubuntu 7.10 and I've been having a very annoying problem with games like Nexuiz and OpenArena.

- During gameplay, almost randomly, the game will drop to windowed mode and all keyboard/mouse action is disabled.  After a second or two (usually after I DIE!) the game will jump back to fullscreen with all controls activated again.

These games worked fine before when I was running Kubuntu 7.04.  The only real difference is, that I'm running Gnome now, and Compiz is turned on.  The NVIDIA drivers are probably updated, but I'm just using the default one in the repository.

PS: These games aren't installed through the repositories, but are grabbed from their respective websites.

PC Specs:
Pentium 4 1.8 GHz
768 MB RAM (DDR226?)
nVidia GeForce FX 5200 128MB VRAM 4xAGP

Any help or insight would be gratefully appreciated.

-- Mishura

---

### Post by Kimm on 2007-11-03
Sounds like some app pops up and then dissappears.

Are you sure you dont get any notifications when this happens?

It might have something to do with Compiz

---

### Post by FG123 on 2007-11-03
I had exactly the same problem.

My solution was to write a custom script that would disable compiz before running a game and re-enable compiz after the game quit. Either that or you can disable compiz yourself before running the game. So long as compiz isn't getting in the way, you shouldn't have any unusual takeovers.

---

### Post by Mishura on 2007-11-03
No notifications when this happens...  it just seems to happen randomly.

As far as disabling Compiz, what would be the command-line argument for doing that? (So I can place that code in front of the game-start script)

---

### Post by Mishura on 2007-11-03
Disabling Compiz seems to work.  Also the games perform much better too.

---

### Post by lite on 2008-03-10
> **Mishura said:**
> 

As far as disabling Compiz, what would be the command-line argument for doing that? (So I can place that code in front of the game-start script)

I have this kind of script (/home/markus/bin/oa)

#!/bin/bash
metacity --replace &
openarena
compiz --replace &

---

### Post by doorknob60 on 2008-03-10
Ah, so Compiz is what's causing that problem. I always disable it before I play games but my brother was complaining about that. COmpiz takes forever to start on his computer because he has only 256 MB of RAM so I'm not sure if he would like switching it on and off all the time though. Nice to know though :D

---

### Post by unknown_history on 2009-04-28
In my case, disabling the screensaver did it. Simple, annoying but effective.

---

