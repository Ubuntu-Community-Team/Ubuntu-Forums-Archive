---
title: "Ubuntu: Keeps asking for root password"
date: 2009-09-16
forum: Desktop Environments
---

### Post by deep_blue on 2009-09-16
Whenever I try to do something, like installing an application or doing something that is related to root, Ubuntu asks for password. Is there a way I can disable this or can I become root user myself so that ubuntu doesn't ask for password again and again.

---

### Post by lisati on 2009-09-16
Have a read here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
If you still have questions, feel free to ask

---

### Post by earthpigg on 2009-09-16
> **deep_blue said:**
> Whenever I try to do something, like installing an application or doing something that is related to root, Ubuntu asks for password. Is there a way I can disable this or can I become root user myself so that ubuntu doesn't ask for password again and again.

typing this command in a terminal will make that a root terminal until you close it. anything ran or launched from there will be done as root.

beware: a typo here can ruin your system.

a mis-click in a GUI app can also ruin your system.

```
sudo su
```

---

### Post by badger_fruit on 2009-09-22
> **deep_blue said:**
> Whenever I try to do something, like installing an application or doing something that is related to root, Ubuntu asks for password. Is there a way I can disable this or can I become root user myself so that ubuntu doesn't ask for password again and again.

It should also ask if you wish to remember the authorisation in the same prompt.
You can also edit the System > Preferences > Authorisations

**DO NOT LOG IN AS ROOT!!!**

---

