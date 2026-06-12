---
title: "lupa/_lupa.c:218: fatal error: lua.h: No such file or directory compilation terminate"
date: 2010-12-26
forum: Gaming &amp; Leisure
---

### Post by werthog2994 on 2010-12-26
Whenever I try to install openblox I get this error, Does anyone here have ideas for solutions? Their forum is always empty.

```
running install
install_dir /usr/local/lib/python2.6/dist-packages/
Checking .pth file support in /usr/local/lib/python2.6/dist-packages/
/usr/bin/python -E -c pass
TEST PASSED: /usr/local/lib/python2.6/dist-packages/ appears to support .pth files
running bdist_egg
running egg_info
writing requirements to OpenBlox_Game_Engine.egg-info/requires.txt
writing OpenBlox_Game_Engine.egg-info/PKG-INFO
writing top-level names to OpenBlox_Game_Engine.egg-info/top_level.txt
writing dependency_links to OpenBlox_Game_Engine.egg-info/dependency_links.txt
reading manifest file 'OpenBlox_Game_Engine.egg-info/SOURCES.txt'
writing manifest file 'OpenBlox_Game_Engine.egg-info/SOURCES.txt'
installing library code to build/bdist.linux-x86_64/egg
running install_lib
running build_py
creating build/bdist.linux-x86_64/egg
creating build/bdist.linux-x86_64/egg/obengine
copying build/lib.linux-x86_64-2.6/obengine/world.py -> build/bdist.linux-x86_64/egg/obengine
creating build/bdist.linux-x86_64/egg/obengine/phys
copying build/lib.linux-x86_64-2.6/obengine/phys/__init__.py -> build/bdist.linux-x86_64/egg/obengine/phys
copying build/lib.linux-x86_64-2.6/obengine/player.py -> build/bdist.linux-x86_64/egg/obengine
copying build/lib.linux-x86_64-2.6/obengine/scripttest.py -> build/bdist.linux-x86_64/egg/obengine
copying build/lib.linux-x86_64-2.6/obengine/luaengine.py -> build/bdist.linux-x86_64/egg/obengine
copying build/lib.linux-x86_64-2.6/obengine/worldtest.py -> build/bdist.linux-x86_64/egg/obengine
copying build/lib.linux-x86_64-2.6/obengine/cfg.py -> build/bdist.linux-x86_64/egg/obengine
copying build/lib.linux-x86_64-2.6/obengine/luautils.py -> build/bdist.linux-x86_64/egg/obengine
creating build/bdist.linux-x86_64/egg/obengine/gfx
copying build/lib.linux-x86_64-2.6/obengine/gfx/worldsource.py -> build/bdist.linux-x86_64/egg/obengine/gfx
copying build/lib.linux-x86_64-2.6/obengine/gfx/window3d.py -> build/bdist.linux-x86_64/egg/obengine/gfx
copying build/lib.linux-x86_64-2.6/obengine/gfx/player.py -> build/bdist.linux-x86_64/egg/obengine/gfx
copying build/lib.linux-x86_64-2.6/obengine/gfx/element3d.py -> build/bdist.linux-x86_64/egg/obengine/gfx
copying build/lib.linux-x86_64-2.6/obengine/gfx/__init__.py -> build/bdist.linux-x86_64/egg/obengine/gfx
copying build/lib.linux-x86_64-2.6/obengine/element.py -> build/bdist.linux-x86_64/egg/obengine
copying build/lib.linux-x86_64-2.6/obengine/attrdict.py -> build/bdist.linux-x86_64/egg/obengine
creating build/bdist.linux-x86_64/egg/obengine/utils
copying build/lib.linux-x86_64-2.6/obengine/utils/__init__.py -> build/bdist.linux-x86_64/egg/obengine/utils
copying build/lib.linux-x86_64-2.6/obengine/__init__.py -> build/bdist.linux-x86_64/egg/obengine
byte-compiling build/bdist.linux-x86_64/egg/obengine/world.py to world.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/phys/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/player.py to player.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/scripttest.py to scripttest.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/luaengine.py to luaengine.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/worldtest.py to worldtest.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/cfg.py to cfg.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/luautils.py to luautils.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/gfx/worldsource.py to worldsource.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/gfx/window3d.py to window3d.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/gfx/player.py to player.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/gfx/element3d.py to element3d.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/gfx/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/element.py to element.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/attrdict.py to attrdict.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/utils/__init__.py to __init__.pyc
byte-compiling build/bdist.linux-x86_64/egg/obengine/__init__.py to __init__.pyc
installing package data to build/bdist.linux-x86_64/egg
running install_data
creating build/bdist.linux-x86_64/egg/EGG-INFO
installing scripts to build/bdist.linux-x86_64/egg/EGG-INFO/scripts
running install_scripts
running build_scripts
creating build/bdist.linux-x86_64/egg/EGG-INFO/scripts
copying build/scripts-2.6/oblaunch.py -> build/bdist.linux-x86_64/egg/EGG-INFO/scripts
changing mode of build/bdist.linux-x86_64/egg/EGG-INFO/scripts/oblaunch.py to 755
copying OpenBlox_Game_Engine.egg-info/PKG-INFO -> build/bdist.linux-x86_64/egg/EGG-INFO
copying OpenBlox_Game_Engine.egg-info/SOURCES.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
copying OpenBlox_Game_Engine.egg-info/dependency_links.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
copying OpenBlox_Game_Engine.egg-info/requires.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
copying OpenBlox_Game_Engine.egg-info/top_level.txt -> build/bdist.linux-x86_64/egg/EGG-INFO
zip_safe flag not set; analyzing archive contents...
creating 'dist/OpenBlox_Game_Engine-0.1-py2.6.egg' and adding 'build/bdist.linux-x86_64/egg' to it
removing 'build/bdist.linux-x86_64/egg' (and everything under it)
Processing OpenBlox_Game_Engine-0.1-py2.6.egg
removing '/usr/local/lib/python2.6/dist-packages/OpenBlox_Game_Engine-0.1-py2.6.egg' (and everything under it)
creating /usr/local/lib/python2.6/dist-packages/OpenBlox_Game_Engine-0.1-py2.6.egg
Extracting OpenBlox_Game_Engine-0.1-py2.6.egg to /usr/local/lib/python2.6/dist-packages
OpenBlox-Game-Engine 0.1 is already the active version in easy-install.pth
Installing oblaunch.py script to /usr/local/bin

Installed /usr/local/lib/python2.6/dist-packages/OpenBlox_Game_Engine-0.1-py2.6.egg
Processing dependencies for OpenBlox-Game-Engine==0.1
Searching for lupa
Reading http://pypi.python.org/simple/lupa/
Best match: lupa 0.18
Downloading http://pypi.python.org/packages/source/l/lupa/lupa-0.18.tar.gz#md5=331237744561d41a1a659e514893d938
Processing lupa-0.18.tar.gz
Running lupa-0.18/setup.py -q bdist_egg --dist-dir /tmp/easy_install-Bf0ZNy/lupa-0.18/egg-dist-tmp-z2adLB
building with Cython 0.12.1
[COLOR="Red"]warning: no files found matching '*' under directory '.hg'
lupa/_lupa.c:218: fatal error: lua.h: No such file or directory
compilation terminated.
error: Setup script exited with error: command 'gcc' failed with exit status 1[/COLOR]
```

