---
title: "Compiz &quot;last known good&quot; fallback"
date: 2009-04-06
forum: Desktop Environments
---

### Post by Nathanael Culver on 2009-04-06
The last couple of days I've been poking around in CSM just to see what's there, and a couple of times now I've farkled X-Windows by enabling some setting or other my hardware apparently doesn't support, so badly in one case I could no longer log into my account and had to create a new account for myself.

Is there any way to force Compiz to remember a "last known good" configuration, or set a fallback window manager in case Compiz gets hosed?

[And, BTW, in which forum should I be posting Compiz questions?]

--Nathanael

---

### Post by gettinoriginal on 2009-04-06
Store this away for future use, it resets compiz to all default settings via terminal:  :p
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by Nathanael Culver on 2009-04-08
Hey, thanks! If I'd only known :-)

--Nathanael

---

