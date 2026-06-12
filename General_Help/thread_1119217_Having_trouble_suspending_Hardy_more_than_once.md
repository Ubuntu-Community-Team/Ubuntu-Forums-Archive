---
title: "Having trouble suspending Hardy more than once"
date: 2009-04-07
forum: General Help
---

### Post by sushman007 on 2009-04-07
I've seen lots of posts but hardly any concrete answers for this; I can only suspend and resume successfully once without rebooting.  When I try to suspend a second time, my screen goes completely black (no blinking cursor), but the system doesn't actually turn off.

There is no way to resume from this state and I'm stuck having to do a hard reset on my computer.

I've checked my kernel log for any hints but really have no clue what to look for.  As far as I can tell, a bad suspend writes the same output as a 
good suspend.

I'm looking for some tips on how to troubleshoot suspend problems, i.e. where to look, what to look for, etc.

---

### Post by 3Miro on 2009-04-07
Try closing all programs before suspending. It may be the case that some program refuses to suspend.

It is possible that a process refuses to suspend, that would be harder to catch. 

You can also try to manually disconnect from the network.

---

### Post by sushman007 on 2009-04-07
> **3Miro said:**
> Try closing all programs before suspending. It may be the case that some program refuses to suspend.

It is possible that a process refuses to suspend, that would be harder to catch. 

You can also try to manually disconnect from the network.

I've tried both closing all programs and disconnecting from the network; still no luck.

Any other suggestions?

---

### Post by sushman007 on 2009-04-11
Update for those interested:

Hibernate doesn't even work once--suspend still works fine the first time though.

I've seen lots of threads for people with laptops; this is a desktop that I'm having trouble with.  Would this more likely be a hardware or a software issue?

---

