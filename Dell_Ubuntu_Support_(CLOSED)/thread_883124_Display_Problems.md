---
title: "Display Problems"
date: 2008-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iflanery on 2008-08-07
Got my computer back from the shop today. Once I hooked everything back up and got it up and running, I saw something quite jarring. Namely, my video resolution was correct, but the display was drastically off-center. I went into the KDE control center, went to the monitor configuration section, and told the computer to redetect my video card and display (which I did under Administration mode). I restarted, but discovered my video resolution had been reset to 1024X768. Upon trying to reconfigure, I discovered that this was, indeed, the highest resolution available. Installing Envy didn't help matters. 

I tried a last resort, this time manually reconfiguring X. I was unsure the first time around, so I restarted, thinking this would solve problems (somehow). Upon restarting, I was met with a blank prompt, so I logged in as root, reconfigured X--which worked, this time around--but presented me with a new set of problems.

Now, I can log in (but by having to run "startx") but I can only log in to GNOME. Changing from KDM to GDM didn't help. In addition, I find that the display, while better than nothing, is a tad blurry.

Anyone know how I can a) get KDM back and b) CORRECTLY configure X?

Or is it just time to upgrade?

I'm using Kubuntu Gutsy.

---

