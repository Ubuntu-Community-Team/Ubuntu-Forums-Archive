---
title: "mpd client / desklet help"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by danifodor on 2008-01-17
Hi!

I have just installed mpd on my home server. It works fine with sonata and gmpc. I would like to add the mpdcontroller adesklet. I installed python-mpdclient and additionally py-libmpdclient as suggested in REDME file. However, I still get the error message if I want to complile:
```

# python mpdcontroller.py 
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "mpdcontroller.py", line 4, in ?
    import mpdclient
ImportError: No module named mpdclient

```

Any idea?

Cheers 

Daniel

---

### Post by danifodor on 2008-01-17
Forgot to write...

The beginning of install file is:
```

#!/usr/bin/env python

import adesklets
import mpdclient
import os
import time

```
and there is no mpdclient package.

D.

---

### Post by danifodor on 2008-01-17
OK, this is a general problem but I do not know where to search.
I cannot install none of the desklets (I tried 3-4). I either download them from sourceforge or with the command adesklets -i. I go to the directory where the desklet is, try to run, then press "r" to register. If I run adesklets nothing happens.

Fluxbox is my desktop environment.

What is the problem?

Daniel

---

### Post by danifodor on 2008-01-17
The soultion was trivial... Desklets were under conky....

:(

---

