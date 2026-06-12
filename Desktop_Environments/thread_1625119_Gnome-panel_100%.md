---
title: "Gnome-panel 100%"
date: 2010-11-18
forum: Desktop Environments
---

### Post by IanWood on 2010-11-18
Hi all,

Hope you can help.

I am using 9.10 64Bit with 4CPUS, 8Gig of ram and a Matrox M9120 PCIe x16 card driving 3 screens with the latest Matrox driver.

About once a week of so my system freezes - the mouse pointer still moves but the clock doesn't tick on and nothing responds. 

I can however ssh on to it. When I do a top Xorg is at the top. If I am able to ssh -X and run gnome-system-monitor I see that gnome-panel is using the most CPU and a whole core is maxed out.

It seems to happen when I start a certain Java application, but as I am a Java developer this may be a coincidence. 

What can I do to fix this? Would this problem be in 10.04 too?

Thanks in advance,

Ian

---

### Post by IanWood on 2010-11-19
Further to this.

Having killed gnome-panel in the process monitor I was able to use the computer again.

Also during the day I noticed that the "desktop" stopped working, i.e. no icons and I couldn't change the background picture. After killing the gnome-panel the background picture changed to the one I had tried to change to before.

Any ideas?

Ian

---

### Post by tom4everitt on 2010-11-19
Hi, I'm running 10.04 and encounter the same problem every once in a while as well. I don't think it is correlated to any java app though, it seems more random then that. Thanks for the tip of killing the gnome-panel, I will try that next time it happens!

---

### Post by IanWood on 2010-11-21
Hi Tom,

Thanks for your replay and sorry to hear you have the same problem every now and then.

I did some Googleing and saw people having similar problems a while ago and it seemed to be related to how many things where open at a time. 

I am using 10.04 32bit at home and never have this problem, well not that I can remember any way.

Are you using 32 or 64 bit and which card and how many screens?

Ian

---

### Post by tom4everitt on 2010-11-21
It's a 32-bit Ubuntu 10.04, on a MacbookPro1,1. 

CPU: Intel core duo, 2.0 Ghz
Graphics: ATI Radeon Mobility X1600
Display: just the standard one. 

When thinking about it, I think for me the problem has been mostly related to when I've been doing a lot of suspend/resume. So I guess that's slightly different than what you describe. (Un)fortunately it hasn't happened the last few days, so I haven't been able to check the gnome-panel thing.

---

### Post by IanWood on 2010-11-22
Thanks for getting back - 

I never do suspend/resume...

It happened again this morning, just after I changed from one workspace to another. I was able to ssh on from a colleague's pc to &#8220;pkill -9 gnome-panel&#8221; and continue working. 

I can't find anything in any logs to indicate why this is happening, anyone know where to look?

---

### Post by IanWood on 2011-01-03
While not a fix I have found a way to recover.

I log into my machine again by using ctrl-alt-F1 (up to F6 works) and log in again. I then "pkill gnome-panel" and use ctrl-alt-F7 to get back to the normal screen.

This is pretty quick and saves me from having to ssh into the machine from another one. 

Still don't know why it does this but at least I can recover now.

---

