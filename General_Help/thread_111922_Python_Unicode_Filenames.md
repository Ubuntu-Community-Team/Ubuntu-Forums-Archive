---
title: "Python Unicode Filenames"
date: 2006-01-03
forum: General Help
---

### Post by xcolour on 2006-01-03
Does anyone know if ubuntu's python supports unicode filenames?  Specifically, what does os.path.supports_unicode_filenames return?  Does it have to be explicitly enabled at compile time, or is it just platform dependent?  I've had trouble with unicode filenames in python on systems that I know support them.

---

### Post by steve.horsley on 2006-01-03
steve@dingly:~$ python
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.path.supports_unicode_filenames
False
>>>

---

