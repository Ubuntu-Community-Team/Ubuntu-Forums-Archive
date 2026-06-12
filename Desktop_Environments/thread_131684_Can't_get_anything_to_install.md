---
title: "Can't get anything to install"
date: 2006-02-16
forum: Desktop Environments
---

### Post by ThirdGenLS1 on 2006-02-16
So everytime i try to complie and install useing sudo this is what i get.

SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/pyshell.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/pyshell.py", line 103
locals=None, properties=None, banner=None):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rcsizer.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rcsizer.py", line 62
__in__init__(self):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rightalign.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rightalign.py", line 68
__in__init__(self, parent, id, *args, **kwargs):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rpcMixin.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/rpcMixin.py", line 103
__in__init__(self,method,args):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/scrolledpanel.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/scrolledpanel.py", line 36
name = "scrolledpanel"):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/sheet.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/sheet.py", line 19
__in__init__(self, parent, id, grid):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/shell.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/shell.py", line 68
__in__init__(self, parent, shell, id=-1):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splashscreen.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splashscreen.py", line 49
nnnnnnnnnnnnnnnnncallback = None):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splitter.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splitter.py", line 60
nnnnnnnnnnnnnnnnnstyle = 0, name="multiSplitter"):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/statbmp.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/statbmp.py", line 23
nnnnnnnnnnnnnnnnnname = "genstatbmp"):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/stattext.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/stattext.py", line 33
nnnnnnnnnnnnnnnnnname = "genstattext"):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/throbber.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/throbber.py", line 34
__in__init__(self):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker.py", line 36
fps=20,nnnnnnnnnnnnnnnn #frames per second
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker_xrc.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/ticker_xrc.py", line 18
__in__init__(self):
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxPlotCanvas.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxPlotCanvas.py", line 55
nnnnif wx.Platform == '__WXMSW__' and wx.GetApp() isnnot None:
^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxpTag.py ...
File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/wxpTag.py", line 106
__in__init__(self):
^
SyntaxError: invalid syntax

dpkg: error processing python-uno (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org2-writer:
openoffice.org2-writer depends on python-uno (>> 2.0.1); however:
Package python-uno is not configured yet.
dpkg: error processing openoffice.org2-writer (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org2:
openoffice.org2 depends on openoffice.org2-writer; however:
Package openoffice.org2-writer is not configured yet.
dpkg: error processing openoffice.org2 (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
bittornado
python-wxgtk2.6
bittornado-gui
python2.4-gnome2
python-gnome2
ndisgtk
python-uno
openoffice.org2-writer
openoffice.org2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ThirdGenLS1 on 2006-02-17
anyone???????

---

