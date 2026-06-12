---
title: "KDE suddenly slow?"
date: 2008-01-10
forum: Desktop Environments
---

### Post by Berethorn on 2008-01-10
Hi,

If this has been addressed, excuse me; I've searched and found solutions for most things, but not this.

I've had Gnome and KDE (Ubuntu 7.10, then installed KDE) going for a few days now. Everything was going great until a couple days ago when KDE suddenly became slow. Really really slow: when you type a phrase, it takes a minute for all the letters to appear. I can't figure out why, and it's hard to look around in KDE when it crawls. I don't know what could have done this, but it must have been something I did in Gnome. Trouble is, I'd done so much in Gnome it's hard to troubleshoot; so I thought I'd ask if anyone knows of a likely reason KDE would be fine, then go suddenly lethargic.

I've tried uninstalling and reinstalling KDE; no luck.

Any ideas? Thanks. :guitar:

---

### Post by marmaladeskies on 2008-01-11
i don't remember what the "task manager" or "system monitor" in kde is, but if you have gnome, try running "gnome-system-monitor" (while you're in kde) (you can get it in apps-settings i think).  or you can open up a terminal and type "top".  look there to see if some process is taking a buttload of memory.  post the output here so that someone smarter than i am can tell you what's going on and whether it's safe to kill the process.

---

### Post by Berethorn on 2008-01-12
Thanks for the suggestion; I ran gnome-system-monitor, and wow! 'kdesktop [kdeinit]' was taking up a whopping 4GB of space.

Hopefully that's the problem, but I don't know where to proceed from here..

EDIT: I just noticed in the system monitor that Synaptic (in Gnome now) is using 4.0gb memory. But Gnome is not slow at all. Moreover, the resources tap doesn't show any abnormal memory usage. Is this normal then? 4gb is about the total memory I have if you include the swap.

---

