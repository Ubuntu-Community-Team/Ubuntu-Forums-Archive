---
title: "no background, gdm already running"
date: 2007-05-10
forum: Desktop Environments
---

### Post by paradoxchild on 2007-05-10
I have a problem where in normal sessions (not failsafe) gdm somehow starts before if is supposed to causing it not to start correctly. This causes me to not have a background or anything on it (can't even right click). I know how to stop and restart it, as I've done it many times, but that doesn't help since I have to log back in. In my daemon.log it says 
"gdm[5579]: GDM already running. Aborting!"
I need to either change the order of how my things startup after logging on, fixing gdm itself, or just making my session startup go back to the original default. Please Help

Currently running feisty (upgraded hoping it may fix the problem), but was running edgy early today. (still have to update some sources and stuff)

Please help

---

### Post by paradoxchild on 2007-05-13
This fixed my problem but probably doesn't fix that fact that gdm is already running logged in daemon.log (haven't restarted and checked yet). In your sessions add metacity and nautilus to the startup programs. log off and log back in and it should work fine if anyone else has this problem. This was mostly likely brought on by beryl and possibly other things.

---

