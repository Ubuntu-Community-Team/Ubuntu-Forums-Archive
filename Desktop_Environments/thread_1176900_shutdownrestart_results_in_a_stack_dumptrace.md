---
title: "shutdown/restart results in a stack dump/trace"
date: 2009-06-02
forum: Desktop Environments
---

### Post by FMBBowen on 2009-06-02
New to ubuntu, noviceish with linux.

My system does a stack dump/trace whenever I do a shutdown/restart, either from the UI or by typing in an init command.  Running desktop 9.04 with a bunch of server stuff installed.

How do I troubleshoot and resolve this?

Thanks!

---

### Post by FMBBowen on 2009-06-09
Alright, a few brain cells must have worked because I finally had the bright idea to run the scripts in /etc/rc0.d in order manually.

gdm shut down OK
usplash results in a stack trace!  ARGH!  Are you kidding me?  The frigging splash screen is crashing on shutdown?  I hate it when unnecessary software crashes.  So ...

sudo apt-get remove usplash

---

