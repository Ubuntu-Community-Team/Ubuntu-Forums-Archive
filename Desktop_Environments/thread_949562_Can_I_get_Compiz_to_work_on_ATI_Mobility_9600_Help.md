---
title: "Can I get Compiz to work on ATI Mobility 9600? Help needed..."
date: 2008-10-16
forum: Desktop Environments
---

### Post by hegenious on 2008-10-16
:KS

I am running 8.04 on a Compaq NC8000.
It has an ATI Mobility Radeon 9600.
The graphix HW seems unable to run any Desktop effects on this laptop.
Is there a way for me to have Compiz run on this hardware? Please help! :confused:

---

### Post by ossi on 2008-10-30
Can you understand German? Then look here:

[http://forum.ubuntuusers.de/topic/compiz-mit-ati-auf-laptop/?highlight=ossi#post-1365454]("http://forum.ubuntuusers.de/topic/compiz-mit-ati-auf-laptop/?highlight=ossi#post-1365454")

Just try if it works when you type in console 

```
SKIP_CHECKS=yes compiz --replace
```

When that works, create yourself a file under 

```
~/.config/compiz/compiz-manager
```

and write in it:

```
SKIP_CHECKS=yes
```

---

