---
title: "Resuming from standby freezes X applications..."
date: 2009-03-03
forum: General Help
---

### Post by sofakng on 2009-03-03
I'm running Ubuntu v8.10 (minimum) mainly for XBMC (media center application for X) and I'm having a problem:

When I resume from standby, my applications in X freeze after a second or two of usage and then their CPU usage slowly increases to 100%.

I've tried "killall -SEGV <app>" but it doesn't kill the process.  However, "kill -9 <pid>" works.

My motherboard is a GIGABYTE GA-E7AUM-DS2H and I also had trouble with my network going down after resuming from standby but I fixed that by adding SUSPEND_MODULES="forcedeth" to my /etc/pm/config.d/local file.

Can anybody please help me out or help me figure out how to debug this?

It seems like my problems are all being caused from resuming from standby... (S3)

---

### Post by sofakng on 2009-03-04
Anybody?

---

