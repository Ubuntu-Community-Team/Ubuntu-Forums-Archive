---
title: "KDE won't load after login"
date: 2010-04-24
forum: Desktop Environments
---

### Post by matmatmat on 2010-04-24
Hi everyone, I've just tried installing KDE4.4 from [this]("http://www.webupd8.org/2009/12/how-to-install-kde-44-beta-in-ubuntu.html") guide. I logged out and tried to login with KDE but after a couple of seconds the screen went black and then it went back to the login screen. I am using Ubuntu 9.10

Can somebody please help?

---

### Post by matmatmat on 2010-04-25
Bump?

---

### Post by Zorael on 2010-04-25
Check **/var/log/kdm.log**, see if it lists any reason.

You'll also want to make sure all packages are updated. If you need to log in to get a working connection it's a bit tricky. If you're on a wired connection and it sets itself up automatically, it's considerably easier.
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```

---

