---
title: "password timeout time"
date: 2006-02-23
forum: Desktop Environments
---

### Post by rfruth on 2006-02-23
Ok this must be in a sticky / howto / FAQ but I can't find it so here goes, I like the fact that breezy asks for my password when the package manager an update (whatever) runs but 10 minutes (whatever the default is) is a bit short for me, what file do I edit to change this ?

---

### Post by shams2 on 2006-02-23
as root in a terminal type:
visudo
add this line to the end of file replace the user_name with your user name, save and exit:
user_name   ALL=(ALL) NOPASSWD:ALL
it will never ask for the password.

---

### Post by rfruth on 2006-02-23
Thanks shams2 can I switch to 20 min not never ?

---

### Post by cwaldbieser on 2006-02-23
[QUOTE=rfruth]Thanks shams2 can I switch to 20 min not never ?[/QUOTE]
I think if you add the following line to /etc/sudoers:
```

Defaults     timestamp_timeout=20

```
that will do it.  

However, since fooling around with the /etc/sudoers file is a good way to lock yourself out of root privledges if you make a typo, I recommend that you have a root shell open elsewhere.  If not, make sure you know how to boot into recovery mode in order to fix things if they go wrong!

---

### Post by nanotube on 2006-02-23
and btw, the default is 15 min, not 10 min, afaik. :)

---

### Post by ardchoille on 2006-02-23
[QUOTE=shams2]as root in a terminal type:
visudo
add this line to the end of file replace the user_name with your user name, save and exit:
user_name   ALL=(ALL) NOPASSWD:ALL
it will never ask for the password.[/QUOTE]
That is extremely dangerous as that makes him root all the time. If someone breaks into his computer, they can run "rm -rf /" (which effectively trashes the entire system) whenever they felt like it. They could even take over the system completely by creating a new admin account with a different password and locking his account. There is a reason for the sudo password and if you disable it, then you are disabling all security in the system.

---

### Post by rfruth on 2006-02-24
Thanks for all the feedback, think I'll leave my sudoers file alone for now :rolleyes:

---

