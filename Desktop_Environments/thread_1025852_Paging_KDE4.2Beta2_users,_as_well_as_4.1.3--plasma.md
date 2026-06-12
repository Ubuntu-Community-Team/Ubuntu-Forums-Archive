---
title: "Paging KDE4.2Beta2 users, as well as 4.1.3--plasma hangs?"
date: 2008-12-30
forum: Desktop Environments
---

### Post by Skripka on 2008-12-30
I've had this happen on KDE 4.1.3 as well.....


Every now and again, Plasma hangs.

Yes, every now and again.  I cannot really be more specific than to say that when it hangs it is for ~10 seconds.  Sometimes happens twice in the space of an hour-sometimes can go for hours without it freezing.

Symptoms:

-Entire DE is unresponsive, clock plasmoid freezes--plasma and desktop effects in mid-process (changing desktops, minimizing windows, closing applications) freeze--only the mouse moves.  Applications freeze in mid-process (such as scrolling in Opera, or playing a game)...BUT-inputs are still recorded, i.e. a scroll wheel event in Opera made during a freeze--will occur after the freeze stops.

-1 processor core goes from 0%-100% in about 1 second.  Only 1 core of 2.

-No one thing triggers it consistently--though closing apps or minimizing windows or changing desktops seems to coincide more often than not.



Now, I know how y'all think...leave Top running in the Konsole-and catch the offending process.....

-When I have Top running in Konsole in a corner of my monitor (still visible) this occurs much less frequently.  Also, when it happens-Top NEVER catches any process rising or locking up.  System freezes-as does Tops output, and when things resume-theres nothing in Top that tells me anything.

-When I have System Monitor running in the background, I get similarly no data, and fewer freezes.

-You're probably wondering, "Skripka how do you know 1 core is at 100% load when top is frozen????"...that output I'm getting from the LCD panel on my G15 keyboard running G15stats (shows CPU load)


Ideas or theories?  I had this happen on KDE4.1 also, but on 4.2Beta2 it seems more frequent.

---

### Post by mandetsis on 2009-01-08
I have the same problem. It seems that plasma crushes and restarts. 
For 10 secs nothing works, then everything is back to normal (no sound, no mouse, nothing).
 I have noticed that it happens more often than not when starting ktorrent (just in the beginning not when ktorrent is running for a while) 
or when opening a new window after a pause in activity. I cannot replicate it when I want. It just happens on its own unfortunately.


update-I have done a clean install of kubuntu 9.04 (alpha5). NO more problems. Plasma is very fast and even when it crashed once, it was backup instantly. My previous (the problematic one) installation was Ubuntu 8.04 -> kubuntu 8.04 -> kubuntu 8.10 via upgrades. Perhaps it did not go as smooth as it should. Note that 9.04 uses the 180 nvidia drivers.

---

### Post by schermozzel on 2009-02-17
I get this a lot on kubuntu. I am using compiz instead of kwin and I assumed that was why. It happens roughly every 10 minutes for up to 2 minutes at a time, compiz greys out the panel and I can't do anything with plasma

I have no idea what is causing it

---

