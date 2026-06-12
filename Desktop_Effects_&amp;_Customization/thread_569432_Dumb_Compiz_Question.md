---
title: "Dumb Compiz Question"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by derekr44 on 2007-10-07
I have a script to start Compiz:

```
#!/bin/bash
compiz --replace &
sleep 5
emerald --replace
```

How can I create a script that stops it?

---

### Post by amadeus266 on 2007-10-07
try this:
```
#!/bin/bash
if ps ax | grep -v grep | grep compiz.real > /dev/null
then
killall compiz.real && xfwm4
else
compiz --replace
fi
```

This is what I use as a toggle switch.

---

### Post by eentonig on 2007-10-07
I guess you're running Xubuntu?

---

### Post by derekr44 on 2007-10-07
> **eentonig said:**
> I guess you're running Xubuntu?

Nope, vanilla Ubuntu.  Compiz works great.  I just have problems running full-screen games in Wine with it.  So I need to shut it down prior to playing.  Re-logging gets old after awhile.

---

### Post by Forlong on 2007-10-07
Just hit [Alt]+[F2] and run ```
metacity --replace
```

You can also use that command for a starter in the panel or on the desktop.

---

### Post by derekr44 on 2007-10-07
Thank you, Forlong.  That was perfect!

---

