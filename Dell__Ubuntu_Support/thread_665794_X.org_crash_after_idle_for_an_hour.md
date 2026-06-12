---
title: "X.org crash after idle for an hour"
date: 2008-01-12
forum: Dell  Ubuntu Support
---

### Post by vanderwaal on 2008-01-12
Hey Everyone,

I rarely post in any linux forums because usually somebody has had the problem before me and there has been a resolution by this point. The problem is this:

After my computer sits idle (and note "idle", if I keep working on it I have no problem) for about an hour or more, Xorg goes crazy and starts taking up all of my CPU and eventually locks up the system fully, then I have to hit Ctrl-Alt-Backspace to restart Xserver. I have an AMD Athlon 64 x2 processor, and oddly enough the cpu usage jumps from one processor to the other, so BOTH are not maxed out simultaneously. 

I have Kubuntu (I'm posting this to the Kubuntu forums as well), and it's on a Dell Dimension C521 desktop with Nvidia GLX driver (the proprietary one from the ubuntu archives: nvidia-glx-new.

I've watched the program usage on htop, and the xserver lockup doesn't seem to correlate to any other programs that I'm running. I do keep apache running all the time, as well as a firewall (firestarter). Any ideas what might be causing this?

I should add that this IS on gutsy gibbon (hence my reason for posting in this forum). 

Thanks for the help . . . I'm still surfing forums trying to find the answer to this problem. 

-William

---

### Post by natehall on 2008-01-12
I'm getting the same problem with an Intel chip and an x3100 driver so   you can rule out the chip and the video card. (Unless by odd chance they both happen to have problems!) I suspect the problem is the power settings manager. For months not a problem for me but now that I messed with that I've had to shutdown my machine on seperate terminals occasionally.( crt alt f1 > login > sudo halt) Seems to be a fine if I set the power settings within an hour of shutdown .  Just this morning I nodded off to sleep  for a few hours with my machine on and it locked up so bad I could only turn it off by yanking out the battery!

---

### Post by vanderwaal on 2008-01-13
So I figured out that it's something with KDE 3.X . . . as it turns out X.org DOESN'T lock up at all with KDE 4.0. Odd, but true.

I wonder if its got something to do with the way KDE 3.X interfaces with X.org in Kubuntu Gutsy?

Just thought this would help :-)

-William

---

