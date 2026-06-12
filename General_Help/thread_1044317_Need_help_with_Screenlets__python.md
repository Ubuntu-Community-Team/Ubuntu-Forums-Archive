---
title: "Need help with Screenlets / python"
date: 2009-01-19
forum: General Help
---

### Post by xjas05 on 2009-01-19
I'm using screenlets... theres a windowlist screenlet, but it doesn't have the 'center' functionality, quick google search finds:

[https://bugs.launchpad.net/screenlets/+bug/302488](https://bugs.launchpad.net/screenlets/+bug/302488)

so theres a patch..
[http://launchpadlibrarian.net/19967250/WindowlistScreenlet.py.patch](http://launchpadlibrarian.net/19967250/WindowlistScreenlet.py.patch)


how do i apply that patch




EDIT: SOLVED

```

sudo apt-get install patch
patch WindowlistScreenlet.py WindowlistScreenlet.py.patch

```

---

