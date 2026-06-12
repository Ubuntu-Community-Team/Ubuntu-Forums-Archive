---
title: "gDesklets - db type could not be determined error!"
date: 2007-04-07
forum: Desktop Effects &amp; Customization
---

### Post by keithdw on 2007-04-07
I've been using gDesklets since I installed Linux on my machine several months ago, and I love it. Last night however it decided to stop working, no error messages, nothing; it just didn't load on startup as it usually does.

From a terminal I tried starting it, but this failed with a timeout error.
```
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
```
I've tried completely removing gdesklets from my machine a reinstalling a fresh version using the Synaptic Package Manager, but this has not helped.

The log file referred to above, has the following...
```
Log messages of /home/keith/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[04/07/07-17:49:36]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]db type could not be determined
in /usr/lib/gdesklets/gdesklets-daemon: line 127 ?
in /usr/lib/gdesklets/gdesklets-daemon: line 114 _gdesklets_main
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/main/Starter.py: line 2 ?
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/DaemonConfigger.py: line 1 ?
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/StateSaver.py: line 128 ?
in /usr/lib/gdesklets/config/StateSaver.py: line 30 __init__
in /usr/lib/gdesklets/config/Backend.py: line 68 Backend
in shelve.py: line 234 open
in shelve.py: line 215 __init__
in anydbm.py: line 80 open
[EXC]/usr/lib/python2.4/anydbm.py

[---]   75             mod = _defaultmod
[---]   76         else:
[---]   77             raise error, "need 'c' or 'n' flag to open new db"
[---]   78     elif result == "":
[---]   79         # db type cannot be determined
[ERR]>  80         raise error, "db type could not be determined"
[---]   81     else:
[---]   82         mod = __import__(result)
[---]   83     return mod.open(file, flag, mode)

```
What this db type it refers to I don't know, I've realised there is very little  in the way of help for gDesklet users, no forum, FAQ etc. There seem to be a few other people out there who have the same problem though, just no solutions that I've seen yet!

If anyone knows how to resolve this I'd be grateful.

---

### Post by rebo0t on 2007-09-11
> 
If anyone knows how to resolve this I'd be grateful.

I have the same problem with gDesklets. Does anyone know how to solve this problem???

---

