---
title: "[SOLVED] Disable user list on login"
date: 2013-11-20
forum: Desktop Environments
---

### Post by martro on 2013-11-20
I'd like to disable users list on login.
I've tried [this]("http://askubuntu.com/a/187946") but does not working.
[CENTER][ATTACH=CONFIG]247946[/ATTACH]
[/CENTER]
 
Now my /etc/lxdm/default.conf (/etc/lxdm/lxdm.conf does not exists!) is

```
## if disable the user list control at greeter
disable=1
```

What's wrong?

---

### Post by steeldriver on 2013-11-20
Are you sure your system uses lxdm? newer versions of Lubuntu use lightdm by default, I think

---

### Post by martro on 2013-11-20
> **steeldriver said:**
> Are you sure your system uses lxdm? newer versions of Lubuntu use lightdm by default, I think

Oh yes, that's [true]("http://askubuntu.com/a/68968")

---

