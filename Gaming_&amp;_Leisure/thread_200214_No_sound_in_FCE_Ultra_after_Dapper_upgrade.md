---
title: "No sound in FCE Ultra after Dapper upgrade"
date: 2006-06-19
forum: Gaming &amp; Leisure
---

### Post by Dr. Feelgood on 2006-06-19
I just upgraded to Dapper and now FCEU has no sound.  It says "failed to initailize sound".  What changed after the upgrade and how do I fix it?

---

### Post by Dr. Feelgood on 2006-09-03
Ok, I'm going to bring this post back from the dead since I found a fix to my problem.
```
killall esd
```
This actually works if typed in before starting fceu an even Diablo 2 under wine (since it was having the same issues with no sound every now and then)

---

