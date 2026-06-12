---
title: "I cant get to Root"
date: 2005-12-23
forum: Desktop Environments
---

### Post by gkhanna on 2005-12-23
hey everyone.... im testing out Ubuntu for the first time...actually linux for the first time. i have installed it using the install CD and want to install the Kubuntu package. I have been told that  i need to do the following in terminal...
su
aptitude install kubuntu-desktop

when i type in 'su' i am asked for a password. Iput in my user password, but apparently thats not it. I reinstalled to make sure that i dint miss anything while installing regarding a root password.

If anyone can advise me on this matter, id appreciate it, coz i basiczlly know nothing about linux ...thanks

---

### Post by cstudent on 2005-12-23
Try this instead

```


sudo apt-get install kubuntu-desktop


```

When asked for the password, enter YOUR user password.

---

### Post by rikai on 2005-12-23
use sudo, not su. ;)

---

### Post by Ubuntumaster on 2005-12-23
I have a weird problem: I just upgraded my amd duron 1104 MHz to an Athlon 1.5GHz, and after that upgrade, even using the *sudo* command, I can't access root.

I reinstalled ubuntu 5.1 onto my p4 machine with hyper threading disabled (I'm running a server) and everything went fine. But, after I disconnected from the server, and re-enabled hyper threading, I began having the aforementioned issue.

Please help, this is a serious issue as I make my own share of changes to linux so that it will fully support my hardware.

---

### Post by r4ik on 2005-12-23
Sudo su gets me to root.

---

### Post by peanut butter on 2005-12-23
i rilly dont know but when i make major hardware changes i just reinstall

---

