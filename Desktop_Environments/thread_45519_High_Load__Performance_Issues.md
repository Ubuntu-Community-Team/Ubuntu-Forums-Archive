---
title: "High Load / Performance Issues"
date: 2005-06-30
forum: Desktop Environments
---

### Post by jeremy7733 on 2005-06-30
Hi, I'm running Hoary Hedgehog on a Dell Poweredge 420, 2.4 Ghz Celeron, with 256 MB Ram.  I sometimes see the system become very slow where I am waiting seconds for applications to respond to simple mouse clicks and commands.  If I check the system load using top, I see high load times sometimes over 10.

Obviously something goes a little haywire, but I'm not sure how to track down the high load causing application.  Any ideas?

If I start closing Firefox, Openoffice, etc. things seem to get better.  If I am impatient and start doing more, the system will crash hard.

Anyone seeing these behaviors?

Jeremy

---

### Post by Xian on 2005-06-30
[QUOTE=jeremy7733]Obviously something goes a little haywire, but I'm not sure how to track down the high load causing application.  Any ideas?[/QUOTE]
There are various ways to do this, but a simple one is to just open the System Monitor (Applications > System Tools > System Monitor) and use that to track your processes usage while you continue to work. When things noticeably slow down begin to scroll down the Process Names and see if you can isolate one (or more) that might be a runaway candidate.

---

### Post by crashtest on 2005-06-30
[QUOTE=Xian]There are various ways to do this, but a simple one is to just open the System Monitor (Applications > System Tools > System Monitor) and use that to track your processes usage while you continue to work. When things noticeably slow down begin to scroll down the Process Names and see if you can isolate one (or more) that might be a runaway candidate.[/QUOTE]

Good advice, and as a guess I'm going to bet it turns out to be Firefox.  I get this problem on my Mac as well, and assuming nothing out of the ordinary is going on, it always turns out to be the web browser that is driving the load up.

Not sure why this happens, but making another guess I imagine it has something to do with the design or content of certain web sites.  One example I ran into was a site that was spawning pop-ups just as fast as Firefox could block them.  I don't really understand what happens, and I'd be interested in hearing what others think, but I can say that 95% of the time I get a high load, closing Firefox or Safari will fix it.

---

