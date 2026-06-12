---
title: "CUPS routinely dies on some 9.10 desktops."
date: 2010-03-24
forum: Desktop Environments
---

### Post by Kyle_S on 2010-03-24
I'm using stock ubuntu 9.10 on 5 machines at work, as internet terminals.  They are all configured the same, are pretty locked down, and are updated regularly.  On two of them, CUPS has started on a regular basis.

If it matters, these machines all use one server for DNS, DHCP and printing via CUPS.

Any ideas what's going on?

--Kyle

---

### Post by jfparis on 2010-03-24
No idea what is going on but I have the same problem here.

Did not start investigating it in depth but I believe it is related to [https://bugs.launchpad.net/ubuntu/+bug/444597](https://bugs.launchpad.net/ubuntu/+bug/444597)

---

### Post by Kyle_S on 2010-03-25
> **jfparis said:**
> No idea what is going on but I have the same problem here.

Humm.  Do you get a segfault for cups in /var/log/messages?

For the meanwhile, I've got a script that runs in cron like this:

service cups status || service cups restart

A dirty little hack, but it seems to keep cups running.

---

