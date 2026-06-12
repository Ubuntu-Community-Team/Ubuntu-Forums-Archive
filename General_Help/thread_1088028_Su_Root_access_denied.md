---
title: "Su: Root access denied"
date: 2009-03-05
forum: General Help
---

### Post by mixtri on 2009-03-05
Hey guys n gals, could someone tell me how to gain root access?

See below for details

albert@albert-laptop:~$ su
Password: 
su: Authentication failure

I do not remember applying a pasword for this. As per example above I used my Sudo password but got the Authentication failure message.
Any clues how to access?

---

### Post by bigb2007 on 2009-03-05
Normally on an ubuntu system you don't do things as root.  You use sudo.  

If you really do want it though, "sudo su -"

---

### Post by taurus on 2009-03-05
To use su, you need to have root password but it is locked as a default.  So, if you want root privilege, use sudo in front of a command and use the same password that you log in with.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by avrilrox on 2009-03-05
Do you want to use the root account?

> sudo passwd root

Enter your password and a new password for root afterwards.

---

### Post by mixtri on 2009-03-05
Blimey! That was exceptionally fast response. Thanks guys.
I'm just trying to install the latest Java JRE app and the instructions ask to use the Su command. I guess I'll try sudo su as recommended by  Bigb2007.

Thanks again guys I love this community!1;)

---

### Post by Tek-E on 2009-03-05
I dont recommend having your root account enabled.
If I were you I would just stick to sudo. But it is your call. 
:)

---

