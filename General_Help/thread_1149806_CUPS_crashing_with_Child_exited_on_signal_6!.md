---
title: "CUPS crashing with Child exited on signal 6!"
date: 2009-05-05
forum: General Help
---

### Post by utkjamie on 2009-05-05
Sometime in the last week CUPS has stopped working for me. Trying to start CUPS from /etc/init.d/cups results in:

```
cupsd: Child exited on signal 6!

```Running sudo tail -f /var/log/messages gives me:

```

operation="sysctl" requested_mask="r::" denied_mask="r::" 
fsuid=0 name="/proc/sys/crypto/fips_enabled" pid=17818 
profile="/usr/sbin/cupsd"

```

I need to print some documents for work, so need a quick fix for this.

---

### Post by utkjamie on 2009-05-05
Found a fix at [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898).

It turns out an incompatible version of libgcrypt11 was installed. From Synaptic I forced a lower version and everything works now. See the above link for details.

Now the question is: how did an incompatible version of libgcrypt11 get on my computer. According to the bug report this version was in the alpha version but that doesn't explain how I would have picked it up since I started using Jaunty when it was as Release Candidate.

---

