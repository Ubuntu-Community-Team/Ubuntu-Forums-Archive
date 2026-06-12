---
title: "apt-get problem with CD line in sources.list"
date: 2005-10-16
forum: Desktop Environments
---

### Post by hoodwink on 2005-10-16
I upgraded from kubuntu 5.04 to 5.10 using the recommended approach in another thread. Unfortunately (and that's putting it mildly)  the upgrade was not comple in one whack, but went on over several days and included one set of upgrades that totaly destroyed X. Fortunately that was fixed rapidly.

The one thing that I haven't seen in any thread. How to fix the initial line in /etc/apt/sources.list. I have the following, of course, since I started with 5.04 CD's:

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

Since I have no CD's for 5.10, what should be in this line? As is, I get a crap load of error messages every time I run, and I would like to eliminate these.

Thanks,

Collins

---

### Post by hoodwink on 2005-10-16
Sorry this post went to the wrong thread, since I am a kubuntu user, but the answer to my problem should be common for either ubuntu or kubuntu.

---

### Post by Ampersand on 2005-10-16
run ```
sudo gedit /etc/apt/sources.list
```
You ca then put # at the beginning of the CD-ROM line. You can also edit the sources from Synaptic (settings - repositories) and delete the cd repository.

---

### Post by seldenthuis on 2005-10-16
Hoary used to install a few packages from CD instead of the online repositories. As far as I know Breezy doesn't. There isn't even a 'deb cdrom'-line in Breezy's sources.list. I just removed that line when I upgraded to Breezy and everything works like a charm.

---

### Post by hoodwink on 2005-10-16
Thanks to all the resopnders - the CD line will go by-by.

---

