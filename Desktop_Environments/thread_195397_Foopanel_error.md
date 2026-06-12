---
title: "Foopanel error"
date: 2006-06-12
forum: Desktop Environments
---

### Post by setenza on 2006-06-12
Hi,

I have downloaded the last version of foopanel. Compiled and when i start ./foopanel i have many error's :

> 
Loading theme SolidBlue
Traceback (most recent call last):
  File "/usr/bin/foopanel", line 37, in ?
    foopanel.run()
  File "/usr/lib/python2.4/site-packages/foopanel/__init__.py", line 84, in run
    gui = core.Gui()
  File "/usr/lib/python2.4/site-packages/foopanel/lib/core.py", line 115, in __init__
    self.set_keep_above( bool( int(globals.config.ontop) ) )
ValueError: invalid literal for int(): True




Any idea ?

---

