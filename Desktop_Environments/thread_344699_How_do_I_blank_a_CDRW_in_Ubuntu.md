---
title: "How do I blank a CDRW in Ubuntu?"
date: 2007-01-23
forum: Desktop Environments
---

### Post by xp_newbie on 2007-01-23
In Windows, the dedicated software you use for burning a CDRW also lets blank it.
But in Ubuntu, how do I accomplish this?

I looked at Places | CD/DVD Creator and I could not find an option to blank a CD.

How do I blank a CD in Ubuntu?

Thanks,
Alex

---

### Post by Joeb on 2007-01-23
If you install gnomebaker or k3b, then you will have a stand alone burning app like in Windows.  Both will give you an option to blank a CDRW.  K3b seems to be more popular, but it is a kde app (runs fine under gnome, though).  Either one (or both) can be installed through the synaptic package manger.

---

### Post by xp_newbie on 2007-01-23
> **Joeb said:**
> If you install gnomebaker or k3b, then you will have a stand alone burning app like in Windows.  Both will give you an option to blank a CDRW.  K3b seems to be more popular, but it is a kde app (runs fine under gnome, though).  Either one (or both) can be installed through the synaptic package manger.

Thanks, Joeb. I actually found a third way, that does not require installing another application: I just type in the command line:

```
cdrecord -blank=fast
```

Thanks!
Alex

---

