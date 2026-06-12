---
title: "remove python"
date: 2009-02-12
forum: General Help
---

### Post by djbushido on 2009-02-12
I am wanting to remove python 2.6 on my system. I already have 2.5, and want to downgrade for dependency problems. If you can help, thanks a lot.

---

### Post by djbushido on 2009-02-14
okay, to fix the problem i removed the python and python2.6 executables, and replace these (also python-config) with the python2.5 and python2.5-config files, and voila, it works.

---

### Post by ch0d3 on 2009-02-14
> **djbushido said:**
> okay, to fix the problem i removed the python and python2.6 executables, and replace these (also python-config) with the python2.5 and python2.5-config files, and voila, it works.

apt-get remove or apt-get --purge remove should work as well

Edit: I suppose you would still have to configure your python environment manually though

---

### Post by djbushido on 2009-02-15
Yes, $PYTHONPATH would get set wrong. Also, the problem is that doing make install doesn't register this with apt-get. You would have to create a debian and then install it from that. So the above way is the only way to work. Make uninstall doesn't work either.

---

### Post by zdmytriv on 2009-06-23
apt-get remove doesn't work. It's trying to remove all the depencies ~ 50 packages with python 2.6

---

### Post by blackxored on 2009-06-23
which ubuntu version did you said you're using?

---

### Post by Martin Witte on 2009-06-23
Don't remove python 2.6, as a lot of other core packages rely on it. On my system 2.5 is also installed, just invoke as
```
martin@sony:~$ python2.5
Python 2.5.4 (r254:67916, Apr  4 2009, 17:55:16) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

---

### Post by fiveacez on 2009-06-23
> **Martin Witte said:**
> Don't remove python 2.6, as a lot of other core packages rely on it. On my system 2.5 is also installed, just invoke as
```
martin@sony:~$ python2.5
Python 2.5.4 (r254:67916, Apr  4 2009, 17:55:16) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

The problem with this is when you want to install something, like pysqlite, it will install in the 2.6 directory instead of 2.5.  BIG issue for me.

---

### Post by djbushido on 2009-06-24
Okay, so basically, you can't remove a version of python. To downgrade, remove the python executable in /usr/bin and re-link to whichever version you want - the program "ln" is what you need to look up. Don't remember the syntax off hand. But only do this if it is absolutely necessary, as it could very well screw up a lot of your system.

---

