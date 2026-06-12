---
title: "Is it possible to reserve cpu &amp; ram space for OS only?"
date: 2012-07-24
forum: Desktop Environments
---

### Post by MasterNetra on 2012-07-24
With only 1GB of ram, my system at times tends to lock up with software (namely minecraft > : ) ) consuming too much ram and/or the CPUs. So I was wondering if there was some way to limit ram and/or cpu consumption from software so that there is at least enough to force kill without waiting 5-15 min to take into effect. I personally don't think so but I figured it doesn't hurt to ask.

---

### Post by Cheesehead on 2012-07-24
> **MasterNetra said:**
> if there was some way to limit ram and/or cpu consumption from software

Of course there is. See [FONT="Courier New"]man nice[/FONT] or [FONT="Courier New"]man renice[/FONT]. You can also renice processes from within System Monitor.

```
DESCRIPTION
     Renice alters the scheduling priority of one or more running processes.
     The following who parameters are interpreted as process ID's, process
     group ID's, or user names.  Renice'ing a process group causes all pro&#8208;
     cesses in the process group to have their scheduling priority altered.
     Renice'ing a user causes all processes owned by the user to have their
     scheduling priority altered.  By default, the processes to be affected
     are specified by their process ID's.
```

---

