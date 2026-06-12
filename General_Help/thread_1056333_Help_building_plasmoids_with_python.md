---
title: "Help building plasmoids with python"
date: 2009-01-31
forum: General Help
---

### Post by agim on 2009-01-31
I have just spent a very frustrating hour following this tutorial...
[http://techbase.kde.org/Development/Tutorials/Plasma/Python/GettingStarted#Project_Structure](http://techbase.kde.org/Development/Tutorials/Plasma/Python/GettingStarted#Project_Structure)

All I can get is this... 

"could not open the hello-python package required for the Hello Python 
widget."

I have all of the required software installed, and I just can't get it to work.
The only thing I haven't done, is install kde from svn. I would rather avoid this step. If I have to install it, fine, I will, but if anybody knows a way to write plasmoids without install kde from svn that would be spectacular.
This has been an incredibly frustrating experience.
Thanks for your help.

---

### Post by agim on 2009-01-31
bump

---

### Post by Splondike on 2009-02-01
Guday, i've got the tutorial working on my machine. I went ahead and made the zip file as they instructed (see attached). Then I installed it using the command:
```
plasmapkg -i hello-python.zip
```
I then ran it in the viewer using the command:
```
plasmoidviewer hello-python
```
Note that it only worked if I installed the package before using the plasmoidviewer program.

---

### Post by marco_ on 2009-02-05
> **Splondike said:**
> 
I then ran it in the viewer using the command:
```
plasmoidviewer hello-python
```


I've download your hellp-python.zip but on my pc (ubuntu 8.10 amd64 + kde4.2 repository) there is this error:

```
$plasmoidviewer hello-python
Traceback (most recent call last):
  File "/usr/share/kde4/apps/plasma_scriptengine_python/pyappletscript.py", line 19, in <module>
    from PyQt4.QtCore import *
ImportError: /usr/lib/python2.5/site-packages/PyQt4/QtCore.so: undefined symbol: PyExc_ValueError
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 401, in <module>
    import select
ImportError: /usr/lib/python2.5/lib-dynload/select.so: undefined symbol: PyExc_ValueError

Original exception was:
Traceback (most recent call last):
  File "/usr/share/kde4/apps/plasma_scriptengine_python/pyappletscript.py", line 19, in <module>
    from PyQt4.QtCore import *
ImportError: /usr/lib/python2.5/site-packages/PyQt4/QtCore.so: undefined symbol: PyExc_ValueError

```

and there is a window with this message:

"This object could not be created for the following reason:
Could not create a python ScriptEngine for the Hello Python widget."


any suggestions? many thanks!

---

### Post by marco_ on 2009-02-09
bump

---

### Post by marco_ on 2009-02-10
Yesterday I've installed kubuntu jaunty (i386) on another hard disk and hello-python plasmoid doesn't work: there is the same problem.

Does it happen only to me?

---

### Post by txcrackers on 2009-02-15
Nope, not only you. I've got the same problem (Kubuntu 8.10, KDE 4.2 from PPA).

Update: I believe I've figured this out - it seems the 4.2 for Intrepid does not contain the appropriate scripting "-dev" packages, so you really can't build any Python (or Ruby) plasmoids. I haven't tried the Javascript one yet...

---

### Post by marco_ on 2009-02-16
many thanks for your reply. :)
BTW, what "-dev" packages? python-dev? libplasma-dev? others?

many thanks! :)

---

### Post by marco_ on 2009-02-18
solved! I've installed python-dev and python plasmoids work!!! many many thanks, txcrackers! :D

So, the bug is that ubuntu python-plasma doesn't depend on package python-dev.

---

### Post by agim on 2009-02-20
Great, I am going to try this and see if I can confirm it.

---

### Post by txcrackers on 2009-02-22
Yup - python-dev does the trick...

---

### Post by Exilant on 2009-03-04
doesn't do it or me (jaunty), although the packages can be installed, plasma doesn't want to show them(from PyKDE4 import plasmascript; fails)

i suspect that has something to do with the python installation, 
/usr/lib/python2.5/site-packages/PyKDE4/plasmascript.py exists, but python2.6 is the default(seems messy anyway, kubuntu-desktop apparently depends on both being available).

---

