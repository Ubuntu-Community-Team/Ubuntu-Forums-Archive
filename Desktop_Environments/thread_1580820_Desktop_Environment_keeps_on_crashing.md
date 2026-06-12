---
title: "Desktop Environment keeps on crashing"
date: 2010-09-23
forum: Desktop Environments
---

### Post by lkjoel on 2010-09-23
I have a problem with my Desktop Environment.
Somehow, it keeps crashing on me.
Here is a list of the desktop environments that crash on me:

GNOME - Crashes very often
IceWM - Crashes often
Blackbox - Crashes sometimes
KDE - Crashes rarely

None of them do not crash.
Could anyone help me?
Thanks!

---

### Post by deesto on 2010-09-24
Possibly a problem with X?  Have you had a look at /var/log/Xorg.0.log (and other logs in the same directory)?  You'll want to pay attention to any lines including `(WW)`, but any real problem lines would contain `(EE)`.

---

### Post by lkjoel on 2010-09-24
> **deesto said:**
> Possibly a problem with X?  Have you had a look at /var/log/Xorg.0.log (and other logs in the same directory)?  You'll want to pay attention to any lines including `(WW)`, but any real problem lines would contain `(EE)`.
I do not see any (EE).
I mostly see (II) and **.

---

### Post by deesto on 2010-10-14
If they _all_ crash, there must be an underlying package that's corrupt or not properly installed, but it's not likely a package related to one or more of the WMs themselves (unless they all have corrupt packages, which would likely mean you have many other currupt packages).  I would think it's X related, but you're saying there are no errors in the X log.  What about after a crash: does anything appear in this log then?  If you're looking in the log _after_ restarting an X session, you'll have to look in another log file, not that exact one, since it starts over fresh with each session.  Also look in /var/log/messages for clues right after a crash.

---

### Post by lkjoel on 2010-10-16
> **deesto said:**
> If they _all_ crash, there must be an underlying package that's corrupt or not properly installed, but it's not likely a package related to one or more of the WMs themselves (unless they all have corrupt packages, which would likely mean you have many other currupt packages).  I would think it's X related, but you're saying there are no errors in the X log.  What about after a crash: does anything appear in this log then?  If you're looking in the log _after_ restarting an X session, you'll have to look in another log file, not that exact one, since it starts over fresh with each session.  Also look in /var/log/messages for clues right after a crash.
Thanks, I will try that when it crashes.
In the meantime, I'm just using Blackbox.

---

