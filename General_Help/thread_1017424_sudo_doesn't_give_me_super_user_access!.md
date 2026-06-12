---
title: "sudo doesn't give me super user access!"
date: 2008-12-21
forum: General Help
---

### Post by corn29 on 2008-12-21
Hello:

Since ubuntu is different from other *nix distros where typing "su" from a terminal window doesn't grant root access, I'm a little confused.

I took a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) but that just gives me more questions.  When I follow the webpage, the prompt never changes to a '#'.  The prompt stays a '$'.

Here is a copy of some terminal output:

dogzilla@dogzilla-laptop:~$ sudo -l 
[sudo] password for dogzilla: 
User dogzilla may run the following commands on this host:
    (ALL) ALL
dogzilla@dogzilla-laptop:~$ 

There are no errors, but shouldn't the prompt change from '$' to '#' as an indicator of increased access?

Thanks for your time!

---

### Post by reality1011 on 2008-12-21
to execute root commands you should do sudo <comand>

to become root temporarily you should sudo su

---

### Post by w0ng on 2008-12-21
```
wong@ubuntu:~$ sudo su -
root@ubuntu:~# exit
exit
wong@ubuntu:~$ 
```

For security reasons, it's recommended you stick with sudo rather entering su mode

---

### Post by binbash on 2008-12-21
sudo su - 

will do the trick

---

### Post by ad_267 on 2008-12-21
Or just "sudo -i"

---

### Post by dnairb on 2008-12-21
From the man page:

> The -l (list) option will list out the allowed (and forbidden) commands for the invoking user on the current host.

As ad_267 above says, you need is **sudo -i**

---

### Post by monkeyking on 2008-12-21
sudo -s also works.

I don't really know the difference of these sudo argumants

---

