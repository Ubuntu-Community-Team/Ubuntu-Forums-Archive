---
title: "Super-User"
date: 2005-12-11
forum: General Help
---

### Post by madsalty on 2005-12-11
I know i have started a thread similiar to this before and that i already have answers however, me being a noob to linux i didn't understand the instructions. could somebody please show me in a simple way (maybe screenshots) how to set the super-user so as i can install my sound card and graphics card drivers.

---

### Post by Leif on 2005-12-11
just type "sudo" before any command that requires the super user. see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by nlindblad on 2005-12-11
You mean to skip the "root-by-sudo"-mechanism and allow ordinary su or login as root?

```
sudo passwd root
```

I'd rather recommend getting into a root-shell by doing:

```
sudo su -
```

(I think GNOME has a super-user-terminal aswell)

---

### Post by madsalty on 2005-12-11
Can you show me how to do that with Screenshots because i am very confused

---

### Post by Leif on 2005-12-11
could you post which thread you're trying to follow ? but assuming that you want to run command "X" as root (super user), do this :

click applications->accessories->terminal

in that terminal window, type "sudo X", then enter your usual password

---

