---
title: "cvscedega problem"
date: 2006-09-01
forum: Gaming &amp; Leisure
---

### Post by m0rfin on 2006-09-01
When i type the command cvscedega in terminal i get this message
```
wine: '/home/m0rfin/.cvscedega/wineserver-m0rfin-desktop' is not owned by you

```

Im new to ubuntu and i would like someone to tell me how to fix this problem. thx

---

### Post by justin whitaker on 2006-09-01
> **m0rfin said:**
> When i type the command cvscedega in terminal i get this message
```
wine: '/home/m0rfin/.cvscedega/wineserver-m0rfin-desktop' is not owned by you

```

Im new to ubuntu and i would like someone to tell me how to fix this problem. thx

Tr4veler posted this over in the ut2004 mod thread

> sudo chmod -R a+rwx Action

Should do what you need.

Note: that gives all users read write and execute permissions for everything in and under that directory.

ln -s [wine directory] [linux directory]

You need to reset the permissions on the folder so that you can access it.

---

