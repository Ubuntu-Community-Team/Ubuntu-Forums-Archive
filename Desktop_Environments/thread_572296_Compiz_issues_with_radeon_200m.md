---
title: "Compiz issues with radeon 200m"
date: 2007-10-10
forum: Desktop Environments
---

### Post by arjones85 on 2007-10-10
I got xgl to load, however upon logging in the desktop is extremely corrupted looking, can't make out anything. 

russell@schoollaptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


This is with THE latest ati drivers downloaded from ati's website, and running fine.

Any help would be greatly appreciated. It is my understanding that I need to get the "direct rendering" section to say "yes." I started following a tutorial but it was for edgy and not feisty, so I did not want to take the chance of messing feisty up.

Any help would be greatly appreciated!

Thanks!

---

### Post by swisscow on 2007-10-10
Can't help with XGL but I have heard ATI are issuing new drivers in the next few days which will mean ATI cards can use AIGLX and Compiz!!!!

I will wait in anticipation

---

### Post by arjones85 on 2007-10-10
What is aiglx?

---

### Post by swisscow on 2007-10-11
Good question, bit like asking what is xgl.

Makes compiz work without a lot of pratting around.

---

### Post by floke on 2007-10-11
See my post here

[http://ubuntuforums.org/showthread.php?p=3505333#post3505333](http://ubuntuforums.org/showthread.php?p=3505333#post3505333)

---

