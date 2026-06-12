---
title: "Creatting a new account"
date: 2009-05-10
forum: General Help
---

### Post by Ravernomina on 2009-05-10
hello.... I need to make an account for my mom because she if forcing me :l. i tried using the "useradd" command and i also made a home directory but idk what the next step is could some 1 tell me please. TYVM!!
    Ravernomina :popcorn:

---

### Post by sisco311 on 2009-05-10
You are looking for the adduser command.

Adding users with adduser is much easier than adding them by hand. Adduser will choose appropriate UID and GID values, create a home directory, copy skeletal user configuration, allow you to set an initial password and the GECOS field.

```
sudo adduser username
```

You can delete a user with *deluser*.

Read the man pages for more details:
```
man adduser
man deluser

```

---

### Post by Ravernomina on 2009-05-10
Bump!

---

### Post by Sef on 2009-05-10
> hello.... I need to make an account for my mom because she if forcing me :l. i tried using the "useradd" command and i also made a home directory but idk what the next step is could some 1 tell me please. TYVM!!

System > Administration > Users and Groups

---

