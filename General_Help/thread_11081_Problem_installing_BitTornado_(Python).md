---
title: "Problem installing BitTornado (Python)"
date: 2005-01-13
forum: General Help
---

### Post by Hikaru79 on 2005-01-13
I'm trying to install BitTornado. I DO have python and I DO have wxpython2.5.3. However, this happens:

```
hikaru79@ubuntu:~/BitTornado-CVS $ python setup.py install
running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

```

But, when I try 
```
hikaru79@ubuntu:~/BitTornado-CVS $ python -V
Python 2.4

```
It find Python no problem, so why doesn't the installer?... any ideas? =/

NOTE: On a previous Ubuntu install, when I used GNOME, all worked fine. I've reinstalled Ubuntu, switched to Hoary, switched to KDE 3.3.2 and now it doesn't :( Could this be the problem? Hoary's unstability?

---

### Post by Waylan on 2005-08-21
I realize this thread is a few months old, but it has not been resolved (that I can see) and I am having the exact same problem with any Python Module I try to install.

The only diffirence would be that I'm using a standard install of Ubuntu.

---

