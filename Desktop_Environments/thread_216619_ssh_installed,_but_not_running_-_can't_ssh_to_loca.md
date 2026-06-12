---
title: "ssh installed, but not running - can't ssh to localhost"
date: 2006-07-15
forum: Desktop Environments
---

### Post by hotani on 2006-07-15
When I've installed ssh in the past it starts up and begins accepting connections. This time it seems to not be doing that.

If I try to start it manually it says "sshd re-exec requires execution with an absolute path"

How to get it up and running (and stay that way)?

---

### Post by hotani on 2006-07-15
well, never mind! looks like it is working now. I went into synaptic, uninstalled and reinstalled the packages for open-ssh and ssh, now it is up and running.

---

### Post by vigleik on 2006-07-15
In case you ever need to manually start your ssh server again, you have to type "/usr/sbin/sshd" instead of just "sshd". They changed it a few months (or is it a year?) ago and I was very confused for a little while because my startup script didn't start sshd anymore. I still don't know why, though I guess it's a security thing.

Vigleik

---

