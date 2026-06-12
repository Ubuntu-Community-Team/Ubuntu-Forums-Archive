---
title: "How to lock a version"
date: 2009-04-29
forum: General Help
---

### Post by Scormen on 2009-04-29
Hi all,

In Synaptic it is possible to "lock" a version.
How does that work via the CLI?

Thanks,
Kris

---

### Post by Tibuda on 2009-04-29
What do you mean by "lock"?

---

### Post by Scormen on 2009-04-29
Hold the current versions, so that Ubuntu won't update that packet.

---

### Post by drs305 on 2009-04-29
To lock it in synaptic, highlight the package, then Package, Lock Version.

There is also the "--no-upgrade" option for apt-get and "aptitude hold" option for aptitude. Review the "man apt-get" and "man aptitude" pages for specifics.

---

### Post by Scormen on 2009-04-29
Yes, I know.

But how do you do that by command in the CLI?

---

### Post by Tibuda on 2009-04-29
> **Scormen said:**
> Yes, I know.

But how do you do that by command in the CLI?

```
sudo aptitude hold packagename
```

---

### Post by slakkie on 2009-04-29
> **Scormen said:**
> Hold the current versions, so that Ubuntu won't update that packet.

Check out pinning a package:
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by bapoumba on 2009-04-29
You need to pin a version release in /etc/apt/preferences:
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

Edit: Doh, I'm slow ;)

---

### Post by Scormen on 2009-04-29
Thats clear ;) thanks for the answers!

---

