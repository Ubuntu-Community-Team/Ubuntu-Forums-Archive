---
title: "amarok plugins now working"
date: 2008-02-01
forum: Desktop Environments
---

### Post by yon2501 on 2008-02-01
im having a few issues with amarok one is that the weekalarm program seems to be having some issues because im missing some packages but i dont know what package to get. this is the error message that it gives me
```

Traceback (most recent call last):
File "/home/jan/.kde/share/apps/amarok/scripts/weekalarm/weekalarm.py", line 25, in <module>
from WeekAlarmUI import WeekAlarmUI
File "/home/jan/.kde/share/apps/amarok/scripts/weekalarm/WeekAlarmUI.py", line 11, in <module>
from qt import *
ImportError: No module named qt

```
the other problem that i think might be related is that whenever i click a menu in amarok or the amarok symbol in the notification area it dose a double take like it half opens then fully opens. but that may be related to compiz fusion even tho it never did that til recently.

now theres one more thing which isnt that big a deal but the visualzation at the bottom of the playlist next to the stop and play buttons, the bars that rise and fall to the music, it suddenly changed from the blue one to a new one and i have no idea how to change it back.

btw i use gnome not kde

---

### Post by yw497 on 2008-03-16
Ah - too bad there's no response here.  I'm having just the same issue.

---

### Post by Freaky#Funga on 2008-03-25
> **yw497 said:**
> Ah - too bad there's no response here.  I'm having just the same issue.

Just read the info for this script

Dependencies:
Amarok 1.2 
Python 2.4 
PyQt Bindings

-> install python-qt4 (python-qt3 also possible) ;)

---

### Post by ucal on 2008-05-10
> **Freaky#Funga said:**
> Just read the info for this script

Dependencies:
Amarok 1.2 
Python 2.4 
PyQt Bindings

-> install python-qt4 (python-qt3 also possible) ;)

I'm having that same problem, and downloading the qt4 off of synaptic package manager didn't work for me.  Any other ideas?

---

