---
title: "Upgrading SAGE"
date: 2010-04-02
forum: Education &amp; Science
---

### Post by AmadeusOK on 2010-04-02
I installed Sage using Synaptic, which gives me a very old version (3.0.5) I want to upgrade to the latest version 4.3.5. However, when I enter "sage -upgrade" I get:

```
Using SAGE Server http://www.sagemath.org//packages
http://www.sagemath.org//packages/install --> install
[.]
Traceback (most recent call last):
  File "/usr/lib/sagemath/local/bin/sage-update", line 64, in <module>
    os.chdir("%s/standard/"%SPKG_ROOT)
OSError: [Errno 2] No such file or directory: '/usr/lib/sagemath/spkg//standard/'
Error getting new packages!
Using SAGE Server http://www.sagemath.org//packages
http://www.sagemath.org//packages/install --> install
[.]
Traceback (most recent call last):
  File "/usr/lib/sagemath/local/bin/sage-update", line 64, in <module>
    os.chdir("%s/standard/"%SPKG_ROOT)
OSError: [Errno 2] No such file or directory: '/usr/lib/sagemath/spkg//standard/'
Error getting new packages!

```

Does anyone know what's going on here? Thanks for your help.

---

### Post by rafita on 2010-04-02
I used to compile and/or upgrade via sage -upgrade, but that takes just so many hours in my netbook. I reccommend you just download the new binary, there is usually one for ubuntu with the latest version.

---

