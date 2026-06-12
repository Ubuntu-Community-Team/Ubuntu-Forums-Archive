---
title: "Low-latency (no mouse/audio jerkiness) in Edgy using Feisty kernel"
date: 2007-01-04
forum: Desktop Environments
---

### Post by Rinnan on 2007-01-04
Tired of the jerkiness I was experiencing in Edgy, I did something completely crazy.  I changed all my repositories from "edgy" to "feisty", did a "sudo apt-get update", installed the latest low-latency kernel ("sudo apt-get install linux-lowlatency"), changed all my repositories back to edgy, updated the repository list again, and rebooted.

It worked!  First, amazingly, it booted without exploding.  Everything appears to work.  And the jerkiness?  Completely gone.  Everything is as smooth as Norwegian goat cheese.

This is not a recommendation.  Who knows what can and probably will eventually blow up.  Just a documentation of my experience.  If you try it, and it explodes in your face, we never met, I have no idea who you are.  :p

---

