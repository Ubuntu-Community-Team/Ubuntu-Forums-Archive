---
title: "Problems installing snowballz"
date: 2007-05-05
forum: Gaming &amp; Leisure
---

### Post by KIAaze on 2007-05-05
I followed the instructions [here]("http://gaming.gwos.org/e107_plugins/content/content.php?content.27") to install snowballz, however I get this error:

```
>sh StartSN.sh
Traceback (most recent call last):
  File "snowballz.py", line 4, in <module>
    from player import Player
  File "/home/me/.Games/snowballz-0.9/player.py", line 2, in <module>
    import ai
  File "/home/me/.Games/snowballz-0.9/ai.py", line 2, in <module>
    import data
  File "/home/me/.Games/snowballz-0.9/data.py", line 2, in <module>
    import textures
  File "/home/me/.Games/snowballz-0.9/textures.py", line 5, in <module>
    class Texture:
  File "/home/me/.Games/snowballz-0.9/textures.py", line 17, in Texture
    def __init__(self, image, scale_format="nearest", internal_format=GL_COMPRESSED_RGBA):
NameError: name 'GL_COMPRESSED_RGBA' is not defined

```

---

### Post by DoktorSeven on 2007-05-05
My guess would be that you need python-opengl package installed (from repos).

Edit: okay, it's not that; apparently; I just downloaded it and I'm having trouble running it.  I'll edit again if I figure it out.
Edit 2: The name mentioned in the error (name 'GL_COMPRESSED_RGBA' is not defined) apparently should be in the python-opengl (PyOpenGL) but it's not.  Not sure where the blame lies here; unless someone else with more knowledge of Python and PyOpenGL can help, because I'm stumped.

---

### Post by Perfect Storm on 2007-05-06
I'll check it out, if it's an error in the guide, if not it might be a good idea to bug report it to the guy who made the game.

---

### Post by Perfect Storm on 2007-05-06
Okay, if you read the news from his page, he actually made an lib called GooeyPy which need to be compiled as well for the new release of snowballz (0.9.0 which have been released recently).

---

### Post by DoktorSeven on 2007-05-06
GooeyPy was installed here, the error is the same.  As I mentioned, the undefined constant supposedly comes from PyOpenGL, which doesn't have it defined when I load it from the commandline and try to reference it.

Edit: Okay, new theory: something is wrong with the python-opengl package in Ubuntu.  I removed that package and installed PyOpenGL with easy_install (**sudo easy_install PyOpenGL**) and the game now works.

Anyone want to confirm?  A bug report for python-opengl probably should be filed if this is the case.

---

### Post by Perfect Storm on 2007-05-06
Okay, I was a bit hasty. I tried it as well. Same error. I better to report this to snaowballz dude.

---

### Post by Crenfinkle on 2007-06-09
Received the following error after "easy_installing" PyOpenGL and GooeyPy. I'll report this upstream as well.

```
Traceback (most recent call last):
  File "snowballz.py", line 23, in <module>
    import menu
  File "/home/chris/dls/snowballz-0.9.2/menu.py", line 3, in <module>
    from gooeypy import gl as gui
  File "/usr/lib/python2.5/site-packages/GooeyPy-0.1-py2.5.egg/gooeypy/gl.py", line 12, in <module>
    from button import Button, Switch
  File "/usr/lib/python2.5/site-packages/GooeyPy-0.1-py2.5.egg/gooeypy/button.py", line 6, in <module>
    from cellulose.restrictions import StringRestriction
ImportError: No module named restrictions
```

---

