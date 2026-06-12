---
title: "Ubuntu hibernate error caused by Compiz?"
date: 2009-02-19
forum: General Help
---

### Post by racie on 2009-02-19
Okay, so I realized that I've never actually used hibernate in Ubuntu.  Well, when I clicked 'hibernate' it took me to a black screen (not an 'off' screen, but a black screen).  I waited a little while and this message popped up:
```
[9991.168007]BUG: soft lockup - CPU#0 stuck for 61s! [compiz.real:5856]
```
So I waited some more.  Shortly thereafter, I received another message saying:
```
[****.*68007]BUG: soft lockup - CPU#0 stuck for 61s! [compiz.real:5856]
```
(It didn't really say ***, but it was a different number than before.)  This continued to happen every 61 (just guessing) seconds.  So eventually I just hit the power button.

So my question is.... what in the world does this mean???

---

### Post by racie on 2009-02-19
bump

---

### Post by racie on 2009-02-20
Anyone know the problem?

---

### Post by xAndrew25 on 2009-03-02
I've got this problem too... For me, it always used to lockup trying to go into standby. When I re-installed ubuntu for *other* reasons, standby suddenly worked, and the hibernate option didn't. It gets locked up whenever I try and I have to shut it off. Help anyone?

---

### Post by alas-poor-yorick on 2009-05-30
Bump - same problem in jaunty, except mine hibernates correctly when I have no or very few programs running. I have AMD 64 and nvidia.

---

### Post by racie on 2009-07-26
Sorry for the massive bump, but I just found out that using Wubi does not support hibernate.  If you installed any version of Ubuntu through Wubi, hibernate will NOT work.

---

