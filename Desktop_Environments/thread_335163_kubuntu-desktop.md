---
title: "kubuntu-desktop"
date: 2007-01-09
forum: Desktop Environments
---

### Post by tylersontag on 2007-01-09
I wanted to give ubuntu a shot w/ the KDE environment since thats what i usually use on the university computers, but when i tried to sudo apt-get install kubuntu-desktop it says it does not exsist, is there some repository i haven't deb'ed into existance?

---

### Post by obsidion on 2007-01-09
> **tylersontag said:**
> I wanted to give ubuntu a shot w/ the KDE environment since thats what i usually use on the university computers, but when i tried to sudo apt-get install kubuntu-desktop it says it does not exsist, is there some repository i haven't deb'ed into existance?


  Did you apt-get update first. There are some things in the multiverse and universe repos but you shouldn't need them to install the basic desktop. Are you sure you didn't make a typo. The other thing is that you actually have to be connected to the net if you installed ubuntu because it doesn't have the kubuntu setup on the cd.

---

### Post by aysiu on 2007-01-10
Post the output of this command: ```
cat /etc/apt/sources.list
```

---

### Post by tylersontag on 2007-01-11
i found out the problem, it was the same one i was having with alot of installations using apt-get or aptitude.  it seems like somply placing sudo before commands wasn't pulling enough clout and i needed to run sudo su to get full access to certain libraries... quite odd, anyways got it installed, thanks for the help/concern all!

---

