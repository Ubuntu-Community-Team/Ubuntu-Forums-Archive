---
title: "How to use /etc/profile ?"
date: 2005-02-08
forum: Desktop Environments
---

### Post by Harderlump on 2005-02-08
I've had trouble installing QNX Momentics (a development environment from QNX Software Systems Ltd.) on Warty. The installation worked fine, but it couldn't start out
of the box, because there were some environment variables missing.

I found out that the required settings have been put into /etc/profile, but /etc/profile was never executed.

I wonder, if that was intended or not?

To fix that problem for me, I've added ". /etc/profile" to .bashrc and .gnomerc.

But is that the way it should work?
Why was /etc/profile not included by default?

The guys from QNX rely on /etc/profile. They test it on RedHat, so it works there.

---

