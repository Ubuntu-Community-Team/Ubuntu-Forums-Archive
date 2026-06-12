---
title: "Idle apps disappear"
date: 2011-06-05
forum: Desktop Environments
---

### Post by JHBrewer on 2011-06-05
Whenever I leave my desktop unattended long enough for the display to go to sleep, when I come back all the apps (Terminals, seamonkey, ...) have disappeared.  They are really gone, as confirmed by *ps aux*, without a trace.   I assumed that this is a new configuration default, so I've searched through *System Settings* and *ccsm* and these Forums and Google for a full day, but I have found no mention of this.  Any advice will be appreciated.  I can't use my computer until this is fixed.

---

### Post by Copper Bezel on 2011-06-05
No, that's not a normal behavior in any way. Does it happen if you put the computer to sleep manually (as opposed to waiting for the timeout?)

---

### Post by JHBrewer on 2011-06-06
Hmmm...  Both "Suspend" and "Hibernate" cause the system to power down, but after Suspend it comes back to life quickly when I hit the power button; after Hibernate it reboots on power-up.  In either case, the window I opened beforehand does reappear.  But not when it times out.  Moreover, if I Log Out and log in again, it remembers nothing about my previous session.  I presume this is a configuration option, but I'd prefer to have it reestablish my session as nearly as possible, like it did before I "upgraded" to 11.04 -- I've again searched for some hint of how to change that option, to no avail.  

In desperation, I installed KDE; it does **not** kill my windows when it goes to sleep.  There are reasons why I abandoned KDE in favor of Gnome, but now it's looking like I'll be driven back to it as the lesser of two evils.  

PS: I already have a Mac; I like it fine, but I don't want my Linux desktop to pretend to be a Mac.  Whose idea was this?

---

### Post by JHBrewer on 2011-06-06
Hold on... this morning it wakes up with my apps still there.   ???   I tested this many times before; the only change is that I installed and tried out the KDE interface, then went back to the Gnome... er, Unity... or is it Compiz... anyway, it seems to have stopped closing my apps.  I'll let you know if it starts doing it again, but for now you can consider the problem "solved" *for me* -- as long as Windows-like inconsistent behavior doesn't bother you....

---

### Post by Copper Bezel on 2011-06-06
We're not devs, so it doesn't much matter if we're bothered. If the problem reoccurs, I'd suggest filing a bug with them.

As for the terminology, Unity is a shell for Gnome, so you could actually correctly call it the Unity, Ubuntu Desktop, or Gnome / Unity session. If you dislike the Unity interface, of course, you can always use Gnome Classic (and although this will be removed in 11.10, the upstream equivalent written for GTK3 will be available in the repositories.)

---

