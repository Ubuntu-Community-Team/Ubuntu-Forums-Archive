---
title: "Occasionally, Nautilus is Launched upon system startup.  How is that prevented?"
date: 2013-04-09
forum: Desktop Environments
---

### Post by GregA on 2013-04-09
Good Day,

I run Kubuntu 12.4.2 with no complaints or issues.  The system has been exceptionally stable for months at a time, but, on rare occasion, Nautilus is launched upon system startup.   How do I prevent that?  I much prefer the dolphin file manager for general use (particularly for its 2 pane display).

Thanks for your help.

Greg
Omaha, NE
US

---

### Post by tartalo on 2013-04-09
Go to System Settings > Startup/Shutdown to see if there's something there that would explain why Nautilus starts.

If in "Session Management" you have "Restore previous session" (which is default in KDE) instead of "Start with an empty session" (which is what most users expect), what could be happening is that something is opening Nautilus during your daily work and then it gets reopened after restart, much to your surprise.

Also, if you prefer Dolphin, why not remove Nautilus from the system? Do you need it?

---

### Post by GregA on 2013-04-10
Thanks Tartalo,

Regarding Nautilus - I don't need it so I can uninstall it, but I suspect it was installed as part of another package install (a dependency I guess).   

Here's a snapshot of my startup settings:

[[IMG]http://img844.imageshack.us/img844/94/gnomenautilusautostart.jpg[/IMG]](http://imageshack.us/photo/my-images/844/gnomenautilusautostart.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

So, I'm thinking it would be simplest to disable retention of the previous desktop . . . that way I won't break something else that I installed (like Gramps for example).

Again, thanks for the tips!:D

---

