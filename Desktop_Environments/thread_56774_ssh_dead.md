---
title: "ssh dead"
date: 2005-08-14
forum: Desktop Environments
---

### Post by usergentoo on 2005-08-14
When i try to connect laptop to  pc1 it keep saying permission denied.
When I connect the laptop to the server it works. When I connect the server to the laptop it works. But when I try to connect pc1 to either my laptop or server it says permission denied. The same happens for the server to pc1.

Now ive removed all keys form all computers and rebooted them all and still the same. Ive also removed ssh from pc1. It seems like pc1 is messed up.
In other words pc1 will not connect to the other pc's and the other pc's cant connect to it.

It worked before I did this major upgrade. I went to install a package and it had a bunch of packages to be upgraded so I did that. This is when it started having the problem.

Any ideas of something else I can remove or try. And yes it still can go online so its not the network.

---

### Post by nad on 2005-08-14
Is there any information in your log file /var/log/auth.log ?

Have you tried with the -l argument to connect as a specific user?

Is your password correct?

---

### Post by heimo on 2005-08-14
When you try to ssh, add -v -vv or -vvv flag to get debug information.

---

### Post by usergentoo on 2005-08-14
```
Aug 14 01:21:11 kubuntu sshd[22843]: (pam_unix) 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.100
```

The password checks out on the actuall computer.
The above is what I pulled off my laptop when tryin to connect to it.

---

### Post by usergentoo on 2005-08-14
It was my mistake

What i did was when the first time it asks about adding the key.
I was trying to access like this ```
ssh 192.168.1.100
``` 
when i should have done this ```
ssh user@192.168.1.100
```

---

### Post by nad on 2005-08-14
Your system is not receiving a username, there is no user= field.

Try logging in as the explicit user: ssh servername/address -l username

---

### Post by nad on 2005-08-14
That works also.

Glad you figured it out.

---

