---
title: "Pidgin Memory Leak?"
date: 2009-03-11
forum: General Help
---

### Post by muecker on 2009-03-11
Has anybody else noticed a memory leak in Pidgin 2.5.2 under Intrepid?  Yesterday afternoon I noticed it was using about a gig of virtual memory.  Today I noticed it was using 2 gig of virtual memory.  I'm not sure where the leak is, I just noticed there is one.  I restarted it and now it is only using 133 meg.

---

### Post by jonobr on 2009-03-11
hello ,


I think this was noted for 2.5.2 in launchpad [here]("http://https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/200392")

The bug was opened for an earlier version, however, later posts indicate a big memory leak issue which could be reproducible.

Im using 2.5.4 and intrepid and dont notice this...
Maybe fixed in the interim? The bug was not closed or marked as fixed.

---

### Post by Neo_The_User on 2009-03-11
If anybody finds the C file in Pidgin, tell me and I will write a fix ASAP. I'm bored out of my mind.

---

### Post by jchysk on 2009-03-28
Yeah I just noticed pidgin using 4 gigs of virtual memory. Even if I close it out and reopen it. I'm going to try restarting and see if that helps (haven't restarted in at least a few weeks).

---

### Post by jchysk on 2009-03-28
went down to 478.8mb

---

### Post by khc on 2009-03-29
> **jchysk said:**
> Yeah I just noticed pidgin using 4 gigs of virtual memory. Even if I close it out and reopen it. I'm going to try restarting and see if that helps (haven't restarted in at least a few weeks).

Virtual memory doesn't mean much, especially if you are on 64bit. It's (almost always) only the residential memory usage that matters.

---

### Post by TerrorBite on 2009-05-08
I just noticed Pidgin 2.5.2's memory usage when it failed to launch a URL with a fork() "failed to allocate memory" error. On a system with 2GB of RAM, it's using 702MB Virtual / 627MB residential. This has been increasing steadily over the few days I've been running Pidgin. I've run into issues with Pidgin's memory usage in the past.

A thought: Could the leak be caused by a Pidgin plugin, instead of the core app? What Pidgin needs is a way to measure the memory usage of individual plugins.

---

