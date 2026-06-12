---
title: "When I gonna update ubuntu 8.10 it gives following error please help me to solve this"
date: 2009-02-07
forum: General Help
---

### Post by ravindukelum on 2009-02-07
```
kelum@ravindu-laptop:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

Then I tried ```
sudo dpkg --configure -a

```

Then it gives message like

```
Setting up python-simplejson (1.9.1-1) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: Trying to overwrite simplejson/encoder.py which is already provided by /usr/share/python-support/lanshark
dpkg: error processing python-simplejson (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

```


Please help me to solve this problem now I can not upgrade my Ubuntu or install any software

---

### Post by Svensk023 on 2009-02-07
Try downloading the .iso and fresh install from a disk, it is alot less problematic that way.

---

### Post by hikaricore on 2009-02-07
I don't think the user is trying to update to a new revision, but is instead trying to update packages in his current version.

Have you installed any third party software by chance?

---

### Post by ravindukelum on 2009-02-07
Thanks for your interest ,yep I have installed So many software,
But I don't want to fresh install again because it coast me so much of money and time for Internet please anybody know to solve this problem?

---

