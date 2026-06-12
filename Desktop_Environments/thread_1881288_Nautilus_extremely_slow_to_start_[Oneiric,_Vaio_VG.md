---
title: "Nautilus extremely slow to start [Oneiric, Vaio VGNAR520E]"
date: 2011-11-15
forum: Desktop Environments
---

### Post by manzdagratiano on 2011-11-15
Hi all,

I am running an up-to-date Oneiric on my Vaio VGNAR520E, and the only showstopper is Nautilus; it takes up to 15-20 seconds to start, always graying out for a few seconds in the process. Upon the initial release of Oneiric, there was the nautilus-open-terminal plugin causing Nautilus to crash, but that was fixed a while ago and I have not had a crash since. I have no other Nautilus scripts installed aside from this one, and I have the same setup on a Dell Vostro V13, in which Nautilus starts instantly like it should - so I think the difference is hardware-related. The specs are:

Vaio:
Processor: Intel Centrino Duo
VGA: nvidia GeForce 8400 GT
Wireless (n/a?): Intel

Vostro:
Processor: Intel Core 2 Solo
VGA: Intel
Wireless (n/a?): Broadcom

Aside from these, there are no significant differences that I think apply. I have tried deleting the nautilus folders from gconf and cache, and not only did they not reappear, the problem persists. Any ideas people?

---

### Post by manzdagratiano on 2011-11-15
I believe I fixed it, though it is not clear why... I searched for the files nautilus installs using:
```

$ dpkg-query -L nautilus

```
and then for which files were associated with nautilus:
```

$ locate nautilus | grep -v home

```
I noticed that both python2.7 as well as python2.6 files were installed in /usr/lib. I purged all python2.6 packages including the minimal environment, since they did not break any other package (and I use 2.7/3.0 anyway), and voila! Nautilus was starting within seconds after. I don't exactly know the cause, except conjecture that perhaps the necessary scripts were being initialized by searching in both python2.6 and python2.7. Anyway, problem solved, at least for now :)

---

