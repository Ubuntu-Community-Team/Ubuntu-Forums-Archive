---
title: "Englightened KDE"
date: 2005-12-12
forum: Desktop Environments
---

### Post by veloct on 2005-12-12
Has anyone tried this yet? If so, how?

---

### Post by daller on 2005-12-14
Could you explain your problem a little better?

---

### Post by ltmon on 2005-12-14
I think he's talking about running parts of Enlightenment (or e17) inside KDE or vice-versa.

Haven't tried this myself.

L.

---

### Post by Sokraates on 2005-12-14
"Enlightened KDE" would mean exchanging the K-windows manager for E17. Just as for [XFCE](http://ubuntuforums.org/showthread.php?t=101066) or [GNOME](http://ubuntuforums.org/showthread.php?t=54476).

Only thing I don't kow is, whether it is possible to change the K-windows manager at all. :confused:

---

### Post by afhp on 2005-12-14
[QUOTE=Sokraates]Only thing I don't kow is, whether it is possible to change the K-windows manager at all. :confused:[/QUOTE]

From /usr/bin/startkde :

```

# finally, give the session control to the session manager
# if the KDEWM environment variable has been set, then it will be used as KDE's
# window manager instead of kwin.
# if KDEWM is not set, ksmserver will ensure kwin is started.

```

Never actually tried it. I like kwin :)

---

### Post by veloct on 2005-12-14
I was just wondering really.  I don't have any issues with kwin at all.

---

### Post by Sokraates on 2005-12-15
So I'm using kwin ... good to know. ;) 

Maybe a dumb question but I'll ask anyway: what's the difference between kwin and session manager (visuals, features etc.)?

---

