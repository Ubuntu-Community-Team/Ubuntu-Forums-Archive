---
title: "Root problem"
date: 2006-09-18
forum: Desktop Environments
---

### Post by freak4pc on 2006-09-18
Hey there everyone
i have a problem with going super-user through the terminal,
when im starting Synaptic , i input my standard password for root and it works

but when im in terminal and i write "su" and my password, it doesnt work , and if i try logging out and then logging back in as "root" and "my password" , it doesnt work either.

When i installed ubuntu dapper it asked for only 1 password , not for 2 , so i have no idea what to do ...

So please help :)
Shai.

---

### Post by amo-ej1 on 2006-09-18
try *sudo su -* to open a root shell

---

### Post by RAOF on 2006-09-18
The root account is disabled by default in Ubuntu.  The replacement is **sudo**, which uses your own password.  For more details, and justification, check out:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ayoli on 2006-09-18
by default, root is not enabled on ubuntu. the password you have set during the intall is your user password. this primary user can grant root privileges by using sudo + your user password.
maybe you should read this page:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by andb on 2006-09-18
If you cant even use sudo then one possibility would be to boot into recovery mode and edit /etc/sudoers. There is an application, visudo to edit this file.

you'll need to be in the admin group and have  a line like this:
%admin ALL=(ALL) ALL

or

USERNAME    ALL=(ALL) ALL

Either would just go at the end. This opens full root privlidges for the user.

I often use sudo -s -H to open a root shell, but really only when needed. Its  easy to be distracted and forget its open...

---

### Post by Najand on 2006-09-18
> **amo-ej1 said:**
> try *sudo su -* to open a root shell

If you want su, use:
```

sudo -s

```
and then enter your user password.

---

### Post by freak4pc on 2006-09-18
Thanks everyone alot! :) very helpful info :biggrin: 

Shai. :lol:

---

