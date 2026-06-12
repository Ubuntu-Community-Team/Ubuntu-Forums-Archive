---
title: "How do I re-enable cpu scaling?"
date: 2009-03-10
forum: General Help
---

### Post by bart1452 on 2009-03-10
I recently put my laptop through "Recovery" and "Fix broken packages" during which it upgraded some packages and on reboot it informed me that cpu frequecy scaling was not supported or the computer was not configured for it. Now the cpu runs at top speed all the time according to the monitor applet. Well, cpu scaling was working before the recovery and "fix broken packages" jobs were done, so what disappeared and what and where do I put it back?

I put p4_clockmod in the /etc/modules/ file like I found in a Source Forge help page, but that didn't help. That's the only how-to I found on a subject search.

---

### Post by LegendofTom on 2009-03-10
If you have an amd cpu, your best bet might be to reinstall powernowd.

---

### Post by bart1452 on 2009-03-10
Thanks, Tom. I do have a AMD cpu and that did it! I had tried cpudyn after seeing powernowd was already installed and it didn't work.

Powernowd does it.

---

