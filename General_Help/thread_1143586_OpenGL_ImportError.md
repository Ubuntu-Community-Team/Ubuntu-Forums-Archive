---
title: "OpenGL ImportError"
date: 2009-04-30
forum: General Help
---

### Post by Urema on 2009-04-30
Hi,

Everytime i run an Python /OpenGL program i get this error message

##########################
Traceback (most recent call last):
  File "./new.py", line 9, in <module>
    from OpenGL.GLUT import *
  File "/usr/lib/python2.5/site-packages/OpenGL/GLUT/__init__.py", line 2, in <module>
    from OpenGL.raw.GLUT import *
  File "/usr/lib/python2.5/site-packages/OpenGL/raw/GLUT/__init__.py", line 6, in <module>
    from OpenGL.raw.GLUT.constants import *
  File "/usr/lib/python2.5/site-packages/OpenGL/raw/GLUT/constants.py", line 7, in <module>
    from OpenGL import platform, arrays
  File "/usr/lib/python2.5/site-packages/OpenGL/platform/__init__.py", line 20, in <module>
    import os, sys, pkg_resources
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 16, in <module>
    import sys, os, zipimport, time, re, imp, new
  File "/home/urema/Documents/University/Coursework/new.py", line 10, in <module>
    from OpenGL.GL import *
  File "/usr/lib/python2.5/site-packages/OpenGL/GL/__init__.py", line 2, in <module>
    from OpenGL.raw.GL import *
  File "/usr/lib/python2.5/site-packages/OpenGL/raw/GL/__init__.py", line 6, in <module>
    from OpenGL.raw.GL.constants import *
  File "/usr/lib/python2.5/site-packages/OpenGL/raw/GL/constants.py", line 7, in <module>
    from OpenGL import platform, arrays
  File "/usr/lib/python2.5/site-packages/OpenGL/arrays/__init__.py", line 20, in <module>
    from OpenGL.arrays.arrayhelpers import *
  File "/usr/lib/python2.5/site-packages/OpenGL/arrays/arrayhelpers.py", line 6, in <module>
    from OpenGL import contextdata, error, wrapper, constants, converters
  File "/usr/lib/python2.5/site-packages/OpenGL/contextdata.py", line 13, in <module>
    from OpenGL import platform
ImportError: cannot import name platform

##################################################

Ive made sure that the files actually exists, like __init__.py etc.....They do reside in the location specified. I tried re-installing OpenGL and that didnt do anything. 

Does anyone know where to start looking?

Thanks in advance.

N Dean G.

---

