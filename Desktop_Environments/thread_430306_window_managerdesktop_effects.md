---
title: "window manager/desktop effects"
date: 2007-05-02
forum: Desktop Environments
---

### Post by mrkilgoretrout on 2007-05-02
Window manager doesn't seem to work with desktop effects turned on.  It appears when effects are turned off.  The symptom is reproducible and reversible.  I'm on amd64.  Hmmm.

---

### Post by mrkilgoretrout on 2007-05-02
I've updated to feisty, sorry.

---

### Post by josephus on 2007-05-02
need more information in order to help you.

what type of graphics card do you have and what drivers are you using.

what message do you  get if you run compiz from the terminal

```
compiz --replace
```

---

### Post by mrkilgoretrout on 2007-05-02
Fixed it.  I have an Nvidia card.  I added a few lines to my xorg.conf and everything seems to be working great.

---

### Post by josephus on 2007-05-02
mind posting what you did so other ppl who stumble on this post can be helped?

---

### Post by Tomun on 2007-05-02
I had this same issue and fixed it by adding:

 Option          "AddARGBGLXVisuals" "True"

to the Screen section in xorg.conf.

---

