---
title: "Screenlets can't start"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by codeAries on 2008-03-18
I have downloaded screenlets_0.0.14-1~getdeb1_all.deb and install it... The installation seems to be OK!

But when i try to run it from System -> Preferences -> Screenlets, nothing happened. 
And when i try to run from the terminal using **screenlets-manager** still nothing, it gives me this output:

```

Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 32, in <module>
    from screenlets import utils
ImportError: cannot import name utils

```

---

### Post by plun on 2008-03-18
Strange error....:confused:

Are you running Gutsy ?  32 or 64 bit ?

Remove Screenlets and then reinstall again

```
sudo apt-get remove --purge screenlets
```

---

