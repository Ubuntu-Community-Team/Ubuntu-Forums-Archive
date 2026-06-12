---
title: "dpkg - disk quota exceeded?"
date: 2009-05-12
forum: General Help
---

### Post by etali on 2009-05-12
Hi all,

I'm trying to install some stuff on my VPS, but I'm having trouble with disk quotas.  The error I'm getting is:


dpkg: failed to open `/var/lib/dpkg/status' for writing status information: Disk quota exceeded

I've got plenty of drive space free. 

I didn't set the VPS up, but if I type quota, I get told:

Disk quotas for user etali (uid 1000): none

What user does dpkg run under, usually?  Is there some way I can over-ride the quotas?

Thanks in advance.

---

