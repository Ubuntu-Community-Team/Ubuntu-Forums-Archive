---
title: "Problem with screenlets and Beryl"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by searayman on 2007-06-11
Well i dont think the problem has much to do with beryl but it is what i am using for composite.

anywho i get this erro rwhen tryign to run screenlets...

mike@mike-desktop:~$ screenlets-tray
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
CachingBackend: Loading cache ...
Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 493, in <module>
    service = ScreenletsService(bus_name)
  File "/usr/local/share/screenlets/screenletsd.py", line 247, in __init__
    self.load_session()
  File "/usr/local/share/screenlets/screenletsd.py", line 317, in load_session
    classname = data[1].replace("\n", "")
IndexError: list index out of range




please help!!!

---

