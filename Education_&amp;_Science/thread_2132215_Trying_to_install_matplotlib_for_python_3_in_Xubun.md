---
title: "Trying to install matplotlib for python 3 in Xubuntu 12.04"
date: 2013-04-04
forum: Education &amp; Science
---

### Post by lethalfang on 2013-04-04
I've installed matplotlib for Python 3.2 before, but now I can't do it in my new computer, and I'm banging my heads. 

I've tried a bunch of instructions on the web, and none have worked for 2 of my computers. It just wouldn't really install. 

Python 3.2.3 (default, Oct 19 2012, 20:10:41) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import matplotlib
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.2/dist-packages/matplotlib-1.3.x-py3.2-linux-x86_64.egg/matplotlib/__init__.py", line 180, in <module>
    from matplotlib.rcsetup import (defaultParams,
  File "/usr/local/lib/python3.2/dist-packages/matplotlib-1.3.x-py3.2-linux-x86_64.egg/matplotlib/rcsetup.py", line 21, in <module>
    from matplotlib.colors import is_color_like
  File "/usr/local/lib/python3.2/dist-packages/matplotlib-1.3.x-py3.2-linux-x86_64.egg/matplotlib/colors.py", line 204, in <module>
    for k, v in cnames.items():
RuntimeError: dictionary changed size during iteration
>>> 


Any idea what went wrong?:confused:

---

