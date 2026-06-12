---
title: "Autologin doesn't work"
date: 2020-09-17
forum: Desktop Environments
---

### Post by toug2 on 2020-09-17
Hi,
I trying to have autologin, but it doesn't work (sometimes, it does :) )

Here is the content of lightdm.conf
```

myuser@myuser-HP-EliteBook-8570p:~$ cat /etc/lightdm/lightdm.conf
[Seat:*]
autologin-user=myuser
autologin-user-timeout=0
pam-autologin-service=lightdm-autologin


```

Please help!

---

### Post by ActionParsnip on 2020-09-17
[https://www.maketecheasier.com/enable-autologin-lightdm/](https://www.maketecheasier.com/enable-autologin-lightdm/)
Seems you need to specify the session name

---

### Post by toug2 on 2020-09-18
> **ActionParsnip said:**
> [https://www.maketecheasier.com/enable-autologin-lightdm/](https://www.maketecheasier.com/enable-autologin-lightdm/)
Seems you need to specify the session name

What is the difference between user and session name?

---

### Post by ActionParsnip on 2020-09-18
user is the username you log in with
session is the name of the session, such as Lubuntu, Gnome-shell, XFCE and sets the desktop environment for you. If you log in normally and run
```

env

```
it should show the session name

---

