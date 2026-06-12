---
title: "Error Trying To Run Cedega"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by OffHand on 2006-07-16
Hi
I have already managed to get Cedega running on this machine but 'cause of problems with getting Guild Wars to work I tried re-installing it.
Problem now is even Cedega doesn't want to start anymore. I get the following error when I try run it from terminal:

:~$ cedega
The Cedega version (5.2) you are defaulting to is missing the following file : c onfig
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2898, in ?
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file, alt ernate_configs ) )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 520, in __init__
    self.match_and_copy_default_cedega_profiles()
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 1967, in match_and_copy _default_cedega_profiles
    log.logger.info("self.current_default_cedega_profile now == " + self.current _default_cedega_profile)
TypeError: cannot concatenate 'str' and 'NoneType' objects


Does anyone know how I can fix this?


:~$ whereis cedega
cedega: /usr/bin/cedega /usr/bin/X11/cedega /usr/share/man/man1/cedega.1.gz

---

### Post by OffHand on 2006-07-16
```
rm ~/.cedegarc
```
worked

---

