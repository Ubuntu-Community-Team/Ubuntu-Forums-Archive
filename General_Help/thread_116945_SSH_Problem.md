---
title: "SSH Problem"
date: 2006-01-13
forum: General Help
---

### Post by Jaygo333 on 2006-01-13
I've never managed to ssh my pc from elsewhere. I also can't ssh from the localhost itself. I've read posts from
[http://ubuntuforums.org/showthread.php?t=116939&highlight=root](http://ubuntuforums.org/showthread.php?t=116939&highlight=root)
and follwed the exapmles mentioned tehre but when I try to sshin the terminal,
It lags. Does nothing. No error comes up, just a blank screen.
I normally type
jaygo333@Ubuntu:~$ ssh xxx.xx.xxx.x

and then nothing. No errors or anything. What did U do wrong?

:confused:h34r: Jaygo333 :confused:h34r:

---

### Post by SickTwist on 2006-01-13
Make sure that you have openssh-server installed on the machine you want to act as a server. If the ssh server is behind a firewall,  you'll need to forward the port used by sshd (port 22 by default).

---

### Post by Mr_Grieves on 2006-01-14
Well.. what do you get when you run

```

sudo lsof | grep ssh

sudo iptables -L

cat /etc/ssh/sshd_config

cat /etc/hosts.allow

cat /etc/hosts.deny

```

---

