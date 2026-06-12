---
title: "FVWM missing debian menu"
date: 2010-02-13
forum: Desktop Environments
---

### Post by AudioDef on 2010-02-13
I just installed FVWM-Crystal and there's naught but a paltry menu. My understanding is that there should be a full menu of installed programs on my system. Running update-menus changes nothing. My Xfce installation has it all. 

What gives?

---

### Post by jpkotta on 2010-02-21
[https://help.ubuntu.com/community/FVWM](https://help.ubuntu.com/community/FVWM) (in the Integration section)

---

### Post by hollerith on 2010-03-03
The application panel menus are missing because 

SyntaxError: invalid syntax
  File "/usr/local/bin/fvwm-crystal.apps", line 209
    def getAppsData(databases=[database],checkExecs=False,searchIconsIn='',sortOrder='prio',minLength=3,with=None,without=None,rootName='/Applications',topInSub=True,fileIcon='default.png',dirIcon='directory.png'):

'with' is a reserved word in python 2.6 and therefore not allowed as a variable.  Fix this, get menus.

---

