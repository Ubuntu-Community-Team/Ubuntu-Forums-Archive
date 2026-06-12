---
title: "Suspend to Disk Restore Problem (Bug?)"
date: 2009-02-03
forum: General Help
---

### Post by AC-BC on 2009-02-03
Hi All,

I've noticed a little problem with Ubuntu while using the "Suspend to Disk" shut down option.  Actually, two problems.

1)  When coming back from suspension, I noticed that the swap drive has a large portion still in use.  Now, since I have 4GB RAM, I have never seen the swap drive used in actual computing.  So, I suspect this is where Ubuntu stores my system state during suspension.  But apparently it is not relinquishing it after power up and restore.

Not only that, but each suspension uses a new segment of swap memory.  So, it is accumulating, taking up more and more of my swap space.

Though thus far, I've shut down completely before swap space has run out (so I don't yet know what will happen if that occurs).

2)  Second problem, also to do with restoration after "Suspend to Disk."  My desktop customisations disappear.  They are restored after a full shut-down, but upon return from suspension they revert to default.

Are these bugs, or do I need to do some more configuration of some sort?

Thank you in advance for addressing my little problems.

AC-BC

---

### Post by AC-BC on 2009-02-05
No takers on this one, hmmmm?

:-(

---

### Post by AC-BC on 2009-03-29
Update on this problem that nobody wants to touch.

I finally filled the swap partition upon suspension.  As it was shutting down, it gave an error message that said the swap was full.  And then it just sat there; so I had to reset.

Upon reboot, I noticed that the Suspend options were no longer available (Suspend to Disk, and Suspend to RAM).  So, I have not been able to suspend any longer.

Much later, while investigating another problem (Ubuntu seems to have a lot of them), I noticed a message in the dmesg listing:
```

$ dmesg | grep -i 'fail'
[   6.035960] PM: Resume from disk failed.

```

This sounds like the suspension is still active -- caught in the 0-zone.

If anybody would care to take a stab at this, at least the unfinished suspension part, please tell me how I can reset the suspension.

Since the swap partition has been whiped, obviously I can't recover the last suspension.  I just would like to use suspension again.  In other words, could someone please tell my how I can tell Ubuntu not to look for a suspended session that no longer exists, and get back the suspend menu options.

Thanks again.

AC-BC

---

