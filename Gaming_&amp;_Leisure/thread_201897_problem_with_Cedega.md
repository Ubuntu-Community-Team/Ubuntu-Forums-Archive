---
title: "problem with Cedega"
date: 2006-06-22
forum: Gaming &amp; Leisure
---

### Post by Paool on 2006-06-22
When I run Cedega I've this error... And I don't what to do :/ Any ideas?

paool@korytko:~$ cedega
The Cedega version (5.2) you are defaulting to is missing the following file : config
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2898, in ?
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file, alternate_configs ) )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 520, in __init__
    self.match_and_copy_default_cedega_profiles()
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 1967, in match_and_copy_default_cedega_profiles
    log.logger.info("self.current_default_cedega_profile now == " + self.current_default_cedega_profile)
TypeError: cannot concatenate 'str' and 'NoneType' objects
paool@korytko:~$

---

### Post by GQed76 on 2006-06-22
Redownload it?  There is an option in the menu to redownload it.

---

### Post by Paool on 2006-06-22
which menu? Cedega don't start at all :) I've tried reinstall package and remove ~/.cedega directory but it doesn't change anything...

---

### Post by keithjr on 2006-06-23
Have you tried posting on the transgaming forums?  This seems like a straight-up code error, perhaps a missing header or dependency?  Check the linux-gamers.com howto for the libraries you should have.

---

