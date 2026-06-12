---
title: "UserAdd"
date: 2006-02-27
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-02-27
OK - I tried adding a new shell user today and noticed that when I issue the command, it does not ask for their password nor does it create a /home directory for that new user.

```
root@notebook:/home/carlos# useradd laura
root@notebook:/home/carlos# cd /home/
root@notebook:/home# ls
carlos

```

---

### Post by midwinter on 2006-02-27
Because you are not using the appropriate switch/es.

man useradd

(you likely want -m for the home dir, i.e useradd -m newusername), then set the password with passwd newusername

---

### Post by CarlosinFL on 2006-02-27
Thanks!

---

### Post by shakin on 2006-02-27
If you use 'adduser' instead, you will get the results you are looking for.

---

### Post by CarlosinFL on 2006-02-27
Ah, so there is a "useradd" and a "adduser" command. How confusing.

---

### Post by svref on 2006-02-27
Sorta related issue...I'm toying with the idea of (gasp) using the GUI to add new users.  However, this doesn't read /etc/adduser.conf, and thus misses my pref to create new users in /roam/$user instead of /home/$user.   Hum ho. :P

---

