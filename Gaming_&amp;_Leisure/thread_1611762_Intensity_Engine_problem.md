---
title: "Intensity Engine problem"
date: 2010-11-02
forum: Gaming &amp; Leisure
---

### Post by luks255 on 2010-11-02
Hi, I have a problem here, with Intensity Engine.

I kind of installed it, it made a directory on my home called "Intensityengine", inside that I have lots of files, and there are two that I am supposed to run: intensity_client.sh and intensity_client.py.

I tried to run both, and this came up on console:

```
lucas@stoews-desktop:~/intensityengine$ sh intensity_client.sh
intensity_client.sh: 5: ./cbuild/src/client/Intensity_CClient: not found
lucas@stoews-desktop:~/intensityengine$ python intensity_client.py
Traceback (most recent call last):
  File "intensity_client.py", line 11, in <module>
    from intensity.base import *
ImportError: No module named intensity.base
```

Any help?

---

### Post by J.K.Makowka on 2010-11-02
I assume Intensity, of the Syntensity project? I guess it's not really worth looking into since the project is more or less dead.
But parts of it have been taken up by the guys from CubeCreate:
[http://cubecreate.com/](http://cubecreate.com/)

---

