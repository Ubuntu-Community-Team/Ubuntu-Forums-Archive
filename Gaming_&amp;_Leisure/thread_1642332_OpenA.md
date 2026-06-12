---
title: "OpenA"
date: 2010-12-10
forum: Gaming &amp; Leisure
---

### Post by Zero2Nine on 2010-12-10
Have used the search first before creating this thread but haven't come across the same problem. 

Problem description:
_Sometimes_ OpenArena is just very slow (stuttering). Normally it runs without any trouble (starts up fast, runs smooth) but just sometimes after the use of some other applications (never happened right after rebooting Ubuntu) it doesn't. It happened only twice and in both cases after a reboot the problem was gone, so it's nothing permanent. This makes me think it has something to do with one of the processes/applications eating resources OpenArena needs, maybe some application's process was not really terminated.

I'm not sure exactly which ones were running (or I already ended) when OpenArena became slow but most likely FireFox and Exaile as I constantly use those two. I've only installed applications from the Software Center so far (fresh install, only a few weeks). Just mentioned that to stress I did no dangerous stuff with Ubtuntu yet to mess up the system ;)

Finally the 'problem' is I'm not able to reproduce the situation. Just started OpenArena, played, closed it, started it again later and nothing was wrong. But when it does happen it is quite annoying. So that's why I'm opening a thread here.

Ubuntu version I use is Maverick Meerkat 32-bit.
Graphics card is a Nvidia Geforce 9600 GT (with the Nvidia driver installed).

My questions: 
1. Is this a known problem, anyone here noticed something similar?
2. If it happens again, what's the best way of finding out what exactly is causing this behaviour?

Thanks in advance.

edit: Title is not finished, should be: OpenArena sometimes slow

---

### Post by rizzeh on 2010-12-10
Could be many reasons: audio applications messing with pulse audio, compiz-like window managers clashing with OpenGL, flash plugin, various launchers/docks like cairo can affect game rendering. 
Try to re-log in to your desktop to restart X server before playing the game.

---

