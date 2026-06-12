---
title: "Orange available on Repo ?"
date: 2010-08-22
forum: Education &amp; Science
---

### Post by satimis on 2010-08-22
Hi folks,

Ubuntu 10.04 64 bit

Can I install Orange on Ubuntu repo?  
[http://www.ailab.si/orange/](http://www.ailab.si/orange/)

If YES please advise how to add Orange repo to menu.list

Furthermore do I need install R to work?

TIA

B.R.
satimis

---

### Post by gunksta on 2010-08-23
[http://www.ailab.si/orange/nightly_builds.html](http://www.ailab.si/orange/nightly_builds.html)

---

### Post by satimis on 2010-08-24
> **gunksta said:**
> [http://www.ailab.si/orange/nightly_builds.html](http://www.ailab.si/orange/nightly_builds.html)

Hi,

Thanks for your advice.

Sorry it can't work.  Orange is hard-linked to python2.5.  Ubuntu10.04 is running python2.6.

I have orange packages download and installed on;
[http://www.ailab.si/orange/debian/dists/lenny/main/binary-amd64/](http://www.ailab.si/orange/debian/dists/lenny/main/binary-amd64/)

Also I have both python2.5.5 and python2.6.5 running here.  Still I failed starting Orange Canvas

$ /usr/bin/python2.5/bin/python /usr/lib/python2.5/site-packages/orange/OrangeCanvas/orngCanvas.pyw```


Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/orange/OrangeCanvas/orngCanvas.pyw", line 7, in <module>
    import orngEnviron, orngAddOns
ImportError: No module named orngEnviron

```

I think I have to building Orange from source.

B.R.
satimis

---

### Post by rubecdrevo on 2010-08-24
No, I am sorry orange is not availabl;e on ubuntu

---

### Post by rubecdrevo on 2010-08-24
No, I am sorry orange is not available on"ubuntu"........

---

### Post by gunksta on 2010-08-24
This is just a shot in the dark -- I haven't actually installed this yet -- but I downloaded the two .debs and I don't see anything about requiring Python 2.5.  Here's the info out of the two control packages:

```
Package: python-orange-svn
Version: 0.0.9360-1
Architecture: amd64
Maintainer: Mitar <mitar@tnode.com>
Installed-Size: 35972
Depends: libc6 (>= 2.7-1), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.2.1), python-imaging (>= 1.1.6-3)
Section: python
Priority: optional
Homepage: http://www.ailab.si/orange/
Description: Data mining framework (Python module)
 Orange is a component-based data mining software. It includes a range
 of data visualization, exploration, preprocessing and modeling
 techniques. It can be used through a nice and intuitive user interface
 or, for more advanced users, as a module for Python programming language.
 .
 This package provides a Python module. 
```

```
Package: orange-svn
Source: python-orange-svn
Version: 0.0.9360-1
Architecture: amd64
Maintainer: Mitar <mitar@tnode.com>
Installed-Size: 6252
Depends: python-orange-svn (= 0.0.9360-1), python-qt4 (>= 4.4.2-4), python-qwt5-qt4 (>= 5.1.0.dfsg-1), graphviz
Section: science
Priority: optional
Homepage: http://www.ailab.si/orange/
Description: Data mining framework (GUI)
 Orange is a component-based data mining software. It includes a range
 of data visualization, exploration, preprocessing and modeling
 techniques. It can be used through a nice and intuitive user interface
 or, for more advanced users, as a module for Python programming language.
 .
 This package provides a graphical user interface.
```

Unless I'm missing something obvious, python 2.5 doesn't appear to be a hard dependency and I noticed the Windows versions are apparently using 2.6 too. I would try removing 2.5 and just running 2.6 to see if it works. Of course, I also assume you have the other deps installed such as python-qt4. I think 2.5 may be causing you problems because the default python-qt4 does require 2.6.

I'm going to play with this at home tonight. I don't want to install it on my work machine but I will play with it tonight. It's an interesting problem and I do like making software work.

---

### Post by satimis on 2010-08-24
Hi Junksta,

At the beginning I don't have python 2.5.5 only python 2.6.5.  I can't get Orange Canvas started.  I have been hunting around and I got an advice on Orange forum saying Orange needs python 2.5 to run.  Therefore I installed python 2.5.5 but keeping python 2.6.5 without downgrade.  Because maybe some other packages on Ubuntu 10.04 need python 2.6.5.

I tested Orange on Win7 and Debian 5.04 respectively.  Both of them work without problem leaving behind only Ubuntu 10.04.  I'm testing all of them on a virtual machine running VirtualBox as virtualizer.

I think I have to build orange from source according to following URL;
[http://www.ailab.si/svn/orange/trunk/orange/doc/INSTALL.linux.txt](http://www.ailab.si/svn/orange/trunk/orange/doc/INSTALL.linux.txt)

I'll test it on another cloned VM running Ubuntu 10.04.

What I can't resolve is follow;```

4. RUNNING

To use Orange in python scripts, try importing "orange" and "orngStat" 
in python interpreter. It should work flawlessly.

```

What does it mean "importing "orange" and "orngStat" in python interpreter" ?


B.R.
satimis

---

### Post by radiobuzzer on 2010-08-31
> **satimis said:**
> Hi Junksta,


What does it mean "importing "orange" and "orngStat" in python interpreter" ?



It means openning a command line window, typing python
then you get this promt
```
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import orange
```
then you type 
```
import orange
```

Well, I am also an Ubuntu 10.04 victim. I just added the repository, typed "apt-get install python-orange-svn" and let it download and install everything. I had no problem with the dependencies. The process was finished with no problem and the package appears to have been installed. But still I cannot import orange. 

Anyway, I think we might have to move the discussion to the orange forum, there has already been a post on [Ubuntu 10.04 here]("http://www.ailab.si/orange/forum/viewtopic.php?p=2564")

---

### Post by muneson on 2011-05-31
(A bit late but maybe it will be helpful to someone.)

Orange is not in the repos, but you can install it
from the provided debian package with some modification.

First, download and install the debian package for orange 
(or add the repository according to 
[http://orange.biolab.si/nightly_builds.html](http://orange.biolab.si/nightly_builds.html))

This package won't currently work out of the box on Ubuntu,
because it assumes that you have python2.5 as your main version, 
and thus it will be installed in 
python2.5-specific module search paths. If you are on a 
newer Ubuntu, you have a later python and orange 
won't be found. Moreover, it doesn't immediately help to install
python2.5 as a secondary python, because 2.5 as a non-main python 
will expect its libraries in 

/usr/local/lib/python2.5

and not in 

/usr/lib/python2.5

which is where the debian setup will place the orange modules.

As far as I can tell, however, orange runs just fine under 2.6 and 2.7,
so it is mostly a matter of changing sys.path to include
the place where debian put it. For instance



```
~$ python2.7
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import orange
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named orange
>>> import sys
>>> sys.path.append('/usr/lib/python2.5/site-packages/orange')
>>> import orange
```

You could make this path change permanent by modifying your PYTHONPATH.
You could also set that variable more temporarily in 
the orange startup script
(/usr/bin/orange), so it looks like so:

```
#!/bin/bash
export PYTHONPATH=$PYTHONPATH:/usr/lib/python2.5/site-packages/orange
exec -a "$0" /usr/bin/python /usr/lib/python2.5/site-packages/orange/OrangeCanvas/orngCanvas.pyw "$@"
```


HTH,

Marcus

---

