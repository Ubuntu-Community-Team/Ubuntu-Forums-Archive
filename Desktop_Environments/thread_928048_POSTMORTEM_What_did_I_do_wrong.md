---
title: "POSTMORTEM: What did I do wrong?"
date: 2008-09-23
forum: Desktop Environments
---

### Post by matt_feliks on 2008-09-23
Well, I was fiddling around with a UNIX for newbies guide, and decided to start another GUI session (Kub 8.04) through terminal using startx -- :1

I switched to this using Ctrl Alt F8 and everything seemed fine. But when I switched back my original GUI, Konsole was unresponsive.

Upon rebooting to solve this, KDE wouldn't start. I'm thinking, ****, I should've backed up. The error was: No write access to /home/matt/.ICEauthority ... I eventually managedreinstated KDE by doing sudo chown matt .ICEauthority from a failsafe terminal.

Since then I haven't had any problems.

So what the hell happened? Is .ICEauthority something to do with saving sessions? :confused:

---

### Post by matt_feliks on 2008-09-26
bump... any ideas?

---

