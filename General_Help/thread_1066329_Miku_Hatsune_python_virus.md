---
title: "Miku Hatsune python virus?"
date: 2009-02-10
forum: General Help
---

### Post by modmadmike on 2009-02-10
Wxpython not working code output not working, weird output resembling a program that I made when I was bored.

```

#!/usr/bin/env python
import wx
print "TEST"
```
When I run this in SPE or the terminal...

```

/usr/bin/melody.sh      
Vocaloid
Ver. 2
Code 01
miku hatsune
Traceback (most recent call last):
 File "/home/modmadmike/test.py", line 3, in <module>
import wx
 File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
from wx._core import *
 File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 6, in <module>
new_instancemethod = new.instancemethod
AttributeError: 'module' object has no attribute 'instancemethod'
```
I get this output!! THE MIKU HATSUNE VIRUS:lolflag:

I reinstalled but as soon as a mounted my /home it was back to the same problem, all of the traces of the program was removed I just don't get it. Reinstalling from synaptic wont help either.

---

### Post by beno1990 on 2009-02-10
Have you tried checking your home directory for config files (hidden files beginning with a .(period)) which might be retaining it?

---

### Post by modmadmike on 2009-02-10
looked but found none so far

---

### Post by modmadmike on 2009-03-20
Fixed! Deleted all of my . files and made a new account and then changed the home directory.

---

### Post by modmadmike on 2009-04-20
lol forgot about this the error was gone but it was actually because I made a new file called wx.py. I deleted this, and it came back!. The problem was oddly because of a file [~/new.py] which I had no suspicion of lol!!! :rolleyes:

---

