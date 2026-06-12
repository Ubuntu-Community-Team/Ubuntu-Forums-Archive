---
title: "Compositor error at shutdown/restart"
date: 2009-04-29
forum: General Help
---

### Post by Kizsde on 2009-04-29
Hi Guys!

Lately I installed Jaunty on my machine and everything seems to be working flawlessly except some minor annoyances. One strange thing is that whenever I restart/shutdown Ubuntu, I get some system beeps while a notification/error window appears for a second and then the computer restarts/shutdowns. I never managed to take a close look at the error, as it almost instantly goes away as the system reboots. I got a glimpse once and it said something about 'compositor' as far as I could tell. I have been searching the forums for this kind of issue, but couldn't really find anything identical. From the research I did, I'm suspecting it has to do something with compiz or avant windows navigator, but I'm not sure.
If anyone experienced this or knows what might be causing this, please let me know. Any input is appreciated!

Thanks,

Kizsde

---

### Post by Kizsde on 2009-04-29
Is it just me who has this issue???:confused:

---

### Post by michaeldt on 2009-04-29
I have the same problem. Quite annoying that I can't see what the error is. Anyone know if these errors are logged and where the logs would be?

---

### Post by ReddJones on 2009-04-30
I have the same problem... Its BS. 
My solution is to enter

[PHP]sudo modprobe -r pcspkr[/PHP]

---

### Post by Kizsde on 2009-04-30
But that command is just to do something with the PC speaker, right? I really want to know what the error says and why it pops up. It would be good to check if there is any log file about this somewhere, as 'michaeldt' suggested.

---

### Post by jiffyloose on 2009-04-30
I have the same issues.  I have gotten rid of the beeps with the blacklist but the "error" message still pops but to fast for me to see.  I am using both awn and conky....I think if I close awn first before shutting down or restarting I don't see the box.  ANyone?

---

### Post by Kizsde on 2009-05-01
Hi!

I just have AWN and yes, I can confirm too, that if I exit AWN before restarting the PC, it won't give the error window. So I guess we can safely say that AWN is giving some kind of an error.

---

### Post by scweston on 2009-05-03
Hi,

I also have the same problem. I think its because as the computer shuts down it unloads compiz which is the compositing software that awn relies on. So, therefore, awn gets a little upset and throws an error message at you just before awn itself is unloaded.

I think the beeps are an unrelated issue as I had that problem even before I installed compiz or awn. It's just a coincidence that they happen to occur at the same time on shutdown.

I don't know how to fix the error message issue, but would probably revolve around changing the order in which things are unloaded as the computer shuts down (i.e. making sure awn gets unloaded before compiz). Unfortunately I don't know how to do that... but if someone else could suggest a method?

Stephen

---

### Post by ZootHornRollo on 2009-05-30
i am having the same problems to with the error message and beep on shutdown.

Also using AWN.

More of an annoyance than a problem but would be nice to be able to solve.

---

