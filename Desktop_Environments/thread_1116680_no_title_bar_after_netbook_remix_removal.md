---
title: "no title bar after netbook remix removal"
date: 2009-04-05
forum: Desktop Environments
---

### Post by joep-vd on 2009-04-05
After uninstalling Netbook Remix, the title bar of maximized windows is closed. What magic do I need to get this back? Thanks! 

BTW: Wouldn't Netbook Remix deserve it's own prefix?

---

### Post by blackened on 2009-04-05
```
killall maximus
```

and/or

```
sudo apt-get remove maximus
```

If you choose not to remove it entirely, then stop it from running on startup by disabling it in System -> Preferences -> Startup Applications.

---

### Post by joep-vd on 2009-04-05
Thanks for your reply. This has fixed the problem!

---

### Post by sopier on 2009-11-07
thanks, it solved my problem too

---

### Post by Firepowerforfreedom on 2010-01-08
Thanks! I've been trying to fix this for days!
If only they'd take that stupid package out of UNR...

---

### Post by blackened on 2010-01-09
> **Firepowerforfreedom said:**
> Thanks! I've been trying to fix this for days!
If only they'd take that stupid package out of UNR...

I think it's a very useful piece of software, but wonder whether or not it should be linked to the UNR meta-package so that they get removed together.

Ideally, it would be nice to be prompted to also remove maximus when removing UNR.

---

