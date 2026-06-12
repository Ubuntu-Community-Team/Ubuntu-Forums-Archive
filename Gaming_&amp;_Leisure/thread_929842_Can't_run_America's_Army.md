---
title: "Can't run America's Army ??"
date: 2008-09-25
forum: Gaming &amp; Leisure
---

### Post by Christian91 on 2008-09-25
Hey guys,

Pretty new to linux so wanted to try out some games... I have downloaded and installed America's Army but can't run it. I have been looking a lot around and done all the things that people have posted.

I have gone into preferences and ticked the box so it is executable so I don't think that is the problem. When i try to run it just does nothing ?

I'd be very grateful for some help ;)

This is what I get when i run it in terminal:

christian@christian-laptop:~$ '/home/christian/armyops/armyops' 
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by Perfect Storm on 2008-09-25
Install libstdc++5 
It's in synaptic/repo.

---

### Post by Christian91 on 2008-09-25
Thanks so much ;) works now !

---