---

### Post by gmargo on 2010-12-26
> **werthog2994 said:**
> [COLOR=Red]
lupa/_lupa.c:218: fatal error: lua.h: No such file or directory
[/COLOR]

You probably need to install the lua development package.

To find what package provides **lua.h**, you can use the [http://packages.ubuntu.com/](http://packages.ubuntu.com/) site.

Here's the search for lua.h in Maverick: [http://packages.ubuntu.com/search?searchon=contents&keywords=lua.h&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=lua.h&mode=exactfilename&suite=maverick&arch=any)

which gives this file to package table:
```

/usr/include/lua40/lua.h                            [liblua40-dev]("http://packages.ubuntu.com/maverick/liblua40-dev")                       
/usr/include/lua5.1/lua.h                           [liblua5.1-0-dev]("http://packages.ubuntu.com/maverick/liblua5.1-0-dev")                       
/usr/include/lua50/lua.h                            [liblua50-dev]("http://packages.ubuntu.com/maverick/liblua50-dev")                       
/usr/include/luajit-2.0/lua.h                       [libluajit-5.1-dev]("http://packages.ubuntu.com/maverick/libluajit-5.1-dev")

```I'm pretty sure it's not the fourth one.  The first three packages are for different versions of **lua**, so you have to figure out which to install.   If you have lua already installed, then match that version.  Otherwise you may as well start at the latest and work backwards.

---

