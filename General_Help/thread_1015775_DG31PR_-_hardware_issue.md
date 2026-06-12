---
title: "DG31PR - hardware issue"
date: 2008-12-19
forum: General Help
---

### Post by BuildSmart on 2008-12-19
It appears that a problem exists with sleep and the Intel DG31PR motherboard.

I've been told that the issue might be video related however the problem occurs if I use a video card or the onboard graphics.

When you put it to sleep it goes to sleep, when you wake it it beeps 4 times and then restarts so it never wakes.

Nothing in the logs cause it never wakes to write any errors, no onscreen messages so debugging information isn't available.

Do I need a patched DSDT?  (if so where can I get it)

If a patched DSDT is not available, if I provide the DSDT source can someone with the knowledge/experience patch it?

---

### Post by Arup on 2008-12-19
I have this board as well running quad core, the inbuilt Intel support has some bugs, notably the one you mention as well as logging out and relogging will get you a blank screen. Turning off compiz and turning on Metacity solves that issue though. I have flashed it with the latest BIOS ver 0059.

---

### Post by BuildSmart on 2008-12-19
Sleep is the only issue I need to overcome, all other problems have been resolved.

---

