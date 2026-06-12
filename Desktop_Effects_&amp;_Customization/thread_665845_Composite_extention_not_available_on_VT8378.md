---
title: "Composite extention not available on VT8378"
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by cool2000m on 2008-01-12
Okay, so I just installed the drivers for my card, But when I tried to enable the desktop effects, it says that the composite extentions are not available. and also, torcs and powermanga won't even open, and when I run compis under terminal I get this:

```
cool2000m@cool2000m-desktop:~$ compiz
aborting and using fallback: /usr/bin/metacity 
```

Does anyone know a fix for this?

---

### Post by cool2000m on 2008-01-18
um...hello? anybody there?

It says "no whitelisted driver" now.

---

### Post by cool2000m on 2008-01-19
I added my card to the compiz file, and now x restarts every time I run it.

---

### Post by Ub1476 on 2008-01-19
Remove your driver from the configuration file and install xserver-xgl, then re-login.

---

### Post by cool2000m on 2008-01-19
by "it" i meant compiz... 
so if i take it out, it'll run fine?

---

### Post by Ub1476 on 2008-01-20
Yes, edit the file you modified, and install XGL. When it says "No Composite Extension Available" it always mean that XGL is not installed.

---

### Post by cool2000m on 2008-01-24
I did this and I can no longer log on, except in failsafe mode...

---

