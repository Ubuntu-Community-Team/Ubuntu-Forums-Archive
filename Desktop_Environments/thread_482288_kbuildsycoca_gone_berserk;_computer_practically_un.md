---
title: "kbuildsycoca gone berserk; computer practically unusable"
date: 2007-06-23
forum: Desktop Environments
---

### Post by DigitalAxis on 2007-06-23
As of last night, my computer will no longer log into Kubuntu properly.  It takes forever, things crash, things aren't currently working.
The symptom, as far as I have determined, is that kbuildsycoca is taking up all my CPU time and all my memory to repeatedly (I just counted four before drkonqi told me it died) generate 450 MB files in /var/tmp/kdecache-adric/

That's all it seems to be doing, and it restarts itself frequently.  Fortunately, when one of them finishes it replaces the other, but this doesn't always seem to be the case.

It's just generating 450 Megabyte files over and over and over, and causing my login to KDE to take something like 30 minutes.


Brief story of how I got this far, in case I've missed the REAL cause...
For some time now, I've experienced random freezing- Mouse pointer stops moving, clock freezes, computer is entirely unresponsive and is just suddenly sitting there.
Two days ago, my computer suddenly got sluggish and then X crashed.  I rebooted, things worked.
Last night, my computer suddenly got sluggish and then X crashed.  When I rebooted, KDE stopped loading on the 'setting up communication" because of something about DCOPserver.
I eventually fixed THAT by removing the .DCOPserver* files and the .ICEauthority file, which it couldn't lock.
Back in an apparently working KDE session, I watched the KDE loading processes, and discovered kbuildsycoca was taking up extremely large amounts of CPU time.  My computer got sluggish and then X crashed.
Thanks to the forum I found some sort of issue with my hard drive being full.  I checked anyway, even though I'm quite sure I would have noticed it before, and found that my root partition WAS suddenly 100% full.  I cleaned out my /var/apt/archives, uninstalled and reinstalled all of Kubuntu-desktop, loaded filelight and found the 450 megabyte file issue.

Since then my problems have been various things like; the bash shell where I killed kbuildsycoca takes 100% CPU and is frozen, init itself starts taking 99.9% of all CPU time, and parts of KDE can't talk to each other (apparently I DIDN'T fix the DCOPserver problem; I just fixed it enough to allow me to log in to a barely-functional KDE system (such as right now, I had to start firefox through a terminal with DISPLAY=:0 firefox because I can't apparently launch anything by clicking on it)

So, does anyone have any ideas what's going on?  My next thought is to delete ALL the multimegabyte configuration files and hope kbuildsycoca can generate a good new one on its own.
My next thought is to burn a Kubuntu 7.04 CD (I think I might have done that already) and reinstall.  I have, as I mentioned, separate partitions for various things: /boot, windows, /, /home, and /tmp, so I'm theoretically not in danger of losing any of my personal data when I reinstall.

On the other hand, if it's a configuration file under /home I need to fix, reinstalling might not stop this mess.

It's probably worth noting that when I run kbuildsycoca manually, it complains about unknown symbols or something, and then throws a few more errors, and quits- but only if I run it from a virtual terminal; if I run it from a Konsole session in KDE, the system gets sluggish and X crashes.

---

### Post by Sonofmoog on 2007-06-23
> On the other hand, if it's a configuration file under /home I need to fix, reinstalling might not stop this mess.

Try logging in as a different user.  Create one, if you have to.  If KDE still balks, you have a more serious problem.  If it loads normally, you've isolated the cause of the problem to something in $HOME ..

---

### Post by DigitalAxis on 2007-06-23
D'oh!

Well, I finally jogged my memory and figured out how... and yes, it's something wrong with my personal configuration settings.

Everything is working fine on this second account, and the kbuildsycoca file for this account is 1.2 megabytes, not 450 megabytes.

I guess now I get to remove and then recreate my KDE desktop settings.  I'm off to delete /home/adric/.kde (AND the kbuildsycoca files)

---

### Post by DigitalAxis on 2007-06-23
It worked, I'm back.  Something in either /var/tmp/kdecache-adric or /home/adric/.kde caused the problem.

---

