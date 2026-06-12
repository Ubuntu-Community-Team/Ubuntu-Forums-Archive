---
title: "Apache refuses to uninstall"
date: 2009-05-07
forum: General Help
---

### Post by ownaginatious on 2009-05-07
I'm trying to uninstall Apache2 to try and fix something, but for some reason, it's not...

I have removed the package, and it says it's no longer installed, but when I restart the computer, the web server starts up again...

Anyone know how to solve this problem?

Thanks,

Dillon

---

### Post by albinootje on 2009-05-07
> **ownaginatious said:**
> I'm trying to uninstall Apache2 to try and fix something, but for some reason, it's not...


Please post the output of this in a terminal :
```

dpkg -l|grep apache

```

---

