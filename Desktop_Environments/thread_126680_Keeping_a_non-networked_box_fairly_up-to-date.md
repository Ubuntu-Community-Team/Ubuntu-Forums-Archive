---
title: "Keeping a non-networked box fairly up-to-date"
date: 2006-02-07
forum: Desktop Environments
---

### Post by logixoul on 2006-02-07
There are 2 computers in my home - one with SUSE Linux OSS 10.0, called *newK* and one with Kubuntu 5.10, called *Kwen* (doesn't have enough RAM for YaST). newK is networked, but Kwen isn't and I don't feel like spending money for a router to share the connection. I tried to install several games for mom to play on Kwen and found out that the games depended on newer versions of libs or on libs not installed at all. My first thought was to see the dependencies (e.g. [here]("http://packages.ubuntu.com/breezy/games/gtkballs")), download them manually, transfer them by floppy and install them one by one. But this would be an insane time-eater, considering that mom wants a new game every, like, two days. Is there a more effective way of doing this?
BTW I'm from a so-called "third-world" country, so please don't tell me to *just get over it and go buy a router*. Our family just doesn't have the money.

---

### Post by GeneralZod on 2006-02-07
I've not really looked into this myself, but people always seems to recommend [apt-zip](http://packages.debian.org/unstable/admin/apt-zip) for this situation.

---

### Post by az on 2006-02-07
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

You don't have to burn this to a cd.  You can keep a local repository on one box and use it to update the other boxes on your network.

---

### Post by logixoul on 2006-02-10
Thanks.

---

