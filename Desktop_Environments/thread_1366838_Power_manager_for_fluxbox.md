---
title: "Power manager for fluxbox"
date: 2009-12-28
forum: Desktop Environments
---

### Post by ~sHyLoCk~ on 2009-12-28
Hey all,
What do you use as power manager in fluxbox or any  other WMs? I am using xfce4-power-manager but the problem is it doesn't turn off the screen half the times. It's like when it's in mood and I have just boot up my pc, then after the specified time it turns off the monitor but other times it just doesn't work.
I can ```
xset dpms force off
```
but that too stays for like a minute. Any ideas/suggestions are welcome.

Regards 
sHy

---

### Post by schmolch on 2009-12-30
Try Laptop-Mode, its very reliable and offers anything that is available in Power-Management.
Look at /etc/laptop-mode.conf and into /etc/laptop-mode/conf.d/ for many more options.
After you set everything up start it with "laptop_mode" and  "VERBOSE_OUTPUT=1" in laptop-mode.conf to see if everything works, then later you can start it with "/etc/init.d/laptop-mode start"

I know this is a great reply with everything you wished for and even more, it was my pleasure to write it for you!
Have fun!

---

### Post by ipstone on 2012-01-08
thanks for this post and pointer to laptop-mode, however, when I tried this one my fluxbox, laptop, acer aspire 11 ubuntu 11.10, I got this error: generic kernel unenabled ... etc

here is my Ubuntu version, mgiht it be it's 64bit, and this particular kernel version?

3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


thanks
best regards, Isaac

---

### Post by andrew.46 on 2012-01-15
Looks like this thread has not been targeted for necroposting so I shall join in :). In fluxbox if you want simple gradated display shutdown (rather than hdd spindown) xscreensaver might very well be your friend. It is what I use on my own fluxbox setup +/- manual adjustment of screen brightness with the laptop Fn keys for screen brightness.

---

### Post by overdrank on 2012-01-15
Hi and please start a new thread with your issues. Back to sleep thread. Thread closed.

---

