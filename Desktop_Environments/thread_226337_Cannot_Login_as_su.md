---
title: "Cannot Login as su"
date: 2006-07-31
forum: Desktop Environments
---

### Post by BluesMan2 on 2006-07-31
Basically i type su in the console and it asks for my password. The only password i have ever set on the system is my logon password for my user acount. This doesnt work for su control (suprise suprise) so i wondered how i set my root password?

---

### Post by x64Jimbo on 2006-07-31
You can't log in as root in Ubuntu unless you create a password for root (not recommended)
Instead, if you want to remain logged in as root, you should use this command:
sudo su
then type your password, and for the remainder of that session, you will perform actions as root. Remember that most commands do NOT need root access, so you shouldn't need to log in as root for an entire session, especially since your terminal should remember your password for a good 10 minutes after your first sudo.

---

### Post by BluesMan2 on 2006-07-31
cheers, i understnad root is dangerous :p

---

### Post by Riverside on 2006-07-31
> **x64Jimbo said:**
> You can't log in as root in Ubuntu unless you create a password for root (not recommended)A traditional root account is necessary for certain things, though (initial client configuration of a Juniper SSL VPN is one that immediately springs to mind).

One can enable the root account (for example, to perform the action referred to above) and then disable it immediately afterwards, following the advice at:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

