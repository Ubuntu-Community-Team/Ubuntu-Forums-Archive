---
title: "Counter Strike boot splash screen."
date: 2006-07-02
forum: Gaming &amp; Leisure
---

### Post by orgy on 2006-07-02
i made a counter strike splash screen, just follow the instructions in the thread below to make it work:
[http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835)

its pretty simple, hope u like it.

---

### Post by Brain Juice on 2006-07-02
i like where your going with this.  \\:D/  

have you had any success running cs:s in dapper?

---

### Post by orgy on 2006-07-03
i ran it one time on cedega, textures where a little messy but playable, but still is better to run it under windows :(. I get better ping on linux though. The only reason i havent moved completly to linux it's because of counter strike source.

---

### Post by Brain Juice on 2006-07-03
damn, I was going to try it this week.  I'm in the same boat.  :-|

---

### Post by tospig on 2006-07-03
me too ^^

even though i'm still a complete newbie, i'm starting to really love this OS - and am getting all my friends who don't play games to try it out. :)

---

### Post by orgy on 2006-07-03
i spend all day on ubuntu, and when its time for me to play some games, got to reboot, go winxp, and play counter strike source or silkroad online.

we need these games native :(

---

### Post by tospig on 2006-07-03
at the moment my windows machine is broken (the motherboard is fried) so no CSS for me for a while :( 

that's why I installed ubuntu on a spare machine I had, and am loving it :)

---

### Post by der_joachim on 2006-07-05
[QUOTE=Brain Juice]i like where your going with this.  \\:D/  

have you had any success running cs:s in dapper?[/QUOTE]

I did actually. I followed [this guide]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games") and made a few shell scripts to launch either HL2 or CS:S. I just used the wine version in the Wine repo. No Cedega for me.

---

### Post by orgy on 2006-07-06
i was able to install it, couldnt get css running but ran hl2 til main menu. what graphics card u got?

---

### Post by Brain Juice on 2006-07-06
I used Cedega and got i running but its still not a great experience playing.  :(  FPS is ok (40-70) but just feels jumpy, laggy and disorienting.  I cant hit anything.  

Ive got a pretty good setup with an AMD 3700, 7900GT and 2 G of ram.  

Im gonna try to use xubuntu next and try your link to wine (thanks!) see if that is any better.

Any recommendations appreciated.

---

### Post by WildTangent on 2006-07-06
I can run CS 1.6 and CS:S using Cedega on my machine, but they really don't perform well in comparison to Windows. Battlefield 2 is completely unusable, so I have to keep Windows :(

-Wild

---

### Post by der_joachim on 2006-07-07
> **orgy said:**
> i was able to install it, couldnt get css running but ran hl2 til main menu. what graphics card u got?

A GeForce FX 5600. Nothing special. Here's the script I use for CSS: 
```

#!/bin/bash
WINEDEBUG="-all" nice -n 20 wine C:/Program\ Files/Valve/Steam/Steam.exe  -fullscreen -width 1024 -height 768  -applaunch 240 -heapsize 768000 -console  -novid -gl -dxlevel 70 "$@"

```

The one that got my copy of HL2 to work, was the *dxlevel 70* option. Apart from some graphical glitches, I never had any real trouble playing HL2. The same script with the *-applaunch 220* option starts the HL2 game. 

However, I'm getting waaaaayyy off-topic here. To the OP: Good work!

---

