---
title: "Is Multi user possible with xgl/compiz?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by nicky.7 on 2006-07-11
Is possible to use a user account with xgl and compiz, do a quick switch to another user and use compiz too?
Thanks

---

### Post by JoWilly on 2006-07-11
> **nicky.7 said:**
> Is possible to use a user account with xgl and compiz, do a quick switch to another user and use compiz too?
Thanks

I have not tried this, but it theorically should be possible.

In /etc/gdm/gdm.conf-custom you define XGL to start on screen 0 (or 1 if you are using ati). For example, adding screen 0, 1 and 2 "should" allow you 3 instances of xgl.

---

