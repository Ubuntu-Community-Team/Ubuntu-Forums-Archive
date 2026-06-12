---
title: "[Dell Mini 9] Gparted hangs at &quot;Scanning all devices...&quot;"
date: 2008-11-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by earthpigg on 2008-11-26
I've seen others **not **using Dell Mini 9's with this issue, and it seems to come from something that went wrong with the fstab (whatever that is).

The thing is, I haven't really changed or modified anything on this 2 day old Mini 9.

My mini 9 is part of the batch that does **not **have the partition problem regarding an 8/16 gig ssd being partitioned for 4 gigs.

contents of /etc/fstab:

```
/dev/sda2             /         ext3 defaults      0 0
proc                       /proc             proc defaults       0 0 
```

:confused:

---

### Post by earthpigg on 2008-11-28
bump!

---

### Post by crewkid89 on 2009-01-28
Does anyone know of a fix to this?  Someone from launchpad emailed me one but it had no effect.

---

### Post by Craigacp on 2009-01-30
Gparted appears to hang on my computer, but if I leave it for a good 5 minutes it loads properly. How long are you leaving it before you think its dead?

---

### Post by armandh on 2009-01-31
I used parted magic without problems

---

### Post by crewkid89 on 2009-02-03
> **Craigacp said:**
> Gparted appears to hang on my computer, but if I leave it for a good 5 minutes it loads properly. How long are you leaving it before you think its dead?

I have been able to confirm this.  It takes several minutes but then loads properly.

---

