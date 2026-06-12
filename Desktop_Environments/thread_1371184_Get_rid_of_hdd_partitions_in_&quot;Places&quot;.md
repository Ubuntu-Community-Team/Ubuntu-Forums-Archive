---
title: "Get rid of hdd partitions in &quot;Places&quot;"
date: 2010-01-03
forum: Desktop Environments
---

### Post by ansiktsburk on 2010-01-03
Under the "places" menu I have "home", "music", etc. fine, I can live with that. But it also show some hdd partitions that I do not want to have there!
How can I get rid of them for all users?

---

### Post by lovinglinux on 2010-01-03
Another reason I love KDE :)

Anyway, see [http://ubuntuforums.org/showthread.php?t=99086](http://ubuntuforums.org/showthread.php?t=99086)

That thread seems to have some methods.

You could also try to find this option in gconf-editor. I'm using KDE, so I can't help you any further, but [these Google results](http://www.google.com/search?q=gconf+hide+partition+site%3Aubuntuforums.org) might help.

---

### Post by mcduck on 2010-01-04
> **ansiktsburk said:**
> Under the "places" menu I have "home", "music", etc. fine, I can live with that. But it also show some hdd partitions that I do not want to have there!
How can I get rid of them for all users?

Mount the partitions anywhere else than inside /media, or disable automatic mounting for them them completely in /etc/fstab.

---

