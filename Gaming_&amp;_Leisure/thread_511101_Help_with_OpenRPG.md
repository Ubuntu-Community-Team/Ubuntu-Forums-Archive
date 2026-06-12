---
title: "Help with OpenRPG"
date: 2007-07-27
forum: Gaming &amp; Leisure
---

### Post by Pzkpfw on 2007-07-27
So I downloaded OpenRPG, it ran fine for some time, then after closing it, it won't start anymore and displays this error:
```
Rooting OpenRPG at: /home/crashed/openrpg1
'NoneType' object is not iterable
Traceback (most recent call last):
  File "start.py", line 12, in <module>
    app = orpg.tools.updater.updateApp(0)
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7757, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7354, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/home/crashed/openrpg1/orpg/tools/updater.py", line 418, in OnInit
    self.settings = orpg.tools.orpg_settings.orpgSettings(self.openrpg)
  File "/home/crashed/openrpg1/orpg/tools/orpg_settings.py", line 46, in __init__
    self.xml_dom = self.xml.parseXml(txt)._get_documentElement()
AttributeError: 'NoneType' object has no attribute '_get_documentElement'
 
```

I asked around in OpenRPG forums and they said that the program can't read settings.xml file, which in my case wasn't even being created, and that i should check my permissions, but chmodding the whole directory to 777 didn't help (and after all, it ran fine before), reinstalling it didn't help either, even getting a friend to send me his copy with all the settings didn't do any good too. I'd be very thankful if anyone could help me with this.

---

### Post by HunterRose on 2007-11-12
```
>	python2.5: can't open file 'start.py': [Errno 2] No such file or directory
hunterrose@HunterRose:~$ openrpg-client
/usr/share/openrpg/orpg/plugins.py:1: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained. Please switch to the wx package as soon as possible.
from wxPython.wx import *
Rooting OpenRPG at: /usr/share/openrpg
[WARNING] Could not create approot file.
[WARNING] Automatic directory resolution not configured.
Traceback (most recent call last):
File "./start.py", line 6, in <module>
import orpg.main
File "/usr/share/openrpg/orpg/main.py", line 35, in <module>
from orpg.orpg_windows import *
File "/usr/share/openrpg/orpg/orpg_windows.py", line 43, in <module>
from wxPython.html import *
File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/html.py", line 151, in <module>
wxHtmlWindowEvent = wx.html.HtmlWindowEvent
AttributeError: 'module' object has no attribute 'HtmlWindowEvent'
```
I am having that problem too :-(

---

### Post by basotl on 2007-12-19
I am having a similar issue.

```
/usr/share/openrpg/orpg/plugins.py:1: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import *
Rooting OpenRPG at: /usr/share/openrpg
Traceback (most recent call last):
  File "./start.py", line 6, in <module>
    import orpg.main
  File "/usr/share/openrpg/orpg/main.py", line 35, in <module>
    from orpg.orpg_windows import *
  File "/usr/share/openrpg/orpg/orpg_windows.py", line 43, in <module>
    from wxPython.html import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/html.py", line 151, in <module>
    wxHtmlWindowEvent = wx.html.HtmlWindowEvent
AttributeError: 'module' object has no attribute 'HtmlWindowEvent'

```

Has anyone found a way to fix this? I've been trying at it and I know I must be missing something simple.

---

### Post by basotl on 2007-12-19
I just had to use the more up to date package from the [unofficial download site]("http://openrpg.digitalxero.net/wiki/").

I guess the issue was addressed but the package at Sourceforge hasn't been updated.

---

