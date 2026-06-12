---
title: "kicker spams syslog"
date: 2020-04-12
forum: Desktop Environments
---

### Post by lvm on 2020-04-12
Every time I start a program via kicker (application menu) it posts a humongous notification to syslog like this one:

```

Apr 12 16:22:19 server org.kde.ActivityManager[1414]: Creating the cache for:  "applications:systemsettings.desktop"
Apr 12 16:22:19 server org.kde.ActivityManager[1414]: Already in database?  true
Apr 12 16:22:19 server org.kde.ActivityManager[1414]:       First update :  QDateTime(2019-05-10 08:24:15.000 MSK Qt::TimeSpec(LocalTime))
Apr 12 16:22:19 server org.kde.ActivityManager[1414]:        Last update :  QDateTime(2020-04-12 10:42:09.000 MSK Qt::TimeSpec(LocalTime))
Apr 12 16:22:19 server org.kde.ActivityManager[1414]: After the adjustment
Apr 12 16:22:19 server org.kde.ActivityManager[1414]:      Current score :  7.28854
Apr 12 16:22:19 server org.kde.ActivityManager[1414]:       First update :  QDateTime(2019-05-10 08:24:15.000 MSK Qt::TimeSpec(LocalTime))
Apr 12 16:22:19 server org.kde.ActivityManager[1414]:        Last update :  QDateTime(2020-04-12 10:42:09.000 MSK Qt::TimeSpec(LocalTime))
Apr 12 16:22:19 server org.kde.ActivityManager[1414]: Interval length is  0
Apr 12 16:22:19 server org.kde.ActivityManager[1414]:          New score :  8.28854
Apr 12 16:22:19 server org.kde.ActivityManager[1414]: ResourceScoreUpdated: "874828fb-1507-47dc-97b9-2ca8c882537c" "org.kde.plasma.kicker" "applications:systemsettings.desktop"

```

How can I disable it? 18.04.

---

