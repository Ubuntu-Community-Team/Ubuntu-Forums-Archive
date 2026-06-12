---
title: "Gmailfs on ubuntu"
date: 2006-06-12
forum: Desktop Environments
---

### Post by pratzabrat on 2006-06-12
I am currently working on a web designing project. Constant use of Macromedia Flash is necessary so I use windows (only when necessary). But when on ubuntu I feel the constant need to update some of the html files. Gmailfs gives the right sort of solution. However I dint find any ubuntu howto on it (There is one on Gentoo's site). Also the default package gmailfs doesnt seem to work fine. 

I get the following error while mounting gmailfs :
> Ignored option :rw
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 159, in ?
    import gmailfs
  File "/usr/local/bin/gmailfs.py", line 29, in ?
    from lgconstants import *
ImportError: No module named lgconstants

---

### Post by asimon on 2006-06-12
Yes, gmailfs is utterly broken on Ubuntu, see [bug #31223](https://launchpad.net/distros/ubuntu/+source/gmailfs/+bug/31223). Maybe it works if you install the current [gmailfs](http://packages.debian.org/unstable/utils/gmailfs) and [python-libgmail](http://packages.debian.org/unstable/python/python-libgmail) packages from Debian. If you need/want gmailfs it's surely worth a try.

---

### Post by fortran01 on 2006-09-09
> **pratzabrat said:**
> I get the following error while mounting gmailfs:

```
Ignored option :rw
Traceback (most recent call last):
File "/sbin/mount.gmailfs", line 159, in ?
import gmailfs
File "/usr/local/bin/gmailfs.py", line 29, in ?
from lgconstants import *
ImportError: No module named lgconstants
```

Try copying lgconstants.py to the folder where your gmailfs.py is located. lgconstants.py is a file also used by libgmail. You can get the lgconstants.py from the libgmail source package (ie from sourceforge).

---

