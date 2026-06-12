---
title: "KDE 4.2 initial resolution"
date: 2009-03-20
forum: Desktop Environments
---

### Post by Grobbendonk on 2009-03-20
Apologies if this has turned up somewhere else, but I can't see anything quite the same.  

I had a machine running Kubuntu 8.10 and KDE 4.1 absolutely fine.  Some of the bugs in KDE 4.1 were starting to really annoy me, so I updated it to KDE 4.2 (add repository via Adept and let it upgrade)

Now, when I boot the machine, it pops up a box complaining about running in "lo res" mode, and being unable to find keyboard and mouse settings.

If I try to continue from the error box, the machine asks if I want to look at the logs, edit the config or resort to failsafe.  None of these actually do anything, the screen blanks and then returns to the question.

Dropping to a terminal session lets me see that there are no errors (that I can find) in the logs, the xorg.conf file is untouched, or even if I regenerate it, it remains the same.

I've seen loads of posts about drivers here, but that is not the problem, because...

Ctrl-alt-backspace on the SECOND warning box (where it asks me about looking at logs/settings and does nothing) drops me to a shell prompt.  Running startx starts up a perfectly good X session with KDE 4.2, with the correct resolution and all X functions working (keyboard, mouse etc), just as it was under 4.1.  Only thing missing is the shutdown/logout stuff, which is expected as I'm running X on top of a shell.

Ctrl-alt-backspace on the FIRST warning box (lo-res warning) kills the session, and restarts GDM as a fully functional X system.

So, my question is, how do I get rid of the inaccurate "lo res" box permanently?  I don't want to be ctrl-alt-<- on every boot.

---

