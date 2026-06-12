---
title: "[SOLVED] Conky on all cube faces?"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by dpar on 2007-12-17
I did a search, but came up with nothing.

Does anyone know how I can get Conky to show up on all the cube faces in compiz?

---

### Post by santiagoward2000 on 2007-12-17
> **dpar said:**
> I did a search, but came up with nothing.

Does anyone know how I can get Conky to show up on all the cube faces in compiz?

Hi there!
All you have to do is look for the line that says **own_window_hints** and add:
```
sticky
```

So, for example, you would get something like this:
```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

I took this from seldon77's [thread]("http://ubuntuforums.org/showthread.php?t=205865"). Thanks seldon!!
Cheers!

---

### Post by dpar on 2007-12-17
Thank you very much!
Worked like a charm.:)

---

### Post by santiagoward2000 on 2007-12-18
> **dpar said:**
> Thank you very much!
Worked like a charm.:)

You're welcome! :popcorn:

---

