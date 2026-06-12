---
title: "AWN Trouble"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by Ox1GeN on 2007-10-14
I have trouble with AWN..
I'm trying to start up AWN manager and i'm getting:
```
humble@humble-desktop:~$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:182: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 162, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 182, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue

```
I'm on the Gutsy Gibbon RC.
Help plz!

---

### Post by vhex on 2007-10-16
Open gconf-editor, go to /apps/avant-window-navigator/title and make sure that text_color is an 8-character hexadecimal number.  I had "~" there, and awn-manager wouldn't start.  Changed it to 00000000, now everything's fine.

---

