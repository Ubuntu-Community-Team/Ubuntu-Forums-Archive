---
title: "[SOLVED] How do I restart compiz?"
date: 2008-03-09
forum: Desktop Effects &amp; Customization
---

### Post by jakev383 on 2008-03-09
I get "ghosts" left over from the fading effects of compiz fusion.  How can I restart JUST compiz without restarting X/rebooting/logging out and logging back in?  Here's the output of ps aux:
```
jake@jake-desktop:~$ ps aux | grep compiz
jake      5958  0.0  0.0   1756   540 ?        S    Mar06   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
jake      6090  0.7  2.2  86428 46484 ?        SL   Mar06  28:34 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 ccp
```
Any help is appreciated.

---

### Post by sisco311 on 2008-03-09
Alt+F2
```
compiz --replace
```

---

### Post by jakev383 on 2008-03-09
Thanks!
For some reason it killed Firefox when I did it, but not Thunderbird. 'Course Firefox seems to have crashy-pants on lately.
Thanks again!

---

