---
title: "Root password"
date: 2004-11-30
forum: Desktop Environments
---

### Post by artAlexion on 2004-11-30
What is the root password.  Sometimes sudo isn't enough and the user password isn't accepted.  Examples are Firestarter and Webmin.  In those cases, how do I set or find the real root password?

---

### Post by kris kincaid on 2004-11-30
Good question. I was unpleasantly surprised to find out I didn't know it!

---

### Post by artAlexion on 2004-11-30
[QUOTE=kris kincaid]Good question. I was unpleasantly surprised to find out I didn't know it![/QUOTE]
 Someone sent me to the following excellent starter how-to:

[http://kitech.com.my/ubuntu/4.10/index.html#setchangerootpassword](http://kitech.com.my/ubuntu/4.10/index.html#setchangerootpassword)

---

### Post by FLeiXiuS on 2004-12-01
[QUOTE=artAlexion]Someone sent me to the following excellent starter how-to:

[http://kitech.com.my/ubuntu/4.10/index.html#setchangerootpassword](http://kitech.com.my/ubuntu/4.10/index.html#setchangerootpassword)[/QUOTE]


To set the root password you may:

```
sudo passwd root
```

Then to login:

```
su -
```

---

### Post by vinz on 2004-12-01
If you only want a root-shell, type
```
sudo -s
```

---

### Post by adbak on 2004-12-01
For Firestarter, right click on the icon in the panel and change it from "gksu" to "gksudo".

---

