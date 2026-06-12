---
title: "super user requires sudo!!!"
date: 2009-03-23
forum: General Help
---

### Post by houcem on 2009-03-23
su command asks for authentication I enter my password or the root password I've tried all my passwords (even my gmail password) but it always fails. However when I type sudo su the authentication is accepted. Can you explain why??

---

### Post by Perfect Storm on 2009-03-23
Because Ubuntu uses sudo instead of su

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bachstelze on 2009-03-23
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mcduck on 2009-03-23
In simple words, "su" aks for target user's password (root password in this case) while "sudo" asks for password of the user who runs the command.

Since you don't have the root password, you can't use "su". (root account isn't enabled by default in Ubuntu, and s´you should not even need to enable it)

If you want to run a root session in a terminal the best way is to use "sudo -i" This loads root's environment correctly while "sudo su" doesn't.

---

