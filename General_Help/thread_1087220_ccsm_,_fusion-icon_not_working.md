---
title: "ccsm , fusion-icon not working"
date: 2009-03-04
forum: General Help
---

### Post by KodeBurner on 2009-03-04
Hi All


When I Start ccsm I Get This Error

```

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/libxslt.so.1: undefined symbol: xmlNewDocPI

```

And When I Start fusion-icon I Get This Error

```

Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.5/site-packages/FusionIcon/util.py", line 21, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/lib/libxslt.so.1: undefined symbol: xmlNewDocPI

```

I Get The Above Errors After Updating My Ubuntu 8.04 64bit

I Have Tried To Reinstall All Compiz .. But Nothing New :(

---

### Post by KodeBurner on 2009-03-04
But Compiz Still Working .. But I Can Not Configure It As I Like Only The Default Settings Still Working

I Have Googled And I Found Nothing :(

Thanks

---

