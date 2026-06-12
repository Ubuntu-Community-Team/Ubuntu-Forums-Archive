---
title: "Is your emesene slow?"
date: 2007-11-08
forum: Desktop Environments
---

### Post by nurv on 2007-11-08
Hi there!

From time to time, i notice that emesene does became slow, or unresponsive. 

After searching for a while, i discovered that emesene is not byte compiled, witch can cause your system slow down emesene.

If you use the deb in :

```
deb http://apt.emesene.org/ ./
deb-src http://apt.emesene.org/ ./

```

then most likely you are using a uncompiled version. 

To repair this, go to /usr/share/ and run:

```
 sudo python
```

Next, within the python interactive shell run this:

```

include compileall
compileall.compile_dir("emesene", force=1)

```

This will recursively search compile you files. After this, your emesene will be quite faster!

PS: Sory, now corrected

---

### Post by zealot_mg on 2007-11-12
hello,  my emesene slows down sometimes and becomes unresponsive, i tried these steps but ....

luis@luis-laptop:~$ cd /usr/share/
luis@luis-laptop:/usr/share$ sudo python
Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> include complieall
  File "<stdin>", line 1
    include complieall
                     ^
SyntaxError: invalid syntax
>>> 


.......
please help i really need to fix this thing, its really anoying u.u
thanks in advance

---

### Post by nurv on 2007-11-13
Small typo, its now correct.

---

### Post by zealot_mg on 2007-11-13
luis@luis-laptop:/usr/share$ sudo python
Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> include compileall
  File "<stdin>", line 1
    include compileall
                     ^
SyntaxError: invalid syntax
>>> compileall.compile_dir("emesene", force=1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'compileall' is not defined


.... sorry if im making something wrong... but i get this error message =s

EDIT: ok i did it, instead of include, used import.. and then everything went ok...
im gonna use emesene now to view the changes

---

