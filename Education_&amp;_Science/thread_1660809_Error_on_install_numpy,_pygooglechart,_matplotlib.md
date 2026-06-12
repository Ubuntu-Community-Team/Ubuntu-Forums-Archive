---
title: "Error on install numpy, pygooglechart, matplotlib"
date: 2011-01-05
forum: Education &amp; Science
---

### Post by Tlingit on 2011-01-05
I have been trying to install several API's for plotting in python and I get the same error every time. It seams I cant get Numpy to install.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-pygooglechart is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic libopenmpi1.3 linux-headers-2.6.35-22
  libnuma1 libibverbs1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-dateutil (1.4.1-3) ...
  File "/usr/sbin/update-python-modules", line 52
    print x
          ^
SyntaxError: invalid syntax
dpkg: error processing python-dateutil (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-graphy (1.0+dfsg-1ubuntu1) ...
  File "/usr/sbin/update-python-modules", line 52
    print x
          ^
SyntaxError: invalid syntax
dpkg: error processing python-graphy (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-numpy (1:1.3.0-3build1) ...
  File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-pyparsing (1.5.2-2) ...
  File "/usr/sbin/update-python-modules", line 52
    print x
          ^
SyntaxError: invalid syntax
dpkg: error processing python-pyparsing (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-tz (2010b-1) ...
No apport report written because MaxReports is reached already
                                                                File "/usr/bin/pycentral", line 87
    raise ValueError, 'unknown version info %s' % vinfo
                    ^
SyntaxError: invalid syntax
dpkg: error processing python-tz (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-matplotlib:
 python-matplotlib depends on python-dateutil; however:
  Package python-dateutil is not configured yet.
 python-matplotlib depends on python-numpy (>= 1:1.3.0); however:
  Package python-numpy is not configured yet.
 python-matplotlib depends on python-pyparsing; however:
  Package python-pyparsing is not configured yet.
 python-matplotlib depends on python-tz; however:
  Package python-tz is not configured yet.
dpkg: error processing python-matplotlib (--configure):
 dependency problems - leaving unconfigured
Setting up python-pygooglechart (0.2.1-2) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                  File "/usr/sbin/update-python-modules", line 52
    print x
          ^
SyntaxError: invalid syntax
dpkg: error processing python-pygooglechart (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-matplotlib-dbg:
 python-matplotlib-dbg depends on python-matplotlib (= 0.99.3-1ubuntu1); however:
  Package python-matplotlib is not configured yet.
dpkg: error processing python-matplotlib-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-numpy-dbg:
 python-numpy-dbg depends on python-numpy (= 1:1.3.0-3build1); however:
  Package python-numpy is not configured yet.
dpkg: error processing python-numpy-dbg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                                  Errors were encountered while processing:
 python-dateutil
 python-graphy
 python-numpy
 python-pyparsing
 python-tz
 python-matplotlib
 python-pygooglechart
 python-matplotlib-dbg
 python-numpy-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



I get this every time i try to install any external graphing API's for python.

In case this matters

```
Linux box 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

```

---

### Post by prince_sabin on 2011-01-05
What version of python do you have?

the output of this:

ls -l $(which python)

The "print x" stuff is different in 3.0 it's now a function

you may need python 2.X.

---

### Post by Sef on 2011-01-06
Moved to Education and Science.  This subforum has a number of threads on this subject.

---

### Post by Tlingit on 2011-01-06
Python 3.1, and thank you for moving it I have tried to look thank you for showing me.

and thank you for pointing out my problem.

---

### Post by Vox754 on 2011-01-06
> **Tlingit said:**
> Python 3.1, and thank you for moving it I have tried to look thank you for showing me.

and thank you for pointing out my problem.

As you can see, some very useful libraries have not yet been ported to Python 3. Therefore, the only sensible solution at this point is to avoid Python 3, and stick to the good ole Python 2.

The Numpy FAQ mentions that [they expected a first release of Numpy for Python 3 by mid 2010.](http://new.scipy.org/faq.html#python-version-support) It seems they were too optimistic about that. Perhaps wait another year.

---

