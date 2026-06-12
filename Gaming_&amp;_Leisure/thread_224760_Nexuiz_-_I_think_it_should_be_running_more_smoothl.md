---
title: "Nexuiz - I think it should be running more smoothly"
date: 2006-07-28
forum: Gaming &amp; Leisure
---

### Post by faddat on 2006-07-28
Okay so I am fairly new (6 months) to linux gaming.  In the past and in the present, I have always noticed that games seem to run a bit more choppily on Linux.  I do have drivers installed, though not the very latest (just the onest that you'd install using [www.ubuntuguide.org)](www.ubuntuguide.org)).  Nexuiz runs great, and the system reports a framerate of about 70fps, but it occasionally seems to slow WAY DOWN for no good reason.  Same thing happens with both Cube and Sauerbraten, though these games give me higher FPS numbers.  All FPS games I run seem to intermittently pause/jerk fairly regularly.  As an online shooter kinda guy, it's terribly frustrating.  I don't have the fastest box (Nvidia 6200 w/128mb, p4 1.5 with 768MB SDRAM) but with windows these games would normally be silky smooth.  

Is this something that enabling CFQ would fix?  I've been reading around and that's the only thing I can think of as of yet.  

Are there any tweaks generally regarded as good before playing games with Ubuntu, other than installing the Nvidia driver?  

Should I install the very latest Nvidia driver?  If so, how do these instructions look?
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=36&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=36&Itemid=63)

As always, any and all assistance is greatly appreciated :)!

-Jake

---

### Post by mlind on 2006-07-28
Some people report that using low latency kernels with CFQ scheduling improves gameplay performance, but I haven't tested this myself.

Would be interesting to get comments from other users that use custom kernel if it really affects noticeably to overal performance.


Have you tried renicing the game (process) ?

---

### Post by abowman on 2006-07-29
Sometimes I forget that I've installed programs like apache or mysql that could be slowing things down.  You check with this command:
```

ps -fe

```

---

### Post by Lord Illidan on 2006-07-29
When playing these games and you experience this slowdown, press CTRL + ALT + F1 and you'll find yourself in a terminal.

Login, and enter top.

It should give you the processes which are consuming the most cpu time. I remember gam_server used to make my Q3 experience a hell.

---

