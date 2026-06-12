---
title: "daperdrake + compiz/xgl + twinview"
date: 2006-05-30
forum: Desktop Environments
---

### Post by nami on 2006-05-30
HI

Just like to say that I am looking forward to the release of dapper drake.  Thanks for such a great comunity!

I have seen some screenshots of dapper drake + compiz/xgl.

I was wondering if dapper drake + compiz/xgl will work across an extended desktop across 2 monitors (twinview)?

nami

---

### Post by renzokuken on 2006-05-30
i seem to remember reading somewhere the installing compiz/xgl breaks twinview.....

i think it was in the first post of the XGL/Compiz "thread to rule them all" or one of the links contained in it

---

### Post by Gort32 on 2006-05-30
You can use multiple screens easily - your old configuration should work just fine. xinerama and twinview's builtin equivelent, however, are broken.  In other words, you can have your desktop span multiple monitors but your window manager will not be aware of the break between your monitors.  It will basically perceive your multimonitor desktop as one big monitor.  So, whenever you maximize a window it will maximize it across all of you rmonitors.  Rather annoying, actualy, but you can still use multiple monitors if you really want to.

---

### Post by Scunizi on 2006-05-30
Actually Gort32,  It doesn't seem to work that way on my machine.  I've activated xinerama and although some smaller program boxes pop up between the two monitors, I can maximize them on one monitor without the spanning.  I'm running a PNY 6600gt.  I find after using dual monitors that it's really hard to live without them even with a few minor quirks.

---

### Post by RAOF on 2006-05-30
The latest CVS of compiz & XGL support xinerama, so if you're getting packages from somewhere other than Ubuntu universe (like the Quinnstorm repositories, or anything from compiz.net), you'll have (some sort of) xinerama support.  It's pretty new, so don't expect it to work flawlessly, but it's there ;)

---

### Post by nami on 2006-05-31
I am still using Ubuntu 5.10.  I was waiting for the actual release of 6.06 before I try this.  Will it be fixed by the time Ubuntu 6.06 is released?

---

### Post by Gort32 on 2006-05-31
Indeed, Scunizi and RAOF are right - I was using old information.
[http://compiz.net/viewforum.php?id=3](http://compiz.net/viewforum.php?id=3)

---

### Post by cykematica on 2006-05-31
i have compiz/xgl running on an nvidia geforce fx5500 with twinview flawlessly.  no spreading inbetween screens.  has been working like that for a few weeks now.

---

### Post by nami on 2006-05-31
Can't wait for the final release of dapper drake! :D

---

