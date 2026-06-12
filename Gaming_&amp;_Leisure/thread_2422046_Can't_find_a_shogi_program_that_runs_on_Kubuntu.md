---
title: "Can't find a shogi program that runs on Kubuntu"
date: 2019-07-01
forum: Gaming &amp; Leisure
---

### Post by SeijiSensei on 2019-07-01
I've now gone through the three major programs to play shogi on Linux, and none of them work for me.  xshogi/gnushogi fail to write to the display. gShogi requires Python compiliation and invariably fails with errors.  Here's what I get if I use the precompiled version of gShogi

```

$ python3 run.py
Traceback (most recent call last):
  File "run.py", line 51, in <module>
    gshogi.gshogi.run()
  File "/usr/local/bin/gshogi-0.5.1/gshogi/gshogi.py", line 1323, in run
    Game()
  File "/usr/local/bin/gshogi-0.5.1/gshogi/gshogi.py", line 117, in __init__
    engine.init(opening_book_path, gv.verbose)
AttributeError: module 'engine' has no attribute 'init'

```

Compiling the program locally returns no error, but installing it returns
```

$ python3 setup.py install
running install
Traceback (most recent call last):
  File "setup.py", line 114, in <module>
    "Topic :: Games/Entertainment :: Board Games",
  File "/usr/lib/python3.7/distutils/core.py", line 148, in setup
    dist.run_commands()
  File "/usr/lib/python3.7/distutils/dist.py", line 966, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python3.7/distutils/dist.py", line 985, in run_command
    cmd_obj.run()
  File "/home/phl/Build/johncheetham-gshogi-2dd2464/setuptools-33.1.1-py3.7.egg/setuptools/command/install.py", line 67, in run
  File "/home/phl/Build/johncheetham-gshogi-2dd2464/setuptools-33.1.1-py3.7.egg/setuptools/command/install.py", line 98, in do_egg_install
  File "/home/phl/Build/johncheetham-gshogi-2dd2464/setuptools-33.1.1-py3.7.egg/setuptools/dist.py", line 490, in get_command_class
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2411, in load
    return self.resolve()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2417, in resolve
    module = __import__(self.module_name, fromlist=['__name__'], level=0)
  File "/home/phl/Build/johncheetham-gshogi-2dd2464/setuptools-33.1.1-py3.7.egg/setuptools/command/easy_install.py", line 51, in <module>
  File "/home/phl/Build/johncheetham-gshogi-2dd2464/setuptools-33.1.1-py3.7.egg/setuptools/archive_util.py", line 11, in <module>
ImportError: cannot import name 'ContextualZipFile' from 'pkg_resources' (/usr/lib/python3/dist-packages/pkg_resources/__init__.py)

```
Is all this just because I'm on KDE with Qt rather than a Gnome/GTK box? The final error reports appear to reflect a missing object in the python3 libraries.

Any other options?

---

### Post by Andreyshel on 2019-07-02
I was able to install it by invoking 
pip3 install gshogi
and then you can find your binary in /home/$username/.local/bin/gshogi

---

### Post by SeijiSensei on 2019-07-03
Thanks, but sadly that didn't work for me either.  I get "cannot import name 'gv' from '__main__' (gshogi.py)".  I'll try ripping out all the stuff I've already tried and start again to see if that works better.

Sure wish there was a .deb package in the Ubuntu repositories for this.

---

### Post by mastablasta on 2019-07-04
looks like they have a couple of different version and packages. 
[http://johncheetham.com/projects/gshogi/](http://johncheetham.com/projects/gshogi/)

[https://pypi.org/project/gshogi/](https://pypi.org/project/gshogi/)

I assume prerequisites are met:

[COLOR=#464646][FONT=&amp]Prerequisites[/FONT][/COLOR]
[COLOR=#464646][FONT=&amp]You need to install these prerequisites first:[/FONT][/COLOR][INDENT]
[LIST]
[*]python
[*]python-cairo
[*]python-gobject
[/LIST]
[/INDENT]
[COLOR=#464646][FONT=&amp]You need the python3 versions. These will have different names depending on your Linux.[/FONT][/COLOR]
On Debian/Mint/Ubuntu
[LIST]
[*]python3-gi-cairo
[*]gir1.2-rsvg-2.0
[/LIST]

heh no issues reported on github if i read correctly.

---

### Post by SeijiSensei on 2019-07-05
Thanks, but even with installing those packages I still get "cannot import name 'gv' from __main__" after using "pip3 install gshogi".  It doesn't complain during the installation, but fails when I try to run gshogi.py.

I'm guessing there are some missing GTK 3 libraries since I'm on KDE. Maybe someday I'll create a vanilla Ubuntu virtual machine and see if it works there.

---

