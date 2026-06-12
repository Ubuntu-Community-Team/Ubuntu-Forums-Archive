---
title: "GNOME desktop does not start (KDE and IceWm work fine)"
date: 2008-06-20
forum: Desktop Environments
---

### Post by ksamanta on 2008-06-20
Problem:

I was trying out wicd in KDE, but could not find it to be better than the network managers that I have in KDE (3.5.9) and GNOME. So I uninstalled wicd and during that I probably broke something which resulted in the following: (1) I cannot load GNOME any more, (2) In KDE I prefer to use a few GNOME packages (e.g. gnome-terminal instead of konsole), which hang in the beginning, take a long time to load (~half an hour!) and even after that they are unusable, (3) I had a perfectly working firefox 3.0 before, which shows similar behavior as gnome-terminal mentioned in (2). I tried running gnome-terminal and firefox from konsole command line, but they show the same behavior. 


System Info:

I am dual booting my Dell Inspiron 6000 (1.6 GHz Inetel Centrino, 2 GB RAM) with Ubuntu Hardy Heron and Windows XP. I use GNOME desktop manager (GDM). I mostly use KDE window manager although I also have GNOME and IceWm installed. I can load KDE and IceWm and work on them, but cannot use any GNOME package or firefox (opera, konqueror, epiphany work fine). 

Steps I took so far:
1) [http://ubuntuforums.org/showthread.php?t=487747](http://ubuntuforums.org/showthread.php?t=487747) -- it did not help.
2) Reinstalled GNOME window manager (```
sudo apt-get remove --purge gnome; sudo apt-get install gnome 
```). I had had some problems in that which I fixed using [http://ubuntuforums.org/showthread.php?t=830301](http://ubuntuforums.org/showthread.php?t=830301). That did not solve my orginial set of problems (1-3 above).

Could you help me fix those three problems? I'm new to this forum, so please let me know what other information I ought to furnish. Thanks!

-KS

---

### Post by ksamanta on 2008-06-21
Anybody out there ------- please, please help! 

Btw, after I messed up my system last night, it is running very very slow. So, if there is no other solution I'll have to reinstall ubuntu.

---

### Post by GrumpyBob on 2008-06-21
Have you tried removing the folders .gnome and .gnome2 from your home directory (e.g. by renaming them - they can then be reinstated by restoring the original name if this doesn't help), then trying to log in to a Gnome desktop?

Robert

---

### Post by ksamanta on 2008-06-21
> **GrumpyBob said:**
> Have you tried removing the folders .gnome and .gnome2 from your home directory (e.g. by renaming them - they can then be reinstated by restoring the original name if this doesn't help), then trying to log in to a Gnome desktop?

Robert


@Robert, 
Thanks for your reply. I had already tried what you mentioned, but that too did not help. Anyway, I reinstalled the system, and everything's back to normal. I generally don't miss this kind of opportunity to learn a few new things, but this time I was in a hurry to get back to work. Thanks again.

---

### Post by xtrmplayr on 2009-01-06
try running nautilus from command line.

---

### Post by ksamanta on 2009-01-06
> **xtrmplayr said:**
> try running nautilus from command line.

Well, I tried most of the GNOME packages (including nautilus) from a CLI (the only way I could get onto the command line was using Konsole while running KDE window manager 3.5.9. But, as I mentioned a fresh install solved everything. It's still a mystery to me, but I'm guessing, as somebody already pointed out, I probably had broken something in .gnome or .gnome2. 
Thanks for your reply!

---

