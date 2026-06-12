---
title: "liquid war is busted....."
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by yowshi on 2008-01-27
ok when i recently tried to launch the game liquid war i got this error 
liquidwar: symbol lookup error: /usr/local/lib/liballeg.so.4.2: undefined symbol: _i_is_cpuid_supported


i have tried reinstalling both liquid war and all the liballeg 4.2 packages

---

### Post by Perfect Storm on 2008-01-27
Properly because liballeg.so.4.2 is installed under /usr/lib and not /usr/local/lib

---

### Post by yowshi on 2008-01-27
but it worked before so why not now. i hadnt run it since before the upgrade to fiesty could this be the cause of my problem?

and how do i fix it without breaking my entire system

---

### Post by Perfect Storm on 2008-01-27
Seems the upgrade messed it up then.

Try uninstall liquid wars and liballegro4.2 (not reinstall)
Then install both of them.

If it doesn't help, try with

```
sudo ln -s /usr/lib/liballeg.so.4.2 /usr/local/lib/liballeg.so.4.2
```

---

