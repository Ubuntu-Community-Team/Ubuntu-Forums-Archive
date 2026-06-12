---
title: "How do I configure VTs in Lucid?"
date: 2010-07-11
forum: Desktop Environments
---

### Post by x1a4 on 2010-07-11
Hi,

I recently "upgraded" Xubuntu from Hardy to Lucid (clean install) and find myself unable to configure it the way I need to.  The biggest thing so far is that I'm unable to setup VTs the way I like.  

How do I configure my system to be as follows?

VT 1 - 4: Consoles
VT 5 - 7: X sessions
VT 8 & 9: Free
VT 10 : User logs
VT 11 : Daemon logs
VT 12 : Kernel logs 

At the very least I need to have three static instances of GDM at startup. 

Hardy and earlier I did this by deleting tty[56] from /etc/event.d/ (this directory is now gone).  Configuring /etc/gdm/gdm.conf-custom (now replaced with custom.conf) but now my changes don't do anything. Configuring /etc/syslog.conf which is now gone and creating it didn't help.  

Any ideas?  Thank you.

---

