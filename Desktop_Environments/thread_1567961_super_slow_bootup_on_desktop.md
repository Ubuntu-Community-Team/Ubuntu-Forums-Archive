---
title: "super slow bootup on desktop"
date: 2010-09-04
forum: Desktop Environments
---

### Post by gbestrada on 2010-09-04
):P Hello everyone ,I'm having a problem whit mi pc .
two weeks ago I installed wine on my computer and tried to run
an old video game (governor of poker ). bot the screen went blank and a error message appeared on the screen :: MODE NOT SUPPORTED ' I pressed ESC but nothing happened
I waited a while but nothing happened so I had to force shutdown .After turning back on my machine noticed that i was taking too long to boot (6:00 minutes) , when before that it only took around one minute .My ? is .Is that normal or is there a problem with wine ?

In advance :p:p thanks for any help .;);)

---

### Post by clrg on 2010-09-04
Looks like your wine program was trying to set a resolution and/or refresh rate not supported by your screen(s). 

During boot, what do you see? Just the splash screen not going away?

Or does Ubuntu start successfully, it just takes too long?

The simplest way to find out if this is wine's fault would be to remove it and see if the problem goes away:

```
sudo apt-get remove --purge wine
```

---

### Post by gbestrada on 2010-09-04
I removed  wine from my pc .and everything works perfectly but when I  turn off the computer or restart it, it takes very long to boot .
And that makes me to leave it on all the time . and I wonder if wine  had affected any part of my hard drive:p

---

### Post by gbestrada on 2010-09-04
ubuntu starts successfully . the problem is that it takes too long to boot up after turned off or restarted.

---

