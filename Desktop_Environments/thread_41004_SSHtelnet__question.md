---
title: "SSH/telnet  question"
date: 2005-06-11
forum: Desktop Environments
---

### Post by glasscleaner on 2005-06-11
hello

i want to know if by default in ubuntu, comeone can try to connect by SSH or telnet or it is disabled? i know there is secure anyway but how can i see if it is enabled or disabled?

thanks

---

### Post by GrumpySmurf on 2005-06-11
I'm looking at my recent Ubuntu installation and I don't see the openssh-server package installed.  

```
$ dpkg -l | grep openssh
```
A simple apt-get fixes that, though:

```
$ sudo apt-get install openssh-server
```
Installation will create the SSH keys for the host, start sshd on your system, and enable startup when the system boots (check that /etc/rc2.d/S20ssh exists).

---

