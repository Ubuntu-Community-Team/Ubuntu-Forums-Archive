---
title: "[SOLVED] can't insert password after su command"
date: 2008-07-06
forum: Desktop Environments
---

### Post by nir2000 on 2008-07-06
Hello!
I need to enter my password as super user after the command su but although the command line says "password:" it doesn't let me enter anything at the command line, so I can't move to the root directory.
It also worth noting that I use the Xterminal to write those commands.
So if anyone can help me I would greatly appreciate it.
Thank you in advance 
Nir
ubuntu 8.04 Hardy Heron

---

### Post by scragar on 2008-07-06
both sudo and su don't show the password as you type, it's an extra layer of security.

just type your password as normal and hit enter.

---

### Post by sisco311 on 2008-07-06
In Ubuntu the root account,by default, is disabled.
You can use:
```
sudo -i
```and 
```
sudo -s
```to start a root shell.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by sayakb on 2008-07-06
Or rather:
```
sudo bash
```
Would also start a bash root session.

---

### Post by nir2000 on 2008-07-06
Thank you everybody for your help. You saved me frustration.

---

