---
title: "can't acces ssh from hoary to breezy"
date: 2005-10-14
forum: Desktop Environments
---

### Post by sabitha on 2005-10-14
anybody know why i can't connect to breezy using ssh from hoary, but i can connect to another hoary from breezy. i'm already instaled ssh on breezy but still can't connected from hoary. i'm trying to upgrade all of my computer to breezy but im stil try just one and a lot of problem.
if i use my webcam the computer (breezy) hang/crash (silent) so i must reboot manualy. 
sorry for my english :???: 
i hope i found the answer or anybody cant help me from this forums

---

### Post by adwait on 2005-10-14
SSH has nothing to do with the distribution, so I doubt the problem is the fact that you are connecting from a hoary to a breezy. Have you started the ssh daemon on the breezy before trying to connect? Try start the sshd and then connecting. You can start the SSH server using
```
sudo /etc/init.d/sshd start
```

This command is to be entered on the breezy to which you are trying to connect.

---

### Post by sabitha on 2005-10-14
client@client-06:~$ sudo /etc/init.d/sshd start
Password:
sudo: /etc/init.d/sshd: command not found

:confused: :(

---

### Post by jimmyp on 2005-10-14
[QUOTE=sabitha]client@client-06:~$ sudo /etc/init.d/sshd start
Password:
sudo: /etc/init.d/sshd: command not found

:confused: :([/QUOTE]

sudo apt-get install openssh-server

---

### Post by sabitha on 2005-10-14
Reading package lists... Done
Building dependency tree... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 191 not upgraded.

---

### Post by jimmyp on 2005-10-14
[QUOTE=sabitha]Reading package lists... Done
Building dependency tree... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 191 not upgraded.[/QUOTE]

try
sudo /etc/init.d/ssh start
instead of
sudo /etc/init.d/sshd start

---

### Post by adwait on 2005-10-14
Ooops.....yeah it should be 
```
sudo /etc/init.d/ssh start

```

---

### Post by sabitha on 2005-10-15
client@client-06:~$ sudo /etc/init.d/ssh start
Password:
 * Starting OpenBSD Secure Shell server...                               [fail]

---

### Post by exosyst on 2005-10-15
yeah i get a fail here as well:

 * Starting OpenBSD Secure Shell server... Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.

---

### Post by sabitha on 2005-10-16
thank's for all help that my fault because my ip set to DHCP now i set to static IP :)

---

