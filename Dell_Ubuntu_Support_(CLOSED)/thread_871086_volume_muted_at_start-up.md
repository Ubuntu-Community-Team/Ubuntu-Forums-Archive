---
title: "volume muted at start-up"
date: 2008-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inca99 on 2008-07-26
Hi, I have an Inspiron 1525 running hardy 2.6.24.20. At start-up my master and front volume levels are always at zero, I up them to full but at next start-up they are back to zero again. Is there any way to have the setting remembered? Thanks

---

### Post by RomanIvanov on 2009-08-24
As for workaround you can do

```
/usr/bin/amixer -q set Master 100% unmute
```

I put this in launcher on Desktop, I failed to automate this by:startup application,.bash.rc, /etc/rc.local, .. . Still in search for the solution.

---

