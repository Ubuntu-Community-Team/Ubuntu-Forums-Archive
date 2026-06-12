---
title: "I broke gnome-terminal -- no more wall messages"
date: 2012-08-16
forum: Desktop Environments
---

### Post by newbie001 on 2012-08-16
Background: I recently messed up some ownership & permissions under /usr.  I fixed most of it by comparing with another system.  BUt some problems remain.

If I do a 

echo "test" | wall 

the test message does NOT appear on any gnome-terminal.  

The test message DOES appear on all xterms and "real" ttys (tested by switching out of X and logging into the console).  

I checked: all terminals (gnome, x, console) report mesg is y.

I have reinstalled gnome-terminal and bsdutils.  No change.

The fact that xterm gets the messages tells me that the problem is not affecting the entire X session, but I'm not sure what to do next.

Any help appreciated!

---

