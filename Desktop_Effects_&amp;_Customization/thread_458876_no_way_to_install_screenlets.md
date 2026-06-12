---
title: "no way to install screenlets"
date: 2007-05-30
forum: Desktop Effects &amp; Customization
---

### Post by djibi on 2007-05-30
Hi, this is the error that I've when i try to run screenlets:

$ screenlets-tray
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
CachingBackend: Loading cache ...
CachingBackend: Loading <s3kj8t0HrmXfQmtO>
Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 493, in <module>
    service = ScreenletsService(bus_name)
  File "/usr/local/share/screenlets/screenletsd.py", line 247, in __init__
    self.load_session()
  File "/usr/local/share/screenlets/screenletsd.py", line 317, in load_session
    classname = data[1].replace("\n", "")
IndexError: list index out of range

If i try to add a control screenlet, it gave me this:

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Screenletsd is not running - cannot add screenlet.

I don't understand why screenletsd don't run.. I have the tray icon...

thanks for the help

---

### Post by Kobalt on 2007-05-30
Do you have Beryl or Compiz running ?

---

### Post by djibi on 2007-05-31
Hi, 
I've Beryl and emerald...

---

### Post by djibi on 2007-06-03
someone can help me?

---

### Post by djibi on 2007-06-08
nobody?:D

---

