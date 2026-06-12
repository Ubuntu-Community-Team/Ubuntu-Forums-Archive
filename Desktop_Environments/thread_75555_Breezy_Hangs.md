---
title: "Breezy Hangs"
date: 2005-10-13
forum: Desktop Environments
---

### Post by fortytwo on 2005-10-13
Hey guys,
I've been using Breezy since the preview release, and have continued to have the same problm:  after some amount of time, Ubuntu will lag terribly.  Just today I was on the desktop, hadn't been booted for too long, and all of a sudden my music stops and I look up to see my clock updating the seconds about every 15 seconds or so.  I try to run top but it lags and takes forever.  I try going into console mode with ctrl-alt-f1 but even that is lagged too.

I've got an nvidia 5200fx but I've installed nvidia-glx for it and did the enable command.  It's a 2.2 Ghz machine with a gig of ram, does anyone have any ideas?  I really want to keep running Linux full time, but if this keeps happening I'm going to have to put Windows back on...

Thanks for the help.

---

### Post by Emerzen on 2005-10-13
Have you checked your RAM usage?  It's possible that you have a program installed that has a "memory leak."  I know an older version of Azureus had this problem, but there have been others as well.  Keep an eye on your RAM and see if it continually increases.

---

### Post by gw90se on 2005-10-13
Sometimes I go off on tangents, so excuse me if this seems like one, but can you monitor your systems temperature? You might have a hardware problem developing.

---

### Post by fortytwo on 2005-10-13
I don't believe it's a memory problem, I have a monitor running at all times and it's never anywhere near full.  

I don't currently monitor the system temperature, but for what it's worth, I had the same setup I have now running on Windows XP without any problems.

---

### Post by gw90se on 2005-10-14
You are probably right. It is just that over the years while doing repair on equipment, it has amazed me how many times I have had other unrelated systems fail while working on a different part of the system. 

That being said, I would also look into something running in the backgroud that is leaking memory.

---

### Post by fortytwo on 2005-10-17
OK, I beleive I've fixed the problem.  I disabled apic by adding 'noapic' and 'nolapic' to my kernel boot line, and it appears to have fixed it...up for 4 days so far and no hangs.  Hopefully this will help someone.

---

