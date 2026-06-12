---
title: "How can I interpret zeitgeist logs?   (12.04LTS)"
date: 2013-03-30
forum: Desktop Environments
---

### Post by zaly on 2013-03-30
I'm trying to find the history/log of activities done recently (yesterday in this case) on my computer.

From what I read zeitgeist is what keeps the activity log (in .sqlite files), I installed the sqlite firefox addon and sqlite manager but since I'm not familiar at all with this kind of files I don't know how to interpret the information stored in them.

A graphical interface for zeitgeist is the Activity Log Journal but I only just installed it so there's nothing n the journal, it is still blank.
Is there a way to read zeitgeist logs without using the activity log journal? Or to import zeitgeist logs in the activity log journal to read them?

---

### Post by Frogs Hair on 2013-03-30
[COLOR=#000000]Zeitgeist history is set in the privacy application and I can be set for different lengths of time. Zeitgeist keeps track of what was accessed through dash and those selections appear for your convenience. Zeitgeist is not for tracking  user activity only accessed files and applications .  The link may be of interest . [/COLOR][http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html](http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html)

---

### Post by Krytarik on 2013-03-30
> **zaly said:**
> A graphical interface for zeitgeist is the Activity Log Journal but I only just installed it so there's nothing n the journal, it is still blank.
From here:

[http://www.webupd8.org/2010/01/install-gnome-activity-journal-and.html](http://www.webupd8.org/2010/01/install-gnome-activity-journal-and.html)
> If you get an empty Gnome Activity Journal, close it and run this in a terminal:
```
zeitgeist-daemon --replace
```
Then open Gnome Activity Journal again.
ADD.: I should add that you may want to run it via the Alt+F2 dialog instead, or if you indeed run it from a Terminal, add a "setsid" in front of it. This is redundant, though, if you've since relogged in.

Regards.

---

