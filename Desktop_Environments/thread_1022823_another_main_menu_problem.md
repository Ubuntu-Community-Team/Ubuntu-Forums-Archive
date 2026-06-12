---
title: "another main menu problem"
date: 2008-12-27
forum: Desktop Environments
---

### Post by ironjawedangel on 2008-12-27
Hi all,
i cannot really tell that I get ubuntu a lot and since I formatted my computer the main menu doesn't work. Running it on the terminal doesn't help either, i get a message as follows:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 20, in <module>
    import cgi, os
  File "/usr/lib/python2.5/cgi.py", line 371
    """Constructor from field name and value."""
    ^
IndentationError: unexpected indent
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 20, in <module>
    from problem_report import ProblemReport
  File "/usr/lib/python2.5/site-packages/problem_report.py", line 15, in <module>
    import zlib, base64, time, UserDict, sys, gzip, struct
  File "/usr/lib/python2.5/gzip.py", line 60
    compresslevel=9, fileobj=None):
    ^
IndentationError: unexpected indent

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 20, in <module>
    import cgi, os
  File "/usr/lib/python2.5/cgi.py", line 371
    """Constructor from field name and value."""
    ^
IndentationError: unexpected indent


any ideas?

---

### Post by ajaysutton on 2008-12-28
I'm having a similar issue, but for me, the alacarte applet won't open at all.

In searching it out, I've come across several who suggest using synaptic or apt-get to remove and re-install alacarte.  That may help you out.

---

### Post by ajaysutton on 2008-12-28
Hi, I just posted this in response to another post.  I'd seen a post by jellybaby here:

[http://ubuntuforums.org/showthread.php?p=6449107#post6449107](http://ubuntuforums.org/showthread.php?p=6449107#post6449107)

This took care of the problem I was having.  I hope it will for yours too.

I had to change ownership (chown) on the .config/menus folder and also the .local folder in my home directory.  I wish I knew why, but here are the commands he used:

```
sudo chown -R user .config/menu
sudo chown -R user .local
```

Hope this helps.

---

