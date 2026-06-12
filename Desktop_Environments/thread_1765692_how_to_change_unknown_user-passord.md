---
title: "how to change unknown user-passord"
date: 2011-05-23
forum: Desktop Environments
---

### Post by Azyx on 2011-05-23
Hi. i have an admin-account and an user-account on a computer. It's automatically log in to the user-account, but I have forgott the passwordt. I want to change it, but to how change it? I need the precent. How do i do? I have the admin password.

---

### Post by aphatak on 2011-05-23
Log in with your admin account.  From the command line, enter -
```
sudo passwd <user-id>
```When prompted, enter the new password (the screen will not show the password as you type it), and then enter it again when asked to confirm.  That is it - your password should be changed.

---

### Post by Azyx on 2011-05-23
> **aphatak said:**
> Log in with your admin account.  From the command line, enter -
```
sudo passwd <user-id>
```When prompted, enter the new password (the screen will not show the password as you type it), and then enter it again when asked to confirm.  That is it - your password should be changed.

Thanx. I also notice that if I log in to my admin-desktop I can change the users-accont without present user password in GUI System-->Admin-->Users and Group :)

---

