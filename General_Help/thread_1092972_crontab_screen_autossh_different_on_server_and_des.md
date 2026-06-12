---
title: "crontab screen autossh different on server and desktop"
date: 2009-03-11
forum: General Help
---

### Post by mad4cron on 2009-03-11
I'm trying to use crontab to run autossh in a detached screen session to login to machine C.  I've created ssh keys (no passwd) on machines A and B.

Machine A: Ubuntu 8.04.2 Desktop i386
Machine B: Ubuntu 8.04.2 Server i386
Machine C: Linux box

I tested the keys by SSHing from A and B to C and they both work no prob.  I run the following via crontab for my non-root user accounts on A and B, and it works perfectly on B (server), but not on A (desktop), and logs have proven to be no help.

@reboot /usr/bin/screen -fa -d -m -S testscreen /usr/bin/autossh -M 0 -p 2222 username@192.168.1.1

If I run just the detached screen on desktop it works fine, but if I add the autossh command, it won't work.  The screen is not even there if I run screen -ls.

Any ideas?

---

### Post by mad4cron on 2009-03-16
For anyone who may run into the same:

Networking is apparently slower to setup on desktop than server.  Ifconfig showed no IP address (DHCP) set before the autossh command.  Setting the environment variable AUTOSSH_GATETIME=0 in the crontab solved the problem.  Thanks maxb!

---

