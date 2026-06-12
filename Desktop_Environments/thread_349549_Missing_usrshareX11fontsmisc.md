---
title: "Missing /usr/share/X11/fonts/misc"
date: 2007-01-30
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2007-01-30
Hey all.

I installed Edgy last night. and I'm trying to setup vnc but apparently I'm missing the dir /usr/share/X11/fonts/misc (as well as /fonts).  Any ideas on how I fix this?  I believe it's causing vnc to not start up correctly.

Thanks.

A

---

### Post by grumpymole on 2007-01-31
A,

> /usr/share/fonts/X11/misc is the path you should use for fonts.  You should get error messages relating to font paths if this is the problem.

You should be aware that vnc4server is currently broken in Edgy (and Feisty) with the latest updates.  Here is [the bug.]("http://launchpad.net/bugs/78282")  The only workaround I have seen is to downgrade vnc4server to the earlier edgy version.  ```
sudo apt-get install vnc4server/edgy
```

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by 11hjpphty76lkjj on 2007-02-01
Thanks. That worked.

A

---

