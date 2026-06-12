---
title: "Access protected files from different ubuntu partition"
date: 2008-12-08
forum: General Help
---

### Post by sandswipe on 2008-12-08
After several months of great performance and a few weeks of spotty to embarrassing service, I'm about to break down and find a copy of windows. 
The latest issue involves my two different root partitions, one of which runs and the other of which has some very important school projects. I can access unprotected folders, but cannot find a way to get to folders that in most cases I am SURE I never set to protect, and just arbitrarily wrapped themselves for my own inconvenience.

What's the easiest way to unprotect files on partition b and pull them up on partition a?

dell something or other with radeon graphics card that hates 8.10
System that runs: 8.04
system that boots with no working video of any sort: 8.10
the two partitions have different usernames and passwords

---

### Post by lovelyvik293 on 2008-12-08
You can set the permissions or the ownership for that diffrent partition.
Using the chmod and the chown commands.

---

### Post by sandswipe on 2008-12-08
Thanks, that fixed it, although it only seems to apply to a single file or folder at a time, and not a folder+contents. Not important right now, anyway. 
I'd been googling for twenty minutes and wasn't finding anything directly applicable. Now if I can just figure out why portal and half life don't show video even in -window and how to stream video to my xp laptop I'll almost be able to relax about my computer again.

---

### Post by bodhi.zazen on 2008-12-08
> **sandswipe said:**
> Thanks, that fixed it, although it only seems to apply to a single file or folder at a time, and not a folder+contents. Not important right now, anyway. 
I'd been googling for twenty minutes and wasn't finding anything directly applicable. Now if I can just figure out why portal and half life don't show video even in -window and how to stream video to my xp laptop I'll almost be able to relax about my computer again.

use the -R flag (for recursive)

---

