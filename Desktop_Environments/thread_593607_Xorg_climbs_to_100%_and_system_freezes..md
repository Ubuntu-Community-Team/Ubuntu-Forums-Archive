---
title: "Xorg climbs to 100% and system freezes."
date: 2007-10-27
forum: Desktop Environments
---

### Post by OldGaf on 2007-10-27
If I use my PC all day, everything is fine.

If I leave it idle with no applications running, Xorg slowly uses more and more cpu until it gets up to 100% and freezes the system. At this pint the mouse is still movable but not clickable.

If I leave "Top" running, it still updates as usual but I cannot close it or move it.

If I start using the system before it his 100%, the system is sluggish for a second or two and then cpu drops down to normal.

This started happening with Feisty 32 about a month ago. I then did a clean install of Gusty AMD64 but the problem is still happening.

I have:
AMD Athlon 64 X2 3600+
2 Gig 6700 Ram
Nvidia 8600 GTS

[Bug filed here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/157756")

---

### Post by OldGaf on 2007-10-27
I just tried switching back to the NV driver and the problem still exists.

---

### Post by OldGaf on 2007-10-30
I just did a fresh install of Gusty 32 bit and installed the proprietary driver via the restricted drivers manager. The problem STILL exists.

---

### Post by Happy_Man on 2007-11-18
Yep, I've having the same problem. Gutsy 32-bit, XOrg climbs to 100%, but Superkaramba and top still update. Same symptoms. It only seems to happen in KDE for me. Any tips?

---

### Post by eldragon on 2007-11-18
by any chance do any of you use the vino vnc server?
if you do, shut it down, and see if it helps.....

it did do that to me on feisty....

---

### Post by Happy_Man on 2007-11-18
No... at least I don't think I do. Is that enabled on Gutsy?

---

### Post by Happy_Man on 2007-11-29
One other thing: I find that if I turn off SuperKaramba, the problem disappears. Are any of you guys running SuperKaramba?

---

### Post by OldGaf on 2008-01-18
Yes..... I am running super karamba. I have switched to Debian and I still get the problem..... but only now and then......... once a week maybe.

---

### Post by OldGaf on 2008-04-27
Has there ever been a definitive fix for this?

I have come back from Debian to try 8.04 64bit..... 24 hours in and I hit the same issue........

---

### Post by OldGaf on 2008-04-28
Not using SuperKaramba does indeed seem to fix this for me.

---

