---
title: "Why Ubuntu is getting on my nerves..."
date: 2005-05-28
forum: Desktop Environments
---

### Post by tommy04 on 2005-05-28
1. The import command in python doesn't find anything, breaking menu-editor and anything using pygame or pygtk
2. For no reason, AC_LIB_* variables or commands or something cannot be found when running ./configure

These are the main two reasons that Ubuntu is getting annoying. I say Ubuntu, not linux, because these problems never happened when I used Red Hat 9.

So if you guys have any advice, help?

---

### Post by cwaldbieser on 2005-05-28
If you go to the interactive python prompt and try to import something, does that work (e.g. >>import sys)?  Is it just certain modules, or is it all modules including standard library modules?

Has your PYTHONPATH environment variable recently been changed?

Not sure what the AC_LIB_* variable you are talking about is, but maybe you don't have some development library installed?  What program(s) are you trying to build from source when you get that error?  Also, posting a little bit more of the error might get you some better results.

---

### Post by tommy04 on 2005-05-28
<3

PYTHONPATH wasn't set, causing the problem. Thanks!

And I'll live without the AC_LIB_* stuff, as I commented out the stuff that checked for whatever it was and the program seemed to work so whoohoo!

And now, a little advertisement for another problem:
[http://ubuntuforums.org/showthread.php?t=31587](http://ubuntuforums.org/showthread.php?t=31587)

It's an nvidia driver problem that's come back to haunt me.

---

### Post by tommy04 on 2005-05-28
Looks like I spoke too soon- pygame still doesn't work because it's not in the directory pygtk is in. Do I have to reset pythonpath each time or what?

---

### Post by cwaldbieser on 2005-05-28
I am not entirely sure what you are trying to do, so here are some general comments that might help:

PYTHONPATH is to Python as PATH is to your shell.  That is, it is basically a list of all the directories that the Python interpreter should search when it is looking to import modules.  I delieve the current working directory is also searched by default, so if you write a script and a bunch of modules in one directory, you don't need to set anything special to import those modules.

By default, standard library modules should also be searched, so you should be able to import modules like "sys" without it explicitly being in your PYTHONPATH.

The PYTHONPATH can also be modified from within a Python script.  If you go to the interactive interpreter and import sys, you can view and modify sys.path, which is a list of all the directories python will search when importing.  Changes made this way last only as long as the script is running-- they don't actually change your environment variables.

I am just guessing, but in your ~/.bashrc, maybe you just need to set your PYTHONPATH to include a some extra python modules you downloaded?

Hope that helps.

---

### Post by tommy04 on 2005-05-29
Hmm. Well, now menu-editor's back to not working. I even set PYTHONPATH...

Errors are:
> tommy@Fry:~$ menu-editor
Traceback (most recent call last):
  File "/usr/bin/menu-editor", line 33, in ?
    import gtk
  File "/usr/local/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 33, in ?
    import gobject as _gobject
ImportError: /usr/local/lib/python2.4/site-packages/gtk-2.0/gobject.so: undefined symbol: PyUnicodeUCS2_FromUnicode
And:
> tommy@Fry:~$ pydance
Traceback (most recent call last):
  File "/usr/games/pydance", line 32, in ?
    from constants import * # This needs to be here to set sys.path.
  File "/usr/share/games/pydance/constants.py", line 62, in ?
    import pygame
ImportError: No module named pygame

And:
> tommy@Fry:~$ gdesklets
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/gdesklets/utils/__init__.py", line 23, in _pretty_excepthook
    deep_trace = True)
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 76, in format
    import vfs
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/utils/vfs.py", line 120, in ?
    exists = exists_urllib2
NameError: name 'exists_urllib2' is not defined

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gdesklets", line 4, in ?
    from main.DisplayList import DisplayList
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/main/DisplayList.py", line 4, in ?
    from utils import vfs
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/utils/vfs.py", line 120, in ?
    exists = exists_urllib2
NameError: name 'exists_urllib2' is not defined


---

### Post by cwaldbieser on 2005-05-29
Hmm, I just got pydance with apt-get and it ran OK, but it crashed when I tried to start a game.  I found a bug entered for it:

[https://launchpad.ubuntu.com/malone/tasks/313/+edit](https://launchpad.ubuntu.com/malone/tasks/313/+edit)

Did you get yours via apt-get or did you download the source?  

The other error you are experiencing I can't test so easily, as I mostly work in KDE ala Kubuntu.  It looks like the menu editor is trying to load a symbol from a DLL (shared object), but that symbol does not exist.  Might indicate a mismatch between the version of the DLL and your version of the python interpreter?

Not sure what is going on in the last case (gdesklets) without looking at the code.  

Do you have any other python programs you are experiencing problems with?  This seems like it may be a problem with your python installation.  You could try reinstalling you python2.4 package.

---

### Post by tommy04 on 2005-05-29
Tried reinstalling Python...

Didn't work.

I have no clue why all this isn't working. I mean, this is getting really annoying. But more annoying then this is the Nvidia driver problems... I'm tempted to try to make backups and reinstall Ubuntu...

---

