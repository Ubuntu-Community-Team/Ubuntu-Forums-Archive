---
title: "Sometimes machine wakes up from hibernate already logged in"
date: 2006-09-29
forum: Desktop Environments
---

### Post by rrwo on 2006-09-29
I'm using Dapper Drafke with Xfce. Hibernate works, but sometimes when the machine is restarted, it wakes up already logged in, rather than locked.
I've also had it wake up logged in with the shutdown menu.  I'm guessing that it's saving the state before the system is locked.

Is there a way to fix this?

It's a security issue, since it means that it sometimes allows someone to get into my laptop without a login.

---

### Post by rrwo on 2006-10-24
I still have this problem. Also, sometimes when I startup, it shuts down within a minute. When I start it up afterwards, it's in the state it was before it shut down (applications I opened are running).

---

### Post by rrwo on 2006-10-31
UPDATE: I'm wondering if this is related to a setting in /etc/hibernate to enable on the of the locking options in common.conf. Alas, I've upgraded to Edgy and cannot suspend/hibernate at all, so this issue is moot until I've fixed that.

---

### Post by rrwo on 2006-11-24
Spoke too soon. In the last few days I've been having the problem with Edgy: when it wakes up from hibernating, sometimes it is logged in.  Does this happen to anyone else?

---

