---
title: "gdesklets problem in 10.04 version"
date: 2010-04-30
forum: Desktop Environments
---

### Post by MaxTub on 2010-04-30
I can not run gdesklets in ubuntu 10.04. 
When I do gdesklets check I got this message:

ERROR:/build/buildd/pyorbit-2.24.0/src/pyorbit-utils.c:39:_pyorbit_escape_name:  assertion failed: (keyword_mod != NULL)
 - ORBit ...Aborted

---

### Post by mister_p_1998 on 2010-04-30
Its fixed here (sort of, going back to previous version)

[http://ubuntuforums.org/showthread.php?t=1454324](http://ubuntuforums.org/showthread.php?t=1454324)

Steve

---

### Post by ghimus on 2010-11-30
I don't have a solution, just an alternative:
[http://www.screenlets.org/](http://www.screenlets.org/)

---

### Post by jeffsa12 on 2011-03-05
Fix gdesklets in ubuntu 10.04 / Linux Mint 9.0 

A simple edit is all thats necessary. Here's the fix!

1) gksu nautilus in terminal
2) go to  /usr/lib/gdesklets/utils/ErrorFormatter.py
3) open the above file with gedit gksu mode
4) edit as follows:

change this line 
```
def _new_imp(name, globs = {}, locls = {}, fromlist = []):
```

to this 
```
def _new_imp(name, globs = {}, locls = {}, fromlist = [], test = []):
```

Then save the changes.

---

### Post by hellonearth on 2011-04-13
Thanks _it works for me !!!:popcorn:_

---

