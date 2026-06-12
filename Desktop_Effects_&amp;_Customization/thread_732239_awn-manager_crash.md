---
title: "awn-manager crash?"
date: 2008-03-22
forum: Desktop Effects &amp; Customization
---

### Post by meph on 2008-03-22
Pardon my ignorance but  i broke my awn-manager somehow and i can't fix it. I tried reinstalling and all that jazz but not very successful.
The actual avant-window-navigator works just fine but everytime i try to change some settings it doesn't work.

```
~$ awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 95, in __init__
    self.appletManager = awnApplet(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnApplet.py", line 78, in __init__
    self.load_applets()
  File "/usr/share/avant-window-navigator/awn-manager/awnApplet.py", line 466, in load_applets
    icon, text = self.make_row (a)
  File "/usr/share/avant-window-navigator/awn-manager/awnApplet.py", line 361, in make_row
    return self.make_icon (item.get_string(gnomedesktop.KEY_ICON)), text
  File "/usr/share/avant-window-navigator/awn-manager/awnApplet.py", line 380, in make_icon
    if "/" in name and os.path.exists(name):
TypeError: argument of type 'NoneType' is not iterable

``` 

Please bare with me i'm a newBie!

---

