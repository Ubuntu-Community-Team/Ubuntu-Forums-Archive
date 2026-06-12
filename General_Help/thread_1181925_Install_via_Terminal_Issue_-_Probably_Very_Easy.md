---
title: "Install via Terminal Issue - Probably Very Easy"
date: 2009-06-08
forum: General Help
---

### Post by zacharyrs on 2009-06-08
I am trying to install some things via terminal and I get the following. Anyone want to help a recent ubuntu n00b?

zach@zach-laptop:~$ apt-get install checkgmail
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
zach@zach-laptop:~$

---

### Post by PirateChef on 2009-06-08
> **zacharyrs said:**
> I am trying to install some things via terminal and I get the following. Anyone want to help a recent ubuntu n00b?

zach@zach-laptop:~$ apt-get install checkgmail
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
zach@zach-laptop:~$

You have to be root to install programs.
Use
```
sudo apt-get install checkgmail
```

---

### Post by zacharyrs on 2009-06-08
Does 'sudo' remove the root issue for me? Thank you so much for your help.

---

### Post by iponeverything on 2009-06-08
yes, sudo runs the command as root.

---

### Post by andrew.46 on 2009-06-09
Hi zacharyrs,

A nicely written article on the the use of sudo in Ubuntu can be seen here:

RootSudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

and it is highly recommended reading if you wish to understand the implications of an authorised person assuming root privileges under Ubuntu.

All the best,

Andrew

---

