---
title: "Avant Window Navigator Problems"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by razeshkale on 2007-11-10
I installed AWN but i couldnot open It.
I followed theread for THr [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
Doesn't help at all
I tried with Terminal But i get some Error Like THis..



root@rasa-laptop:~# awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:183: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 165, in __init__
    self.setup_color(TITLE_BACKGROUND, self.wTree.get_widget("backgroundcolor"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 183, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/background isn't set.
Restarting AWN usually solves this issue


Does anyone has same Problem......

---

### Post by rapiddl on 2007-11-11
Avant-manager is to setup the config of ur avant panel instead try calling up "avant-windows-navigator" that should do the trick then u should be able to call up "avant-manager" using the terminal or even call it thru the avant panel.
Hope it helps i just installed it yday with the curve its brill much better than kiba-dock alot more stable. :guitar:

---

