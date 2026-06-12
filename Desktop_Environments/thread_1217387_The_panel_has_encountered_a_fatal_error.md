---
title: "The panel has encountered a fatal error"
date: 2009-07-19
forum: Desktop Environments
---

### Post by thunderbirdje on 2009-07-19
After login, only the desktop shows up. No panels at all.

The error which is prompted:

```
The panel has encountered a fatal error

The panel could not register with the bonoboactivation server (error code: 1) and wil exit. It may be automatically restarted.
```

I already tried ```
sudo apt-get install --reinstall gnome-panel (and also ubuntu-desktop and libbonobo2-common
```

Does someone know a solution? Do I have to reinstall my whole ubuntu system? :'(

Seeking help...

Thanks!

---

### Post by bhavya_g_mihira on 2011-07-12
Hi all,

Anyone who faces this problem must check if they installed zlib-1.2.5.It was the one that caused the problem for me(That too on a system that had a lot of projects on it).Try uninstalling zlib-1.2.5 and install some older version like 1.2.3 or smth.This solved the problem for me for me when nth else did.

Thanks and regards

Bhavya

---

