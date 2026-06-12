---
title: "AWN Manager won't start."
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by harsh2209 on 2007-10-26
Hi Friends,

I followed the wiki - 'http://wiki.awn-project.org/index.php?title=DistributionGuides' to install AWN. Installtion had no errors, Upon clicking AWN manager from Preferences, it doesn't start. In terminal I execute a command $ awn-manager and get the following:-

awn-manager
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


----Any comments?

---

### Post by slymi2005 on 2007-10-26
Did you upgrade from 7.04 to 7.10 because someone told be that if you upgrade to gutsy it wont work, apparently you have to do a fresh install. lame.

---

### Post by seanhvw on 2007-10-27
Having same issue running 7.10 beta with latest updates. Do I have to do a clean install or is there a fix?

---

### Post by harsh2209 on 2007-10-27
No, its a clean install of latest 7.10.

---

### Post by MoRtYMer on 2007-10-27
Well i've updated from 7.04 to 7.10 and installed it after and its working.

---

### Post by jfal on 2007-10-28
I was having this same issue in Gutsy.  Make sure you have actually started Avant Window Navigator from Applications > Accessories > Avant Window Navigator.  Once it is running you can then startup AWN Manager.  

Good luck.

---

### Post by cpgktm on 2007-10-28
thanks jfal, that was my problem all along. i never started the avant window navigator :)

---

