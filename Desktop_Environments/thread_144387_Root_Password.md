---
title: "Root Password"
date: 2006-03-14
forum: Desktop Environments
---

### Post by brucecassidy on 2006-03-14
Ok so i may be a bit of an idiot here but i have just installed ubuntu and its lovely but .

Yup there is a problem, i have gone into my terminal to try out yum, but i dont have a clue what the root password is and as it did not ask me during the install process im really confused.

Help me oh clever ones:-k

---

### Post by knalle on 2006-03-14
post your /var/log/installer/cdebconf/questions.dat file :-D

no im kidding, the root password is the password for the first user that was registerd during install

---

### Post by brucecassidy on 2006-03-14
Right well i tried that one and its not working if i have typed it in wrong is there any way of recovering it or do i have to reinstall,

---

### Post by knalle on 2006-03-14
are you using sudo or are you trying to login directly as root? root is not used in ubuntu by default, use sudo

---

### Post by Gustav on 2006-03-14
Look at [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by Darkriser on 2006-03-14
look here:

[http://www.ubuntuforums.org/showthread.php?t=142110](http://www.ubuntuforums.org/showthread.php?t=142110)

and here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

maybe it helps...

Marcel

---

### Post by brucecassidy on 2006-03-14
oh i see ok i'll give it a try thanks

---

### Post by mavr on 2006-03-14
if u have lost it you have lost it. But you simply can't loose it. How did u log in?
I think u are not using the right command. Try to type 
sudo su
and u will be asked for a password. Try it there

---

