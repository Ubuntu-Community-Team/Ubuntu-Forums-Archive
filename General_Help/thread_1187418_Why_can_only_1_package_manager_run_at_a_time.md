---
title: "Why can only 1 package manager run at a time?"
date: 2009-06-14
forum: General Help
---

### Post by camper365 on 2009-06-14
Why is is that only one package manager can run at a time?

---

### Post by mikewhatever on 2009-06-14
How many do you need?

---

### Post by Amilo1718 on 2009-06-14
i'd say... cuz webconnections from the same IP address have their limits ?

---

### Post by Amilo1718 on 2009-06-14
> **mikewhatever said:**
> How many do you need?

lol
euh from my IP-address i want to be connected to the same server... let's say a thousand times?
:popcorn:

---

### Post by Therion on 2009-06-14
Well there is really only one true package manager in Ubuntu and that's Apt.  Add/Remove and Synaptic are really only front-end applications that simplify the use of Apt.  You can't have more than one instance of Apt running because, obviously, Apt installs applications packages and maintains dependency integrity.  Having apt be capable of doing things like simultaneously installing *and* removing the same package, for but one example, would be problematic for obvious reasons.

---

### Post by khelben1979 on 2009-06-14
[Wiki about package manager]("http://en.wikipedia.org/wiki/Package_manager").

Read and learn, I guess.

---

### Post by doas777 on 2009-06-14
my guess would be because the manager needs to establish a write-lock on the database, to ensure that operations are concurrent, and can't be interfered with by other processes. for instance, imaging having one terminal open reinstalling wine. and another terminal purging it? it would bad.

---

### Post by MaxIBoy on 2009-06-14
The previous poster is correct.

See, Debian's APT (Advanced Packaging Tool) has a complex and delicate database, in which it stores lists of installed packages, which files belong to which package, dependencies, and so on. If two programs were to fight over control of the database, the data would likely get corrupted. Imagine two cars trying to take the same parking space, and you'll see what I mean.

---

### Post by camper365 on 2009-06-15
ok thx

---

