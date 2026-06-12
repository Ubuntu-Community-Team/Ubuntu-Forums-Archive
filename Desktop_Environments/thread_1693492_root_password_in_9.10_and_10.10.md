---
title: "root password in 9.10 and 10.10"
date: 2011-02-22
forum: Desktop Environments
---

### Post by cjejuni on 2011-02-22
installed 2 desktops, ubuntu 9.10 and 10.10. i do not remember root/password entry during the installation on both pcs. i do not like reaching for the power button when i can shutdown gracefully. until yesterday i 9.10 pc hang up, is there a default root/password combo? my superuser is not recognized to be logged in at the command prompt. how do i enter/change the root/password?
thanks,
cj

---

### Post by ubun2warrior on 2011-02-22
hi 

just open a terminal and then type-  sudo passwd.
then the system will ask for your current user password(the one with which you logged into the system)
then enter the new UNIX passwd.. and ur passwd will change

best of luck !!

---

### Post by Krytarik on 2011-02-23
> **ubun2warrior said:**
> hi 

just open a terminal and then type-  sudo passwd.
then the system will ask for your current user password(the one with which you logged into the system)
then enter the new UNIX passwd.. and ur passwd will change

best of luck !!
The given command would change the password of the current user, because it is run without specifying a user.

See here for further information about enabling the root account, and a big warning:
[https://help.ubuntu.com/community/RootSudo#root%20account](https://help.ubuntu.com/community/RootSudo#root%20account)

---

