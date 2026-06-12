---
title: "Problem with Bouncy the Hungry Rabbit"
date: 2012-04-27
forum: Gaming &amp; Leisure
---

### Post by Handssolow on 2012-04-27
Thought I'd install Bouncy the Hungry Rabbit for my granddaughters to play but it doesn't run, perhaps an openGL issue? Attempting to run via the Terminal I get the messages below. Is there a simple solution to get this fixed?

Traceback (most recent call last):
  File "game.py", line 8, in <module>
    from OpenGL.GL import *
  File "/usr/lib/pymodules/python2.7/OpenGL/GL/__init__.py", line 2, in <module>
    from OpenGL.raw.GL import *
  File "/usr/lib/pymodules/python2.7/OpenGL/raw/GL/__init__.py", line 6, in <module>
    from OpenGL.raw.GL.constants import *
  File "/usr/lib/pymodules/python2.7/OpenGL/raw/GL/constants.py", line 6, in <module>
    from ctypes import *
  File "/usr/lib/python2.7/ctypes/__init__.py", line 10, in <module>
    from _ctypes import Union, Structure, Array
ImportError: No module named _ctypes

---

### Post by Perfect Storm on 2012-04-28
Is python-opengl library installed?

What about other 3D games, do they work?

---

### Post by Handssolow on 2012-04-29
Thanks.
Terminal reports that python-opengl is already installed.

I can run Sauerbraten without any problem except that I'm no good. Looks like Bouncy Rabbit might be more aimed at my skill level, if I could only get it to run.

Oh and Extreme Tux Racer has been popular with my grandaughters.

---

