---
title: "trigger script at logoff"
date: 2008-08-27
forum: Desktop Environments
---

### Post by neill on 2008-08-27
hi

i have a small back up script that syncs some local folders with others mounted in /media that are actually on a LAN samba server

i want the script to run automagically every time i logoff or shutdown

how might i approach that ?

thanks

/neill

---

### Post by mtbsoft on 2008-08-28
I don't know for sure but I suspect that you might have issues with ensuring the task is complete befor the session terminates is you latch onto the logout/shutdown events.  

Might not a better way be simply to have two scripts each doing the sync but one issuing a logoff and one issuing a shutdown instruction at the end, then use these to perform those actions.

Just a lateral thought.

---

