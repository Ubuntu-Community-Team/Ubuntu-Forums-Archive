---
title: "boot up and auto-login to a locked screen?"
date: 2009-03-15
forum: General Help
---

### Post by Andreas1 on 2009-03-15
here's what bugs me:

wait while computer boots --> enter password --> wait while gnome session loads --> do something

one solution would be to disable password prompt but that kind of defeats the purpose of the password. what i would like to have is something like this (since i am the only user):

wait while computer boots and gnome session loads --> enter password and do something

is there a way to achive this? like lock the screen immediately at login?

---

### Post by zvacet on 2009-03-15
If you are only user you can use autologin.It is in** system<admin>login window>security** and there select user for autologin.

---

### Post by Andreas1 on 2009-03-15
> **zvacet said:**
> If you are only user you can use autologin.It is in** system<admin>login window>security** and there select user for autologin.

> **Andreas1 said:**
> 
one solution would be to disable password prompt but that kind of defeats the purpose of the password.

this is not what i want, since autologin means disabling password promt.

---

### Post by KuriKai on 2009-03-15
Maybe make a script with this in it and get it to run on login
```
gnome-screensaver-command --lock
```

---

