---
title: "Icepodder in Ubuntu Lucid, no downloads!"
date: 2010-04-26
forum: Desktop Environments
---

### Post by mister_p_1998 on 2010-04-26
Did an upgrade to Ubuntu Lucid last week, everything works ok apart from Icepodder, which runs but gives the following errors:

Scanning...
Uncaught exception!
Traceback (most recent call last):
File "/usr/share/icepodder/ipodder/core.py", line 1116, in start
self.scanenclosures(mask,catchup)
File "/usr/share/icepodder/ipodder/core.py", line 561, in scanenclosures
self.scanner = scanner = engine.Engine(mw)
File "/usr/share/icepodder/ipodder/engine.py", line 114, in __init__
threads.OurThread.__init__(self, **kwargs)
File "/usr/share/icepodder/ipodder/threads.py", line 95, in __init__
self.name = kw.get('name')
File "/usr/lib/python2.6/threading.py", line 669, in name
assert self.__initialized, "Thread.__init__() not called"
AssertionError: Thread.__init__() not called

Is it a python thing?
missing my podcasts!!
Help!

Steve

---

