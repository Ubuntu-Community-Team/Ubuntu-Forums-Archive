---
title: "/etc/init.d/rc problem"
date: 2006-07-03
forum: Desktop Environments
---

### Post by yoyozzz on 2006-07-03
I have the next message error while booting the system:

```
/etc/init.d/rcS: /etc/init.d/rc: /bin/sh^M: bad interpreter: No such file or direcotory
/etc/init.d/rcS: line 8: /etc/init.d rc: Success
* INIT: Entering runlevel: 2
* INIT: Cannot execute "/etc/init.d/rc
```

I have changed rc permisses whith chmod (chmod +x rc), but it doesnt work.
Any ideas?

Thanks

I´m spanish, sorry for my english.

---

### Post by yoyozzz on 2006-07-03
I have found the solution. Just replace /etc/init.d/rc from cd to the specifiec destination(/etc/init.d/rc)

---

