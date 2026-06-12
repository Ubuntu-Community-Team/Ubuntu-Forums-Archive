---
title: "Compiz problem after upgrade"
date: 2010-10-14
forum: Desktop Environments
---

### Post by andreus on 2010-10-14
Today u upgrade like normal, but after reboot i had no window decoration and lower panel. I realized i installed some KDE packages and i removed them. 
After another reboot i have window decoration, but compiz doesnt work. When trying make some changes in setting manager, each effect has blank screen and then simply crash. 
After trying setup extra effects on desktop windows decoration disappear and i got message "extra effects cannot be enabled" or something.
Finally after trying run fusion-icon i got error:
```
Backend     : ini
Integration : true
Profile     : default
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'

```

any suggestions?
Thanks

---

### Post by andreus on 2010-10-14
No one know? :/

---

### Post by carlosjimy on 2010-10-14
It appear to be a problem with the version of some compiz package installed. Try downgrading compiz version, see that:

[http://ubuntuforums.org/showthread.php?p=9959374](http://ubuntuforums.org/showthread.php?p=9959374)

Work it?
Bye!

---

### Post by andreus on 2010-10-15
> **carlosjimy said:**
> It appear to be a problem with the version of some compiz package installed. Try downgrading compiz version, see that:

[http://ubuntuforums.org/showthread.php?p=9959374](http://ubuntuforums.org/showthread.php?p=9959374)

Work it?
Bye!

Thanks for answer.
I downgrade to libdecoration0 1:0.8.4-0ubuntu15.2 (amd64 binary) but still got same error :confused:

---

### Post by carlosjimy on 2010-10-15
Nops! You must uninstall all packages relationated with compiz, then downgrade all these forcing version with synaptic:

**compiz** 1:0.8.6-0ubuntu9(maverik)
**compizconfig-beckend-gconf** 0.8.4-1ubuntu5
**compiz**-**plugins** 1:0.8.6-0ubuntu9(maverik)
**compiz-core **1:0.8.6-0ubuntu9(maverik)
**compiz-fusion-plugins-main** 0.8.6-0ubuntu2
**compiz-genome **1:0.8.6-0ubuntu9(maverik)
**libdecoration0** 1:0.8.6-0ubuntu9(maverik)
**libcompizconifg0** 0.8.4-0ubuntu3

Bye!

---

### Post by andreus on 2010-10-16
> **carlosjimy said:**
> Nops! You must uninstall all packages relationated with compiz, then downgrade all these forcing version with synaptic:

**compiz** 1:0.8.6-0ubuntu9(maverik)
**compizconfig-beckend-gconf** 0.8.4-1ubuntu5
**compiz**-**plugins** 1:0.8.6-0ubuntu9(maverik)
**compiz-core **1:0.8.6-0ubuntu9(maverik)
**compiz-fusion-plugins-main** 0.8.6-0ubuntu2
**compiz-genome **1:0.8.6-0ubuntu9(maverik)
**libdecoration0** 1:0.8.6-0ubuntu9(maverik)
**libcompizconifg0** 0.8.4-0ubuntu3

Bye!


Great It succesfully work now. Big one THANKS for you ;)

I had one more question. I disabled compiz repo for updating, but libdecoration still wants update how can i disable update for libdecoration0?

---

