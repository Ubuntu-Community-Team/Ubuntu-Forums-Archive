---
title: "Nicotine broken?"
date: 2005-12-15
forum: General Help
---

### Post by snae on 2005-12-15
Hi Folks,

Today, on starting nicotine I get the following:

Traceback (most recent call last):
  File "/usr/bin/nicotine", line 146, in ?
    app = frame.MainApp(config)
  File "/usr/lib/site-python/pynicotine/gtkgui/frame.py", line 933, in __init__
    self.frame = testwin(config)
  File "/usr/lib/site-python/pynicotine/gtkgui/frame.py", line 246, in __init__
    if self.np.config.needConfig():
  File "/usr/lib/site-python/pynicotine/config.py", line 83, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc'):
  File "/usr/lib/python2.4/UserDict.py", line 168, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.4/UserDict.py", line 100, in iteritems
    for k in self:
  File "/usr/lib/python2.4/UserDict.py", line 87, in __iter__
    for k in self.keys():
  File "/usr/lib/python2.4/shelve.py", line 98, in keys
    return self.dict.keys()
  File "/usr/lib/python2.4/bsddb/__init__.py", line 238, in keys
    return self.db.keys()
bsddb._db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')

Is anyone else getting this issue?  Has Python been updated recently to have caused this - I have not noticed in my list of updates (but then sometimes just update anyway and don't look, bad form I know...)

TIA

---

### Post by bored2k on 2005-12-15
Download teh latest (2.6) wxpython and libwxgtk2.6-0 and use the source on [http://nicotine.thegraveyard.org/](http://nicotine.thegraveyard.org/) .

---

