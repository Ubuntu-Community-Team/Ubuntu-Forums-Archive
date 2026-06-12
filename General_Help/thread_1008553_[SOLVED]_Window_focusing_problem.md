---
title: "[SOLVED] Window focusing problem"
date: 2008-12-11
forum: General Help
---

### Post by hugo.riley on 2008-12-11
Hi, 
recently I have some weird problem with window focusing. 

When I first login into session, I can't focus windows by clicking on it's content. I can select text or get context menus for items in this window but it never get into focus. I can't write into it. Only way to get such windows into focus is with alt-tabing to them.

Now, it's problematic behavior but what's weird is when I logout and login again, everything is working normal. So, after powering on the PC, first user who logs in has this problem. After logout and sequential logins, problem disappears. 

I was trying whole day to isolate the problem but I'm still not sure where is the problem. What I know now is this:
[LIST]
[*]Problem is not in user configurations, every user has this problem if he logs in first
[*]Failsafe Gnome session didn't help
[*]I installed fluxbox and it had the same problem
[*]I compared running processes from session that work ok and problematic one: no difference
[*]I deactivated ATI drivers just to eliminate the possibility, but to no avail
[/LIST]

And so I'm stuck now. Current solution is to logout and login again if I want to work. Other is to do fresh install but to configure everything again is weekend long job. And there's also my curiosity: I really want to know what went wrong here. So, please, do anybody know what can I do about it?


Ubuntu 8.10 with latest updates
Gnome with Compiz  (tried also with Fluxbox)

Regards,
Hugo

---

### Post by hugo.riley on 2008-12-12
Well, I solved the problem.

I've inserted the Live Ubuntu CD, just to see how it should behave originally and, lo and behold, problem was still there. I tried it on another computer and it was OK there so I was sure the problem is in my hardware. I've plugged in PS2 mouse instead of USB and got it working. When I returned USB mouse the problem was there again. So it's the mouse problem. And finally, I plugged out an USB cable, adapter to my cellphone (which wasn't plugged in) and then it worked with my USB mouse. Just to try my luck, I've plugged everything in as was before and now everything works.

So, messing with USB cables helped. I'm not sure what really happened under the hood but if somebody has this problem, try that way.

---

