---
title: "No composite extension?"
date: 2007-05-22
forum: Desktop Environments
---

### Post by Bakudan on 2007-05-22
I've read a lot about this in the past few days but can't seem to find quite what I'm looking for. I just installed Feisty on my laptop with an ATI Radeon Mobility 9600 card and I thought I had everything installed correctly.

When I run...

```
$fglrxinfo
    display: :0.0  screen: 0
    OpenGL vendor string: ATI Technologies Inc.
    OpenGL renderer string: MOBILITY RADEON 9700
    OpenGL version string: 2.0.6334 (8.34.8)
```


```
$glxinfo | grep direct
   direct rendering: Yes
```


But when I call beryl-manager it throws an error (as seen below.)
```


$ beryl-manager
    **************************************************************
    * Beryl system compatiblity check                            *
    **************************************************************
    Detected xserver                                : AIGLX
    Checking Display :0.0 ...
    Checking for XComposite extension               : failed
    No composite extension
    beryl: No composite extension
```

What did I break?

---

### Post by ronocdh on 2007-05-22
I believe you'll have to set up an XGL session for an ATI card. I used [this guide]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") with my X1600 Radeon Mobility.

---

### Post by Bakudan on 2007-05-22
Well I got better results, but still not quite running. I get the following when try to run beryl-manager:
```

** (beryl-manager:17924): CRITICAL **: can't execute beryl-xgl: Success
```


It probably has to do with the fact I didn't quite understand the "disable the universal repository" step. What should I do?

---

### Post by Bakudan on 2007-05-22
For the record I got it fixed. Thanks to this thread.  (The last entry on page 1.)


[http://ubuntuforums.org/showthread.php?t=429090&highlight=can%27t+execute+beryl-xgl]("http://ubuntuforums.org/showthread.php?t=429090&highlight=can%27t+execute+beryl-xgl")

---

