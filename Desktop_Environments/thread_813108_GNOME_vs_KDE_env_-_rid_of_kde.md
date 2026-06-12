---
title: "GNOME vs KDE env - rid of kde"
date: 2008-05-30
forum: Desktop Environments
---

### Post by josh6847 on 2008-05-30
I had gnome running originally and installed kde. All it did was made the login use kde and then when I'm actually logged in, the desktop setup is gnome but it just has some kde apps. I tried just selecting gnome on the login but it doesn't default to gnome when I restart or log back in. How can I get rid of kde all together and just run gnome again? (I know I could just uninstall kde but I am looking for the workaround) Also, is my performance being effected by having "both" environments running?

Thanks,
Josh

---

### Post by dje on 2008-05-30
Have a look [here]("http://psychocats.net/ubuntu/puregnome")

hope that helps,
dje

---

### Post by Xiong Chiamiov on 2008-05-30
If you want to change which environment you log in to, you have to choose the appropriate session when you log in.  If you want to change which login manager you use, run
```

sudo dpkg-reconfigure gdm

```
and choose gdm to be the default.

---

