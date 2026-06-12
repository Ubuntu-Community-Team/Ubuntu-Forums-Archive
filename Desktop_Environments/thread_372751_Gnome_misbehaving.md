---
title: "Gnome misbehaving"
date: 2007-02-28
forum: Desktop Environments
---

### Post by Apocalypse_X on 2007-02-28
Okay call me a n00b but somehow I managed to remove the application menu. The Button is there , but it doesn't drop down. When clicked, it shows only a very small white square. Also the menu layout starts, but shows "starting" in tray for a few seconds and also doesn't work... 

Another problem is with gDesklets, which also refuse to start (the were working for some time). 
I tried shutting down beryl, but it doesn't matters... Anyone can help?

---

### Post by ComplexNumber on 2007-02-28
for your first problem, i wonder if its the same old problem. that is, ~/local somehow becoming owned by root. assuming your username is Apocalypse_X, try typing this on the comandline:
sudo chown -R Apocalypse_X:Apocalypse_X[COLOR=White]....[/COLOR]~/.local



>  Another problem is with gDesklets, which also refuse to start (the were working for some time). 
what happens when you type the following on the commandline:
gdesklets start

---

### Post by Apocalypse_X on 2007-02-28
Well changing the owner didn't help :(

gdesklets printout 

apocalypse@TurboDiesel:~$ gdesklets start
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.


and the log says:



==========================================================[02/28/07-22:50:42]===
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

---

### Post by Apocalypse_X on 2007-03-06
Anyone help? It's very frustrating without the applications launcher :mad:

---

