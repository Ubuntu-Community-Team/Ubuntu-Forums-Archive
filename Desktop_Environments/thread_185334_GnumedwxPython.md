---
title: "Gnumed/wxPython"
date: 2006-05-31
forum: Desktop Environments
---

### Post by denisesballs on 2006-05-31
I found [gnumed]("http://www.gnumed.org/") in the repos and decided to try it. I ran apt-get install gnumed-client and it installed a bunch of dependencies, but when I fire it up I get this:

```
jesse@dapper:~$ gnumed
log file is [/home/jesse/.gnumed/gnumed.log]
GNUmed startup: Determining GNUmed base directory ...
- environment variable GNUMED_DIR not set
  (only necessary if nothing else works, though)
GNUmed startup: Determining GNUmed resource directory ...
GNUmed startup: Cannot import wxPython library.
GNUmed startup: Make sure wxPython is installed.
CRITICAL ERROR: Error importing wxPython. Halted.
[PANIC] (/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py:Main@407): Exception: Unhandled exception encountered.
[PANIC] (/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py:Main@407): exception type : exceptions.ImportError
[PANIC] (/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py:Main@407): exception value: No module named wxPython
[PANIC] (/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py:Main@407): Traceback (most recent call last):<#10-0x0A-lf>
[PANIC] (/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py:Main@407):   File "/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py", line 395, in ?<#10-0x0A-lf>    from Gnumed.wxpython import gmGuiMain<#10-0x0A-lf>
[PANIC] (/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py:Main@407):   File "/usr/lib/python2.3/site-packages/Gnumed/wxpython/gmGuiMain.py", line 26, in ?<#10-0x0A-lf>    from wxPython import wx<#10-0x0A-lf>
[PANIC] (/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py:Main@407): ImportError: No module named wxPython<#10-0x0A-lf>
Traceback (most recent call last):
  File "/usr/lib/python2.3/site-packages/Gnumed/wxpython/gnumed.py", line 395, in ?
    from Gnumed.wxpython import gmGuiMain
  File "/usr/lib/python2.3/site-packages/Gnumed/wxpython/gmGuiMain.py", line 26, in ?
    from wxPython import wx
ImportError: No module named wxPython
```

Any idea what's going on? Shouldn't it have installed everything it needed?

---

### Post by shilbert on 2006-06-02
Hi !

I am one of the GNUmed coders.I am surprised gnumed can be found in dapper. I  am no regular Ubunutu user but I will go check it out and report.

---

### Post by shilbert on 2006-07-03
Look like Debian packages were used in Ubuntu. Seems to me GNUmed packages use python2.3 whereas Ubuntu uses python2.4 and installs wxpython 2.4 in python2.4.

wxpython cannot be found obviously.

version0.1 is outdated anyway I will make sure version0.2 will run

---

### Post by Briquet on 2006-07-08
Any idea about when is going to be released the 0.2  aka "librarian"?

---

### Post by docboat on 2006-07-18
> **shilbert said:**
> Hi !

I am one of the GNUmed coders.I am surprised gnumed can be found in dapper. I  am no regular Ubunutu user but I will go check it out and report.

Ah! Many thanks! I have been looking for just such support for a while.

---

### Post by shilbert on 2006-08-19
I am back with some more good news. I have now been able to reproduce the problem by using an Ubuntu virtual machine.

Seems like GNUmed will be in Edgy. Meanwhile we have released version 0.2

read more about it on wiki.gnumed.de

GNUmed's Debian packages do not run out of the box on Breezy. They work on Dapper however. 

Dapper features an older version of python-support packages than GNUmed's Debian packages like but it works anyway.

The source tarball works on Breezy, Dapper and Edgy since it does not trip over this dependency.

Check out wiki.gnumed.de

---

### Post by shilbert on 2007-09-29
Looks like GNUmed 0.2.6.3 will be in Gutsy and will really make a difference in user experience as the version in Feisty is still a problem for some users.

---

