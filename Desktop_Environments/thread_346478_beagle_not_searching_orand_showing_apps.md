---
title: "beagle not searching or/and showing apps"
date: 2007-01-25
forum: Desktop Environments
---

### Post by royg1234 on 2007-01-25
Beagle search doesn't seem to be searching or showing applications.  (e.g. I search for "firefox", and no applications come up).

Any ideas?

---

### Post by royg1234 on 2007-01-26
nobody?  Something else, if I search for "ter*", terminal comes up, but for "t*", nothing does.  I would greatly appreciate any help.

---

### Post by cmfrtblynmb on 2008-04-25
The same problem here! ihad this problem after upgrading to hardy

---

### Post by dbera on 2008-04-25
To remove unnecessary matches, there could be a limit on the number of actual characters you have to type before the '*' could be used. Just a guess.

The details of all applications are stored in a system-wide index. AFAIR that index is created/updated at the midnight by a cron job. So either you can wait till that system wide index is updated for Hardy or do it yourself.

---

