---
title: "Unable to run sudo!"
date: 2006-09-15
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-09-15
Hi,i don't know what happened but i cannot run sudo and have to use su root for it.the error says:-
pluto@Neptune:~$ sudo firestarter
sudo: must be setuid root

Help please!!

---

### Post by sheep on 2006-09-15
```

su -c chmod +s /usr/bin/sudo

```

Try that.

---

### Post by Anduu on 2006-09-15
Maybe this can help...

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

