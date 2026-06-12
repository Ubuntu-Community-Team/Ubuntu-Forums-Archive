---
title: "My root password on a LIVE CD?"
date: 2009-04-06
forum: General Help
---

### Post by Hellstudios on 2009-04-06
I am running my live CD to do something in ROOT in the terminal, but it asks for my password and I am running a live CD... how do I get around this???

or what is the default root password for ubuntu 8.10 LIVE?

---

### Post by jespdj on 2009-04-06
You can't login as root. Ubuntu does not use the root account. You can use **sudo** if you need to do anything as root, see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As far as I know, the password on the live CD is empty. Just press Enter when it asks for a password after entering "sudo <command>".

---

### Post by Hellstudios on 2009-04-06
I did that, and I pressed enter multiple times. this is what happens:


```

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 


```

---

### Post by Hellstudios on 2009-04-06
Never mind I got it. last time it asked for passwords.


thanks.

---

### Post by boof1988 on 2009-04-06
> **Hellstudios said:**
> I did that, and I pressed enter multiple times. this is what happens:


```

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# 


```

When the last part of the prompt changes from a $ to a #, it means the user is running as superuser(root?).

Also, the *user* (in the case above) changes from ***ubuntu*** to ***root***

---

