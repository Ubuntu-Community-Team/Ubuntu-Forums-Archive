---
title: "What does -session mean ?"
date: 2008-04-28
forum: Desktop Environments
---

### Post by Cygnus on 2008-04-28
I have made a small tray application a while back ago. But I just noticed something today. When I logged into KDE without having my application running:

```
$ ps aux|grep snake
cygnus   2422  0.0  1.3  32824 13984 ?        S    10:52   0:00 snaketray -session 10dbe17472000119365256900000057900124_1209139523_659393
cygnus   2423  0.0  1.3  32824 13980 ?        S    10:52   0:00 snaketray -session 10dbe17472000120030566800000103440030_1209139523_659614
cygnus   2424  0.0  1.3  32824 13988 ?        S    10:52   0:00 snaketray -session 10dbe17472000120118061300000289180039_1209139523_659401
cygnus   2428  0.0  1.3  32824 13984 ?        S    10:52   0:00 snaketray -session 10dbe17472000120334710400000053840023_1209139523_659814
```

What are those -session entries ? And I have not even started the app so why is it running ? After starting it it is listed as normal but the four -session entries are still there unless I kill them.

---

### Post by Cygnus on 2008-04-29
No clues about this ?

---

### Post by Cygnus on 2008-05-28
Does it have something do with if you exit kde with the application still running ?

---

