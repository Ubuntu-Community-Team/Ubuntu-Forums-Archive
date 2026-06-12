---
title: "Menus look messed on KDE after upgrade to 13.04"
date: 2013-04-29
forum: Desktop Environments
---

### Post by vibrunazo on 2013-04-29
After I upgraded Kubuntu from 12.10 to 13.04 (using the built in automatic upgrade), some of the KDE menus are looking really messed up. Here is one example from the notification overflow menu.

Is there something I can do about it on my end, other than just re-installing the whole thing?

[IMG]http://i.imgur.com/FWYwzfB.png[/IMG]

---

### Post by schnelle on 2013-04-30
You can reset kwin (desktop effects) to its defaults and see if that helps.

Remove ~/.kde/share/config/**kwinrc** file and then alt+f2 and type *kwin --replace* and hit enter.
Then you can configure your desktop effects from scratch in system settings>desktop effects.

Hope it helps :)

---

