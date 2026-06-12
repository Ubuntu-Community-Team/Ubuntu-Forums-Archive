---
title: "OnTV - works in window, not in panel"
date: 2008-04-07
forum: Desktop Environments
---

### Post by spiregrain on 2008-04-07
I'm having  a problem with OnTV under Hardy.

It runs fine in a window, as in:
```
/usr/lib/ontv/ontv -w
```

Running without the "-w", or by Adding it to the panel in the normal way doesn't work.  Nothing happens.  The program is running- it gets a process ID and appears in the process list and everything.  Running in debug mode gives nothing either.

Any suggestions for ways to test it further or work out what's going on?

---

### Post by jarvis13 on 2008-04-08
wait...what service are you using for OnTV? Zap2it no longer works and i haven't been able to use my precious OnTV since!

---

### Post by spiregrain on 2008-04-10
I'm using the Bleb.org service.  It's got all the UK channels apart from ITV.  No great loss.

---

### Post by spiregrain on 2008-04-29
I find that this problem persists with Hardy Heron and OnTV 3.  I'd welcome any assistance.  Lots of similar problems have been reported in Launchpad with config details, stack traces and the like.

I have found a partial solution, however- the gnome-swallow-applet.  Anyone following this issue can try that.  It allows any program to be added to the gnome panel, including the window version of ontv (ie. "/usr/lib/ontv/ontv -w").

---

