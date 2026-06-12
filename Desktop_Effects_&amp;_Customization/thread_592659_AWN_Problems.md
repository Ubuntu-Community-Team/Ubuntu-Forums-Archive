---
title: "AWN Problems"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by j00j07 on 2007-10-26
Well I installed AWN with [this tutorial]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator")and went to System >> Preferences >> AWN Manager ... when I click on it nothing happens ... any suggestions ?:confused:

---

### Post by j00j07 on 2007-10-26
Also when I go to the terminal and type ```
awn-manager
``` this is what i I get

```
joey@joey-laptop:~$ awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:182: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 162, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 182, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue

```

---

### Post by andrewsomething on 2007-10-26
> **j00j07 said:**
> Well I installed AWN with [this tutorial]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator")and went to System >> Preferences >> AWN Manager ... when I click on it nothing happens ... any suggestions ?:confused:

For some reason, awn-manager will not run unless you run AWN at least once first. AWN should be listed under accessories, but if it isn't for some reason press Alt-F2 and run "avant-window-navigator"

---

### Post by j00j07 on 2007-10-26
Thanks !! IT WORKED !!

---

