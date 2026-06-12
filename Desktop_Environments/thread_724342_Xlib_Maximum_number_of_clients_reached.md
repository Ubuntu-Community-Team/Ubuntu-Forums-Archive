---
title: "Xlib: Maximum number of clients reached"
date: 2008-03-14
forum: Desktop Environments
---

### Post by bozzochet on 2008-03-14
Hello to all!

Since few days I have this problem when I try to open grahical application:

```
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
```

Normally this appear when I open an appliction when I have another one opened...

Few days ago this appened with compiz BUT NO without it, now it happens always... I also disintalled compiz but the problem is still present.

Any idea?!

---

### Post by bozzochet on 2008-03-31
It was an error in ksmserver. I hat to remove ~/.kde/share/config/ksmserverrc and kde re-generated it at the next boot and then all worked right... I don't know the cause of the problem but since some days when I turned off my PC I have the segnalation of ksmserver crash and I, stupidily, didn't preoccupe because was suffucient to click ok and the PC seems to turn off normally...

---

