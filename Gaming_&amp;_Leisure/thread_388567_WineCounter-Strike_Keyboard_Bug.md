---
title: "Wine/Counter-Strike Keyboard Bug"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by u-blunt-2 on 2007-03-19
Here's the beef :
After installing wine and STEAM using the linux-gamers guide, I can play Counter-Strike 1.6 :) I even get a better framerate than in windows, although the emulation takes up a lot of CPU juice (both e6600 cores runnning near 100%).
However, there appears to be some problem with my keyboard. As soon as I hit space (the key to walk in game instead of running), it can't release. When I type I get all caps, and capslock status doesn't change. I am stuck in walking mode and get fragged very easily :( Changing the walk key to something else works, but as soon as I hit space again I am doomed. This is unacceptable since I always end up pressing it (can't teach an old dog new tricks).

Is there some way to change keyboard profiles with wine? Do I have to change some X11 settings ? Am I doomed to boot winblows every time I need to satisfy my headshot cravings ?

---

### Post by u-blunt-2 on 2007-03-20
This is the type of error I get from console :
```
err:keyboard:X11DRV_ToUnicodeEx (virtKey=10,scanCode=36,keycode=32,state=11)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym FE0A (ISO_Prev_Group) :

```

---

