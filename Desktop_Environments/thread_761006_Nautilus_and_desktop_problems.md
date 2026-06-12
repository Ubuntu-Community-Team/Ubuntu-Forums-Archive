---
title: "Nautilus and desktop problems"
date: 2008-04-20
forum: Desktop Environments
---

### Post by GB2732 on 2008-04-20
First of all, I've done a ton of searching on Google and in this forum, and can't find a solution. I'm hoping someone can offer some insight to my problem.

Yesterday while using Nautilus, it crashed for no apparent reason. I hadn't installed or removed anything except for an apt-get update. I rebooted the machine and logged back into Gnome as normal, but there were no desktop icons or desktop files and the right mouse click didn't work. Nautilus would open, but when I attempted to open a certain desktop folder from within Nautilus, it would crash. With a little experimentation, I noticed that I could open that folder as root, and Nautilus wouldn't crash. So I deleted its contents (some mp4 files) and it fixed the crashing.

So that's where I am at this point. Nautilus doesn't crash any more, but I still can't get my desktop icons or files to show up. When I go to ~Desktop, everything is there.

I've tried all solutions I can find including reinstalling Nautilus, reconfiguring Nautilus, and a ton more, but nothing works.

The desktop loads properly when I log into Failsafe mode.

I'm using Ubuntu 7.10

Help would be appreciated.

---

### Post by GB2732 on 2008-04-20
OK, I just opened Nautilus in terminal and all icons and folders returned. When I shut down terminal I got this 

[SIZE="3"]Nautilus can't be used now, due to an unexpected error.[/SIZE] [SIZE="2"]Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem[/SIZE].

Still looking and needing help. :confused:

---

