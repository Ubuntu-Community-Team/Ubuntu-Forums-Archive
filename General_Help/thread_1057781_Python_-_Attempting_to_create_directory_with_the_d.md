---
title: "Python - Attempting to create directory with the date as the name"
date: 2009-02-02
forum: General Help
---

### Post by chrismyers on 2009-02-02
Hi guys,

I am beginner trying to use Python to create a directory where today's date is the name.

This is what I have done so far:

```
#!/usr/bin/python
import time, datetime, os

today = datetime.date.today()
os.mkdir(today)
```This isn't working for me. I get the error:

TypeError: coercing to Unicode: need string or buffer, datetime.date found

I have googled for the above phrase & also using keywords Python, unicode, date, but I have not found anything useful.

Can anyone help please?

---

### Post by niteshifter on 2009-02-02
Hi,

Try this:
```
#!/usr/bin/python
import time, datetime, os

today = datetime.date.today()  # get today's date as a datetime **type**

todaystr = today.isoformat()   # get string representation: YYYY-MM-DD
                               # from a datetime type.

os.mkdir(todaystr)

```

Hint: When things don't work as you expect they should in Python the keyword **type** can save a lot of frustration. Example:

```
Python 2.5.1 (r251:54863, Jul 31 2008, 23:17:40) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import time, datetime, os
>>> today = datetime.date.today()
>>> os.mkdir(today)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: coercing to Unicode: need string or buffer, datetime.date found
>>> **type(today)**
<type 'datetime.date'>
>>> todaystr = today.isoformat()
>>> **type(todaystr)**
<type 'str'>
>>> print todaystr
2009-02-02
>>> 

```

---

### Post by chrismyers on 2009-02-02
Many thanks niteshifter. That's just what I needed. Thanks for the 'type' tip as well.

:-)

---

