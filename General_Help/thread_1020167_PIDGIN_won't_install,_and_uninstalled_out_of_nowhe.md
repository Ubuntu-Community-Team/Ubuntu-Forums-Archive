---
title: "PIDGIN won't install, and uninstalled out of nowhere."
date: 2008-12-23
forum: General Help
---

### Post by JakeWatkins on 2008-12-23
I can't install through add/remove, and here's a pic from Synaptics Manager: [http://img78.imageshack.us/my.php?image=screenshotea1.png](http://img78.imageshack.us/my.php?image=screenshotea1.png)

---

### Post by Patrick793 on 2008-12-23
Try this.

```
sudo apt-get purge pidgin pidgin-data libpurple0
sudo apt-get clean
sudo apt-get install pidgin pidgin-data libpurple0
```

From my knowledge it should work, but if it says it will remove ubuntu-desktop say no instead of yes. You don't want to do that.

---

### Post by JakeWatkins on 2008-12-23
It worked. Sometimes, I hate Linux. But when it's fixed, God I love it! = D

Got any fixes on speeding up Flash/keep it from lagging in HD fullscreen on Hulu.com ?

---

