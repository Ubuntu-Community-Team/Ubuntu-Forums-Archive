---
title: "Something is not right with 8.10"
date: 2008-12-18
forum: General Help
---

### Post by trendyabinash on 2008-12-18
Sir I am facing an unknown problem.

My ubuntu 8.10 is working perfectly fine, but after a few hours it just don't act normal.

Nothing works at all, my internet stops, I can not open synaptic package manager, All I can do is move my mouse here and there click and wait for it but nothing opens at all, and I have to restart my system.

After restart everything becomes normal again. I am just blank about this kinda problem, no error message nothing, please help me out.

I am using a wifi network using the software ndisgtk, as I didn't find a linux driver for my card, is it creating the problem?? Just a blind guess not sure though.

PLEASE HELP ME, I have lots of work on the net, I can not sit on PC 24 hrs but it has run, a few days back this happened so I thought may be it is because I keep on trying new possibilities in my ubuntu, so i might have corrupted some files so I reinstalled my ubuntu, but the problem still exists.

ANY HELP is heartly welcomed

---

### Post by trendyabinash on 2008-12-18
I have used these steps to install my device driver

[http://ubuntuforums.org/showthread.php?p=6386869#post6386869](http://ubuntuforums.org/showthread.php?p=6386869#post6386869)

---

### Post by mathieuI on 2008-12-18
can you use the keyboard shortcuts like ctrl + alt + F(1-6) ? (for the tty)

---

### Post by SteveDee on 2008-12-18
You could try installing the application "System Monitor" and set it up so that you can see graphs for (say) cpu% usage and Network. This may help when the system stops (e.g. is the cpu heavily loaded?).

Also the application "X Sensors" may show you whether the cpu is overheating.

---

### Post by trendyabinash on 2008-12-18
> **mathieuI said:**
> can you use the keyboard shortcuts like ctrl + alt + F(1-6) ? (for the tty)
thank you for prompt support
Yes it was working but had not tried it last time.

You know it happens after hours of usage so I can tell you in details once it happens agains

---

### Post by trendyabinash on 2008-12-19
it happened again now, my system just went out, I was not able to open system monitor also.

Ya but ctrl+alt+f1 is working

please help me, I was downloading open arena it was almost complete and now I have to download it again it is quite irritating.

---

### Post by SteveDee on 2008-12-19
> **trendyabinash said:**
> it happened again now, my system just went out, I was not able to open system monitor also.


Sorry I meant to say if you display monitors in a panel you should still be able to see them even if you cannot navigate your system. They may be frozen or still updating, but at least this provides more information for you.

---

### Post by trendyabinash on 2008-12-19
Should I reinstall my ubuntu???

I think that may resolve this issue

---

### Post by decoherence on 2008-12-19
you may want to keep syslog open while you are using it. in a terminal run

```
tail -f /var/log/syslog
```

and just leave it running -- it won't cause any problems. once you notice your computer behaving badly, check syslog and see if there are any clues. if you don't find anything obvious, copy/paste the output here.

---

### Post by trendyabinash on 2008-12-27
I did as you have said but I am not even able to open my firefox how can I paste it here.

I can create a file but it is not opening at all, so that I can paste the output.

This is very strange, I think ndisgtk is creating this issue. ANY IDEAS???

---

### Post by cariboo on 2008-12-28
It sounds like you are suffering from a memory leak, if you can get to a console, run top and see waht application is using all the ram. It may take a while, but try to kill the app that is causing the problem.

Jim

---

