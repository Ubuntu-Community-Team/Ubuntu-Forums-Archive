---
title: "checking if a package is installed via command line"
date: 2009-01-02
forum: General Help
---

### Post by BattlePanic on 2009-01-02
Is there a command I can use to check if a given package is installed on my system?  I have been using apt-cache to look up package info but it doesn't seem to tell me whether or not a given package is installed.  Thanks for any tips.

---

### Post by dagnabit dang doohickey on 2009-01-02
I have a habit of doing:
```
aptitude show *package*
```(I do *aptitude shoe [I]package*[/I] a whole bunch too. ;))

But, the [whereis]("http://linux.die.net/man/1/whereis") command may be what you want.

---

### Post by Loosewheel on 2009-01-02
> **BattlePanic said:**
> Is there a command I can use to check if a given package is installed on my system?  I have been using apt-cache to look up package info but it doesn't seem to tell me whether or not a given package is installed.  Thanks for any tips.

Hi BattlePanic,
Maybe this will do it...
dpkg -l *<search_term>*

This will find packages whose names contain <search_term>. Similar to apt-cache search, but also shows whether a package is installed on your system by marking it with ii (installed) and un (not installed).

---

### Post by jerome1232 on 2009-01-02
> **BattlePanic said:**
> Is there a command I can use to check if a given package is installed on my system?  I have been using apt-cache to look up package info but it doesn't seem to tell me whether or not a given package is installed.  Thanks for any tips.


This will show the verision installed (or it will say it's not installed)
It will show what version is in the cache (the version that would be installed if you were to install it, or to update to if you do an upgrade)
it also shows which repo it's coming from
```
apt-cache policy *packagename*
```

---

