---
title: "AWN &amp; Gnome session order"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by stek79 on 2008-04-12
Hi, 
     I used AWN with great pleasure since a some days ago.

Too bad I'm noticing some weird issues: when I log into my system, some times I find no AWN bar. 

After a bit of analysis, I've found that the avant-window-navigator process is active (I have it in my startup sessions) but apparently it gets started before compiz is ready.

In fact, in my .xsession-errors I find the entry in which AWN say that no composite WM is active. 

It is strange, since in my session I have compiz with order 10, AWN with order 50. I solved the issue putting a sleep before AWN startup, but I would like to make a better solution.

I've tried to change the AWN order, for example setting 60, but it seems that config parameter it doens't get saved: after a logout-login, I find it again at 50...

Any ideas?

Thanks

---

### Post by moonbeam on 2008-04-12
> **stek79 said:**
> 

It is strange, since in my session I have compiz with order 10, AWN with order 50. I solved the issue putting a sleep before AWN startup, but I would like to make a better solution.



Honestly, sleep is probably the best solution at the moment.  It's a known issue that there can be some strangeness with awn in this situation and  the sleep solution is the normal recommendation.

---

