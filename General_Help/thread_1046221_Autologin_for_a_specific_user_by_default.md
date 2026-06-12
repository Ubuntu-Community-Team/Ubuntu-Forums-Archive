---
title: "Autologin for a specific user by default"
date: 2009-01-21
forum: General Help
---

### Post by Lety on 2009-01-21
There are lots of messages about autologin, but I can't find how to do (Ubuntu 8.10 64).
I've created unprivileged user and want make him login by default without any login screen (like autologin feature). I also have another user that is an admin. 
Unprivileged user is going to be used only for browsing, editing documents, listening to music and watching movies.
If needed to do some settings/administration, then I log off user and login my admin account.
The problem is that autologin works only if there is only one user on the system.

Does anybody know how to make it possible to autologin the specific user straight to the desktop when the machine starts, and then switch to more privileged user if required ?

---

### Post by amauk on 2009-01-21
System > Admin > Login Window

Under the Security tab
check "Enable automatic login"
select user from dropdown list

you can also set the timed login, if you wish
(will logon as selected user after x seconds)
will give you a chance to enter different user if you wish (so you don't auto login as one user, only to immediately log out and back in as another)

---

### Post by sisco311 on 2009-01-21
(Somewhere in the menu ->)Login Window -> Security -> Enable Automatic Login
or:
```
gksu gdmsetup
```
you need admin privileges to change the settings.

---

### Post by Lety on 2009-01-22
Thanks **amauk** and **sisco311**, now it's working.
I tried to find this in Users and Groups menu item instead of going to Login Window :)

---

