---
title: "Solution: no sound effects"
date: 2009-01-31
forum: General Help
---

### Post by Pidgin on 2009-01-31
The lack of sound effects is caused by the bug in [FONT="Monospace"]libcanberra[/FONT].
[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507")
The solution is to update [FONT="Monospace"]libcanberra[/FONT] from 0.06 to 0.10, which can be done by simply adding these repositories and update:
```
deb http://ppa.launchpad.net/gkulyk/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/gkulyk/ppa/ubuntu intrepid main
```
I have just tested that and it works!

---

