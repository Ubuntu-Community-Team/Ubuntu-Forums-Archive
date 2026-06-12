---
title: "Dell 10v : 190 updates available"
date: 2009-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wrinkley1 on 2009-06-20
Update Manager on my Mini 10v says there are 190 updates available. Surely this can't be right !
Has anyone installed them and if so was it all OK ?
If this isn't right is there a way to get rid of them ? I have not downloaded the updates !
HELP!

---

### Post by Brandon Williams on 2009-06-20
As shipped, then mini 10v will update once with a small number of upgrades (15 at the time I received mine), including update-manager-core, which installs /etc/apt/sources.list.d/dell-mini.list. This new package source will trigger a second update with large number of packages to upgrade (190 now, could be more later). This is expected, and it worked just fine for me. The only (very minor) problem that I see at the moment is that something appears to be a little bit screwed up with scrollkeeper. This is not a problem for day-to-day use, though.

I assume that you already fixed the problem with libxcb-shape0, which had to be fixed in order for that first small update to work.

---

### Post by wrinkley1 on 2009-06-20
Thanks Brandon, I'll try installing the updates. Yes I fixed the shape0 problem with info from another thread.I was worried because I realised after I posted that I'd used 'Add / Remove Programs' to browse all available programs, not just supported ones (I didn't install anything). I thought this might mean I'd acquired unsuported changes in Update Manager i.e. it was looking in a different respositary.

---

