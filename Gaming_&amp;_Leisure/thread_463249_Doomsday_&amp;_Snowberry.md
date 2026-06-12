---
title: "Doomsday &amp; Snowberry"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by tribunal on 2007-06-03
I have a problem. Downloaded Doomsday and Snowberry
Compiled Doomsday (had to find CMakeLists.txt!)
And.. snowberry doesn't start :(

Here is its:

Traceback (most recent call last):
  File "./snowberry.py", line 26, in <module>
    import language, ui, plugins, sb.profdb
  File "/home/kolya/Share/src/deng-1.9.0-beta5.1/snowberry/ui.py", line 698, in <module>
    app = SnowberryApp()
  File "/home/kolya/Share/src/deng-1.9.0-beta5.1/snowberry/ui.py", line 536, in __init__
    wx.App.__init__(self, 0)
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/home/kolya/Share/src/deng-1.9.0-beta5.1/snowberry/ui.py", line 540, in OnInit
    self.mainFrame = MainFrame('Snowberry')
  File "/home/kolya/Share/src/deng-1.9.0-beta5.1/snowberry/ui.py", line 290, in __init__
    self.mainPanel = MainPanel(self.profSplitter)
  File "/home/kolya/Share/src/deng-1.9.0-beta5.1/snowberry/ui.py", line 166, in __init__
    area.addSpacer()
  File "/home/kolya/Share/src/deng-1.9.0-beta5.1/snowberry/sb/widget/area.py", line 197, in addSpacer
    self.containerSizer.AddStretchSpacer(self.weight)
AttributeError: 'BoxSizer' object has no attribute 'AddStretchSpacer'

What is wrong? :(

---

### Post by tribunal on 2007-06-04
Boom!
Did anyone have success in  starting snowberry under (K)Ubuntu 7.04?
Forum at doomsday's site is closed for registration :( And I don't know, where I can ask...

---

### Post by KuriKai on 2007-06-04
[http://dengine.net/dew/index.php?title=Installation#Linux.2FUnix](http://dengine.net/dew/index.php?title=Installation#Linux.2FUnix)
This is how to get it working

---

