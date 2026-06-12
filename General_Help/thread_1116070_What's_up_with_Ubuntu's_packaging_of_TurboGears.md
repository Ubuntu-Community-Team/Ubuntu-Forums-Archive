---
title: "What's up with Ubuntu's packaging of TurboGears?"
date: 2009-04-04
forum: General Help
---

### Post by bkline on 2009-04-04
I'm running the LTS Ubuntu [8.04] on Intel, on which I just installed TurboGears.  Seemed to install fine, but attempts to use it fail:

```
$ uname -a
Linux ws 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux
$ sudo apt-get install python-turbogears
...
Setting up python-turbogears (1.0.4.3-1) ...
...
$ mkdir src/tg
$ cd src/tg
$ tg-admin quickstart
Traceback (most recent call last):
....
ImportError: No module named filters.basefilter

```

Did someone leave out a dependency check in the packaging?

---

### Post by bkline on 2010-01-13
> **bkline said:**
> Did someone leave out a dependency check in the packaging?

Still broken, 8 months later, on Karmic with TG 1.0.8-2ubuntu1.  Anybody home?

---

### Post by bkline on 2010-05-03
Still broken in Ubuntu 10.4.  Hello?

---

