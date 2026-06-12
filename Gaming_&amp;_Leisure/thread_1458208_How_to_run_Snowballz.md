---
title: "How to run Snowballz?"
date: 2010-04-19
forum: Gaming &amp; Leisure
---

### Post by Crazedpsyc on 2010-04-19
When I run it from the menu nothing happens. from the terminal, it says:
> 
/usr/share/games/snowballz/font.py:3: UserWarning: 
*******************************************************************************
The rabbyt.fonts module is deprecated and will be removed in a future version
of rabbyt.  I recommend using pyglet for font rendering.

If you still want to use pygame fonts, check out the ``pygame_font.py`` example
included with rabbyt.
*******************************************************************************

  import rabbyt.fonts
/usr/share/games/snowballz/font.py:3: UserWarning: 
The rabbyt.vertexarrays module is deprecated and will be removed in a future
version of rabbyt.

  import rabbyt.fonts
Traceback (most recent call last):
  File "snowballz.py", line 28, in <module>
    import menu
  File "/usr/share/games/snowballz/menu.py", line 3, in <module>
    from gooeypy import gl as gui
  File "/usr/share/games/snowballz/gooeypy/gl.py", line 1, in <module>
    import util
  File "/usr/share/games/snowballz/gooeypy/util.py", line 10, in <module>
    from cellulose import *
  File "/usr/share/games/snowballz/cellulose/__init__.py", line 24, in <module>
    from cellulose.celltypes import CellList, CellDict, CellSet, ComputedDict
  File "/usr/share/games/snowballz/cellulose/celltypes.py", line 72, in <module>
    class CellList(DependencyCell, _ListBase):
  File "/usr/share/games/snowballz/cellulose/celltypes.py", line 66, in __init__
    try: new.__name__ = old.__name__
AttributeError: 'NoneType' object has no attribute '__name__'


and then nothing happens. plz help!

---

### Post by seamonkey on 2010-04-21
I had the same problems, commenting out lines 66-67 in /usr/share/games/snowballz/cellulose/celltypes.py seems to fix it. You comment out lines with # in python and you need to be root to change the file.

---

### Post by Crazedpsyc on 2010-04-26
Oh, hey thanks, I 4got I asked this lol! can you give that idea in a bit more detail? I am a bit of a noob to ubuntu!

---

### Post by kulus1969 on 2010-05-09
This didn't work.  Running LTS Hardy Heron 8.04.
Do I need to upgrade my ubuntu release to make it work?
Thanks...

:guitar:

---

### Post by Crazedpsyc on 2010-06-17
Lalala doodlydoo... HELLO?!? hey kulus, I don't know what is wrong with this place, i've been waiting weeks for one answer, and not a thing! This didnt work for Karmic either, so I don't think upgrading will fix it, sorry. I have been learning a lot about languages like python and C(all_of_them), so if I figure out HOW TO DECOMPILE(!!!!) I will look into the issue. but the only decompiler I found is Boomerang, and for some reason it never actually works, so...

---

