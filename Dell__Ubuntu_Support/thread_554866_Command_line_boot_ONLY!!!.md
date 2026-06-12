---
title: "Command line boot ONLY!!!"
date: 2007-09-19
forum: Dell  Ubuntu Support
---

### Post by leech38128 on 2007-09-19
I have looked throughout these threads and could not find anyone that has had the same problem.  It seems that people want to boot into the command line, but I want to get out of it.](*,)
So here's the drill:  I freshly installed FF the other day and got it set up just the way I wanted, with Beryl working perfectly and wireless (Dell 1390) going good.  I finished with it last night before bed, so I shut it down.  Today when I tried to boot the laptop, it went into command line (and automatically logged in as root!!!).  I tried to reboot into the older kernel (2.20-15) and the GUI loads fine (but the wireless doesn't work).  I could not find anything out of the ordinary in 'menu.lst' (I haven't modified it at all) and uninstalled 'usplash' stuff...but it still will not boot the new kernel(2.20-16) into GUI.

I could really use some help on this, as I have already exhausted all my current resources trying to figure it out!
Let me know what additional information I need to post, if you need it.

Much Thanx

---

### Post by Lord Illidan on 2007-09-19
That sounds like the failsafe mode to me.

Tell me, when you're in there, can you type in this command :

```
/etc/init.d/gdm start
```

---

### Post by leech38128 on 2007-09-19
Yes it does...but it says "Failed to initialize HAL"
What are the reasons it might have done this?

---

### Post by Lord Illidan on 2007-09-19
Try this command :

sudo aptitude install ubuntu-desktop

perhaps we can get it how it was before.

---

### Post by leech38128 on 2007-09-19
...and it doesn't load the networking interfaces, or let me in them...it must still be in failsafe mode....

---

