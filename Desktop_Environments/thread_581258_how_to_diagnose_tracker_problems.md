---
title: "how to diagnose tracker problems?"
date: 2007-10-19
forum: Desktop Environments
---

### Post by szulat on 2007-10-19
i just upgraded to 7.10 yesterday (from feisty) and now i'm fighting to make the system usable :-)

for example i wanted to try the new tracker.
the first contact: run the deskbar applet, type one word, delete, type another, deskbar hangs, kill it, finished. well... the first test was not entirely successful, but i'm not giving up so easily.

after installing the commandline tools (tracker-utils package) i was able to determine that the deskbar applet was not particularly evil  - all tracker-* utilities just hang. so i thought that perhaps there is some conflict with beagled (which was still running after the upgrade).
beagle was removed, and so was tracker ("mark for complete removal") to make a fresh start.

now, after reinstalling and starting trackerd it seemed to accept queries (for example i saw that tracker-stats shows the increasing number of files and tracker-status is "Indexing").
unfortunately, tracker-search still does not return any matches.
and what is worse, it hangs after several calls, like before. so i achieved nothing :-P

what can i do to resolve this?

---

### Post by Anon Customer on 2007-10-19
Having the same problems, please update if you have any luck diagnosing the problem. Thanks!

I also had Beagle installed and working when I upgraded. I also tried removing it and that didn't help. Tracker is working sporadically, last night was great for a number of searches, this morning can't do a single one.

---

### Post by srikantmarakani on 2007-10-19
In my case, it seemed to work ok in the beginning, but yesterday it increased its memory requirement to 1.7gig resident memory (3gig total) :eek:! Needless to say I have removed it for now. Including networked file systems I do have about 2tb of disk space but 1.7gig of resident memory is insane (atleast until 16gig or so of ram becomes standard :rolleyes:)!

---

