---
title: "corrupt file?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by WildTangent on 2005-12-04
OK, so whenever I install or remove a program, dpkg gives me an error, for the same two packages everytime, citing the same problem. These packages are language-selector, and serpentine. It tells me everytime that it cannot access a specific file. I think a screenshot will explain better, please see the attached picture.

Basically...I think this file is corrupt, and I don't know how to fix it. If someone could tell me how to replace it or whatever, it would be greatly appreciated.

-Wild

---

### Post by az on 2005-12-04
Can you delete it?  

No.  That will not bork the removal of the package.  I would not reccommend you run the program, though.

---

### Post by amohanty on 2005-12-04
In a terminal:

```

cd /usr/lib/python2.4/site-packages
sudo rm -rf DiscID.pyo
sudo python

```

now in the the python interpreter:

```

aseem@kandinsky:~$ python
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import py_compile
>>> py_compile.compile("DiscID.py")

```

This should regenerate the DiscID.pyo file.

HTH
AM

---

### Post by WildTangent on 2005-12-04
I can't delete it:
```
>>> py_compile.compile("DiscID.pyo")
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/usr/lib/python2.4/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 13] Permission denied: 'DiscID.pyo'

```

-Wild

---

### Post by amohanty on 2005-12-04
did you do an :
```
sudo python
```

_not_
```
python
```

---

### Post by WildTangent on 2005-12-04
[QUOTE=amohanty]did you do an :
```
sudo python
```

_not_
```
python
```[/QUOTE]
I did sudo python...no dice.

EDIT: Tried again:
```
justin@chimera:~$ cd /usr/lib/python2.4/site-packages
justin@chimera:/usr/lib/python2.4/site-packages$ sudo rm -rf DiskID.pyo
Password:
justin@chimera:/usr/lib/python2.4/site-packages$ sudo python
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import py_compile
>>> py_compile.compile("DiskID.pyo")
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "/usr/lib/python2.4/py_compile.py", line 115, in compile
    f = open(file, 'U')
IOError: [Errno 2] No such file or directory: 'DiskID.pyo'

```

When I browse to its location with Nautilus, it's still there, and still corrupted.

-Wild

---

### Post by amohanty on 2005-12-04
Can you do the following:

```
rm -rf /usr/lib/python2.4/site-packages/DiscID.pyo
```

AM

---

### Post by WildTangent on 2005-12-04
```
justin@chimera:~$ sudo rm -rf /usr/lib/python2.4/site-packages/DiscID.pyo
rm: cannot remove `/usr/lib/python2.4/site-packages/DiscID.pyo': Permission denied
justin@chimera:~$

```

EDIT: Can't even do it as root:
```
justin@chimera:~$ su
Password:
root@chimera:/home/justin# rm -rf /usr/lib/python2.4/site-packages/DiscID.pyo
rm: cannot remove `/usr/lib/python2.4/site-packages/DiscID.pyo': Permission denied
root@chimera:/home/justin#

```

-Wild

---

### Post by amohanty on 2005-12-04
The next thing to try would be to drop into the recovery console and try and delete it. If that doesnt work either then use a Live CD to delete it.

Kind of strange that it wouldnt let you delete the file.

Try the above and let us know how it goes.

AM

---

### Post by wgrant on 2005-12-04
[QUOTE=amohanty]Can you do the following:

```
rm -rf /usr/lib/python2.4/site-packages/DiscID.pyo
```

AM[/QUOTE]

WHY are you using -r!!?? Recursive on a file isn't going to do anything! A recursive, forced, super-user delete operation is a dangerous thing... Just a couple of stuffed up characters can send your system to an oblivion. Best to leave out the -r!

I still remember the time when there were a number of . files in a directory, and I ran 'sudo rm -rf .*'. The system rather rapidly vanished! I have not done that in quite a few years now, thankfully.

William.

---

### Post by amohanty on 2005-12-04
Sorry about that.

---

### Post by wgrant on 2005-12-04
OK. I just didn't want somebody to be taught that that was the proper method of deleting a file... As I said, it can be _extremely_ dangerous.

William.

---

