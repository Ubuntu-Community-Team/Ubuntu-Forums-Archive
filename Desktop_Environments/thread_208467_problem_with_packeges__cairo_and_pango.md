---
title: "problem with packeges : cairo and pango"
date: 2006-07-03
forum: Desktop Environments
---

### Post by benny@linux on 2006-07-03
when i tryed to install LIBGTK-DEV pack i get this msg in synaptic:

[COLOR="Green"]libgtk2.0-dev:
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libcairo2-dev but it is not going to be installed
[/COLOR]
what to do? , 
if i try to install one of the missings packs - say cairo i get this msg :

[COLOR="Green"]libcairo2-dev:
  Depends: libcairo2 (=1.2.0-0ubuntu1) but 1.1.10-0ubuntu1 is to be installed
[/COLOR]

---

### Post by Jagot on 2006-07-03
Try:

```
sudo aptitude -f install libgtk2.0-dev
```

---

### Post by benny@linux on 2006-07-03
thank you i am trying this now , in the meanwhile can you tell me what aptitude -f install mean?

i just want to know what was the problem with my synaptic/ubuntu and how i fixed it :)

---

### Post by Jagot on 2006-07-03
It's force install.

From the man pages:

Try hard to fix the dependencies of broken packages, even if it means ignoring the actions requested on the command line.

Basically depenencies can sometimes cause problems that cannot be resolved, so, you just force install it to get around this - sometimes it will ignore dependencies, but it usually works.

---

