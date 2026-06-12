---
title: "mythtv configuration"
date: 2006-02-26
forum: Desktop Environments
---

### Post by ravalox on 2006-02-26
Okay, so MythTV is installed via the repositories.  I have to use sudo to run mythbackend in order to run mythtv.  In Ubuntu there is no "root" user, so the init.d script for mythtv I think tries to use "root" to operate, which it cannot do.  So how to I start a process with "sudo" in ubuntu?

---

### Post by andrewsawyer on 2006-02-26
Could you create a user named root and give it full admn rights?  Other than that I think there is a howto thread on getting root user in the tips and tricks section

---

### Post by toganet on 2006-03-12
Root's always there, you just have to give it a password.  Logged in as your regular user, issue the command

```
sudo passwd root
```

You will be prompted to set the root password.   You can use su or log in to a terminal as root, but GDM still won't let you log in to GNOME.

---

