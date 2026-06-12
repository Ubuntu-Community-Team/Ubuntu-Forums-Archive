---
title: "run add/remove programs using a priviliged user other than root"
date: 2006-03-30
forum: Desktop Environments
---

### Post by wshamroukh on 2006-03-30
Hi all

how can i run the add/remove programs GUI using a privilged user(i made him as a root) other than the root.. when i run this utility it asks about the root password and i don't have it... how can i run it using the priviliged user i made?

thanx in advance

---

### Post by mcmillan on 2006-03-30
I'm a little confused by the fact that you said you made a privlidged user as root. Ubuntu shouldn't have given you a root user. 

If you mean the first user you made that has all the sudo privliges you can give other users sudo rights by typing sudo visudo into a terminal. This will let you edit the sudoer file. Add the line:
[user]    ALL=[any commands you want to give rights to] 
I'm not sure what exactly brings up the add/remove, but you can have pretty much the same effect with synaptic, and I think you'll need to have apt-get listed also. Just make sure to use the full name of the command (e.g. /usr/bin/apt-get and /usr/sbin/synaptic)

If I misread this and you mean you want to add programs with the user with sudo riights, just type in your password. It's asking for root because in most linux setups you'd be doing this as root, rather than with sudo

---

### Post by aysiu on 2006-03-30
Read this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

