---
title: "Setting processor affinity for Urban Terror"
date: 2008-02-24
forum: Gaming &amp; Leisure
---

### Post by Melcar on 2008-02-24
Anyone know how to set processor affinity?  The Urban Terror read me recommends that the program be isolated to one core if it's run on a multi core system, since running the game on a multi core may lead to slowdowns .  I have indeed noticed that when the process switches back and forth between cores the game kinda stutters for a few seconds.

---

### Post by happyhamster on 2008-02-25
Should be possible with the taskset command. To set affinity for core 1 for example:

taskset -c 1 program_name

See 'man taskset' for a bit more info.

---

### Post by Melcar on 2008-02-25
That actually works, thanks, but now sound is jerky for some reason.  The slowdowns are not there thought.

---

