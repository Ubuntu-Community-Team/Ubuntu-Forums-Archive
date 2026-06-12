---
title: "Suspend failure, Apport doesn't work"
date: 2009-04-30
forum: General Help
---

### Post by dsokus on 2009-04-30
Hi, 

My Toshiba M400 has serious suspend/resume issues (WARNING: RESUME FAILURE. PRESS ANY KEY TO CONTINUE) and I'm having a really hard time pinning down what causes it (doesn't seem consistent; sometimes happens, sometimes doesn't). 

I have attempted to run the checkbox suspend/resume test, which fails every time (but again in an inconsistent way; never resumes from suspend on its own: 
- sometimes I can get it to resume (this has only ever happened if I opened the lid, but doesn't happen *every time* I open the lid) -- I haven't had the chance to check every single thing, but essential functions (keyboard, touchpad, wifi) appear to work OK 
- sometimes I get RESUME FAILURE and need to restart (this usually happens if I use the power button, but sometimes also when I open the lid)
- sometimes it appears to resume but my keyboard/touchpad are frozen (this was when the automatic script made it to the 20-min test (from which it woke up 5 minutes later), and I needed to use the power button to shut down the machine).
- it never resumed automatically from the script, except once after what was supposed to be the 20-min test (which turned out 5 minutes instead and froze my keyboard/touchpad) 

Apport never generates a bug report. 

I don't know how to use the in-built "Report bug" function of the Help menus or the command line to report a suspend problem...

I have added a line to [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback)  -- is this what I'm supposed to be doing, and is there anything else I should do to report this bug in a useful way? The problem has been present since Feisty (regression from Edgy) and it's an extremely unpleasant limitation because I'd need to suspend my laptop a lot. So it would be very good if I could help fix it asap.   

Thanks!

---

