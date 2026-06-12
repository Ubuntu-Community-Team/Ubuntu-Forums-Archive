---
title: "When I start compiz --replace nothing happens"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by swoll1980 on 2007-07-29
When I ran beryl in feisty it worked fine. When I try to run it in gutsy I get a white screen. When I try running compiz-fusion I get this error message

/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't                                                             going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Any Ideas?

---

### Post by phetre on 2007-08-01
Hi swoll1980,

I had the same message earlier tonight, and it seemed to be because my direct rendering wasn't enabled. The following command will tell you whether or not it's enabled on your system: ```
glxinfo | grep "direct rendering"
```
If not, try installing libgl1-mesa-dri.

Incidentally, I still can't get compiz-fusion to run on my machine (first-gen Macbook), but that got me closer.

---

