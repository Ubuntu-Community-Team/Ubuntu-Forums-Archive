---
title: "pypanel refuses to start"
date: 2005-04-24
forum: Desktop Environments
---

### Post by Pinguvin on 2005-04-24
Hi,

Im planning to use openbox together with pypanel, but i cant pypanel to start. When i try to start it from a terminal i get this error:

```
File "/usr/bin/pypanel", line 739, in ?
    from ppmodule import ppinit, ppshade, ppicon, ppfont, ppfontsize, ppclear
ImportError: No module named ppmodule
``` 

I have no idea what this means or how to fix it. Hopefully, some of you guys can assist me?   :) 

btw I used the .deb from [http://laylward.com/debian/unstable/](http://laylward.com/debian/unstable/) .. its called pypanel_2.2-2_i386.deb

---

### Post by sas on 2005-04-24
have you tried installing xlibs-dev ? A google search said that could be the culprit..

---

### Post by Pinguvin on 2005-04-25
i installed these packages along with pypanel

libimlib2 libltdl3 libungif4g python-xlib python2.3 python2.4-xlib

---

### Post by Pinguvin on 2005-04-27
anyone?  :?

---

### Post by Fab on 2005-04-27
try installing  the xlibs-dev package

---

### Post by Pinguvin on 2005-04-27
installed the xlibs-deb but it still wont work

---

