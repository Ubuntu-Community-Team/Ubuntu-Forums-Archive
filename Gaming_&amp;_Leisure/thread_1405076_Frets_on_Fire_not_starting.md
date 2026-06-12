---
title: "Frets on Fire not starting"
date: 2010-02-12
forum: Gaming &amp; Leisure
---

### Post by wobin77 on 2010-02-12
Hey all,

After installing Frets on Fire from the Software centre i get this error while trying to boot from shell:

```
wobin@wobin-laptop:/usr/games$ fretsonfire 
Traceback (most recent call last):
  File "./FretsOnFire.py", line 45, in <module>
    from GameEngine import GameEngine
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 23, in <module>
    from OpenGL.GL import *
  File "/usr/lib/pymodules/python2.6/OpenGL/GL/__init__.py", line 2, in <module>
    from OpenGL.raw.GL import *
  File "/usr/lib/pymodules/python2.6/OpenGL/raw/GL/__init__.py", line 6, in <module>
    from OpenGL.raw.GL.constants import *
  File "/usr/lib/pymodules/python2.6/OpenGL/raw/GL/constants.py", line 7, in <module>
    from OpenGL import platform, arrays
  File "/usr/lib/pymodules/python2.6/OpenGL/platform/__init__.py", line 36, in <module>
    _load()
  File "/usr/lib/pymodules/python2.6/OpenGL/platform/__init__.py", line 27, in _load
    plugin_class = plugin.load()
  File "/usr/lib/pymodules/python2.6/OpenGL/plugins.py", line 14, in load
    return importByName( self.import_path )
  File "/usr/lib/pymodules/python2.6/OpenGL/plugins.py", line 28, in importByName
    module = __import__( ".".join(moduleName), {}, {}, moduleName)
  File "/usr/lib/pymodules/python2.6/OpenGL/platform/glx.py", line 8, in <module>
    class GLXPlatform( baseplatform.BasePlatform ):
  File "/usr/lib/pymodules/python2.6/OpenGL/platform/glx.py", line 16, in GLXPlatform
    mode=ctypes.RTLD_GLOBAL 
  File "/usr/lib/pymodules/python2.6/OpenGL/platform/ctypesloader.py", line 48, in loadLibrary
    return dllType( name, mode )
  File "/usr/lib/python2.6/ctypes/__init__.py", line 353, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: ('GL: cannot open shared object file: No such file or directory', 'GL', None)
```

Python-opengl is installed on my system. 
Using 1005ha EEEpc. 

Thanks in advance

---

### Post by wobin77 on 2010-02-12
-> Solved it making a link:

```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
```

---

