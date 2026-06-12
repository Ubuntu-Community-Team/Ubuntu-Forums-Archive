---
title: "Cannot save Hosts file"
date: 2008-12-23
forum: General Help
---

### Post by toms33 on 2008-12-23
I am trying to save a hosts file I edited and I get the error message:

You do not have the permissions necessary to save the file.

How to I save this file.

Please describe in detail the steps and what to type in where.

*Please note I am running Ubuntu 8.10 in VMware, if that makes any difference or not.

---

### Post by toms33 on 2008-12-23
Please don't post links to similar topics I have read them all and have no Idea what they are talking about.

---

### Post by jocko on 2008-12-23
To be able to make changes to /etc/hosts (or any other file outside of your home directory), you need to have root permissions, which you get by using sudo or gksudo.
So, to edit the /etc/hosts file, type this comand in a terminal:
```
gksudo  gedit /etc/hosts
```

---

### Post by Xiangxianni on 2008-12-23
Also you can run command

sudo -s

then input your root password.Then you have the root priviledge.
Take care.

---

### Post by jocko on 2008-12-25
> **Xiangxianni said:**
> Also you can run command

sudo -s

then input your[COLOR=Red] root password[/COLOR].Then you have the root priviledge.
Take care.
There is no root password. With sudo you use your own password.

---

