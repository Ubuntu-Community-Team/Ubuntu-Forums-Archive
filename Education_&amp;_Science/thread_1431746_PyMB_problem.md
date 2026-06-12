---
title: "PyMB problem"
date: 2010-03-17
forum: Education &amp; Science
---

### Post by billharris on 2010-03-17
I've used PyMB under Jaunty and before, but it won't launch on Karmic for me.  When I try it from bash, I get

> $ PyMB
 wxPython version 2.6.3.2 was imported.
Traceback (most recent call last):
  File "/usr/bin/PyMB", line 8, in <module>
    load_entry_point('Model-Builder==0.4.1', 'gui_scripts', 'PyMB')()
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 277, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 2180, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 1913, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/lib/python2.6/dist-packages/model_builder/PyMB.py", line 32, in <module>
    import wxFrame1
  File "/usr/lib/python2.6/dist-packages/model_builder/wxFrame1.py", line 42, in <module>
    from pylab import *
  File "/usr/lib/pymodules/python2.6/pylab.py", line 1, in <module>
    from matplotlib.pylab import *
  File "/usr/lib/pymodules/python2.6/matplotlib/pylab.py", line 247, in <module>
    from matplotlib.pyplot import *
  File "/usr/lib/pymodules/python2.6/matplotlib/pyplot.py", line 78, in <module>
    new_figure_manager, draw_if_interactive, show = pylab_setup()
  File "/usr/lib/pymodules/python2.6/matplotlib/backends/__init__.py", line 25, in pylab_setup
    globals(),locals(),[backend_name])
  File "/usr/lib/pymodules/python2.6/matplotlib/backends/backend_wxagg.py", line 23, in <module>
    import backend_wx    # already uses wxversion.ensureMinimal('2.8')
  File "/usr/lib/pymodules/python2.6/matplotlib/backends/backend_wx.py", line 144, in <module>
    raise ImportError(missingwx)
ImportError: Matplotlib backend_wx and backend_wxagg require wxPython >=2.8

I have both versions 2.6 and 2.8 of wxPython installed.  I tried uninstalling 2.6 with Synaptic, but it took model-builder (PyMB) away, too.  Reinstalling brought back wxPython 2.6.

Any tips for getting this to work?

---

### Post by fccoelho on 2010-03-18
this bug has been fixed in the latest version (not yet on ubuntu servers). To install it:

first install the python-setuptools package:

sudo apt-get install python-setuptools

the install the latest version of Model-Builder

sudo easy_install -U Model-Builder

thanks for reporting.

---

### Post by billharris on 2010-03-18
Thanks!

---

