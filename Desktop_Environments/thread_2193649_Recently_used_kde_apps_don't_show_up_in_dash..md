---
title: "Recently used kde apps don't show up in dash."
date: 2013-12-14
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2013-12-14
In Ubuntu 13.10 recently launched kde applications (e.g k3b) don't show up in the recently used applications list in the dash though they are searchable. A bug has been reported and the original bug reporter has found the reason for this behaviour. [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1251915](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1251915)  

Basically zeitgeist has some difficulty accessing /usr/share/applications/kde4 where the .desktop files of these applications reside. The workaround of manually creating symlinks for these .desktop files to /usr/share/applications works, as would copying the contents of /usr/share/applications/kde4 to /usr/share/applications. But these methods seem tedious. I am wondering if there is a more automatically way to achieve the same. 

Also please add an affect me too to the bug report. Thanks.

---

### Post by monkeybrain20122 on 2013-12-16
Nobody uses kde applications in Unity??:confused:

---

