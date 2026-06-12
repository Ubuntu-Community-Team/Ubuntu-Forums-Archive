---
title: "Startup Display Problem"
date: 2010-09-13
forum: Desktop Environments
---

### Post by jim_deadlock on 2010-09-13
I'm not sure what I did to cause this but lately whenever I start my computer, my mouse pointer is a black 'X' and my windows have no title bar. I can fix this by going to System -> Preferences -> Appearance -> Visual Effects -> select Normal (it's usually set to None), it then tries to search for drivers for a while and then my title bars reappear and my proper mouse pointer returns (the Visual Effects stay on None which is what I want).

Is there something I need to reinstall or reset so that I don't have to keep doing this every time I reboot?

---

### Post by jim_deadlock on 2010-09-15
I've tried messing around with xorg.conf and switched from compiz to metacity, none of these have any effect on the problem. Any pointers or suggestions would be much appreciated.

---

### Post by jim_deadlock on 2010-09-15
I'm making some progress. I had a warning that my windows manager was no loaded, so I've installed compiz fusion icon and when I use it to reload windows manager it fixes the problem. Now all I need to know is how to make my system load the windows manager (compiz) on startup...?

---

### Post by jim_deadlock on 2010-09-15
This turned out to be the culprit:

~/.local/share/applications/metacity.desktop

```
Hidden=true
```Removing that line fixed it. Here is the thread that led me to it:

[http://ubuntuforums.org/showthread.php?t=1466754](http://ubuntuforums.org/showthread.php?t=1466754)

---

