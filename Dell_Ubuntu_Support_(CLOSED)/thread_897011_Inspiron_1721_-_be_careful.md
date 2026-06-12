---
title: "Inspiron 1721 - be careful"
date: 2008-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by asungtang on 2008-08-21
I spent about 2 weeks duration (maybe around 30 man hours total) trying to get Hardy Heron to the host OS, and use as Vista guest OS on VMWare. I discovered the following:

Dell's MediaDirect is actually it's own OS, but it is somehow interdependent on Vista. So if you install HH as the main OS and accidentally push that little button on the top of the keyboard (the one with the picture of a little house), it will blow away HH. There is absolutely no way whatsoever to disable that little button.

I actually managed to successfully install HH as the main OS, install VMWare 2.0 with Vista as guest OS and using FireFox 3.0 (there were alot of problems with higher versions of FF).

When I discovered the problem with MediaDirect button I decided to go with dual boot. I started the execution of that decision with the most rational step I could think of: format the entire drive and start from scratch with Vista as the main OS. Bad idea.

I couldn't install Vista after I did that. I called Dell for support to try to get Vista installed. The guy was giving me line commands in Assembly. When you start typing in things like MOV you know you're in trouble.

They sent me a new harddrive. So now, I will use the hard drive in bay 1 for Vista and I will buy a new hard drive for HH on bay 2.

---

