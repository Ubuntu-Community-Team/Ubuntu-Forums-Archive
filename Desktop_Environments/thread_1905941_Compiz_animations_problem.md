---
title: "Compiz animations problem"
date: 2012-01-08
forum: Desktop Environments
---

### Post by PinguyOS on 2012-01-08
I'm using Macbuntu 11.04(it's a kind of ubuntu 11.04 with a mac design). I'm in big trouble with compiz animations. I don't know why but they doesn't work. For example, if i go to ccsm->animations->minimize tab, there is no animation. I click new i choose the animation, but it doesn't record it in the list. If i run compiz from terminal i get this error when adding animation

```
File "/usr/lib/python2.7/dist-packages/ccm/Settings.py", line 149, in Get
    return self.Setting.Value[self.CurrentRow]
IndexError: list index out of range
```

---

### Post by Krytarik on 2012-01-08
Try this, the cause of the issues might be the same, even though the symptoms are not:

[http://ubuntuforums.org/showthread.php?p=11316837#post11316837](http://ubuntuforums.org/showthread.php?p=11316837#post11316837)

Hope it works for you, too.

---

### Post by PinguyOS on 2012-01-09
> **Krytarik said:**
> Try this, the cause of the issues might be the same, even though the symptoms are not:

[http://ubuntuforums.org/showthread.php?p=11316837#post11316837](http://ubuntuforums.org/showthread.php?p=11316837#post11316837)

Hope it works for you, too.

Thank you very muc, it worked.

---

