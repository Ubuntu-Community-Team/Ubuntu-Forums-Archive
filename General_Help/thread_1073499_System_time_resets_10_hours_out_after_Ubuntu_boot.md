---
title: "System time resets 10 hours out after Ubuntu boot"
date: 2009-02-18
forum: General Help
---

### Post by scooter22 on 2009-02-18
Hi Guys, I have this annoyance that after I boot into a graphical session of Ubuntu my system clock resets itself in Win XP. Is this something to do with the time zone? I used the "inside windows" install and presumed that it would just read the clock as it is?

Cheers,
Scooter22

---

### Post by heindsight on 2009-02-18
I don't know much about windows, but I seem to recall that in the past windows used to assume that your hardware clock stores local time while Ubuntu (like all unix like operating systems) expects the hardware clock to store UTC time. When you shut down or restart ubuntu, it sets the hardware clock to the current system clock time (in UTC).

This means that if your timezone is UTC-10 then once you boot windows after ubuntu, windows will think it's 10 hours later than it really is.

The solution is to either configure windows to tell it that your hardware clock is set to UTC, or to configure Ubuntu to tell it that your hardware clock is set to local time. I have no idea how to configure anything in windows, but in Ubuntu you can edit /etc/default/rcS and change the line that says ```
UTC=yes
``` to ```
UTC=no
```

---

