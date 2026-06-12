---
title: "Can't SSH to localhost"
date: 2008-12-11
forum: General Help
---

### Post by LuserName on 2008-12-11
I installed openssh-server and to test it, I tried:  $ ssh localhost.  I got:

ssh: connect to host localhost port 22: Connection refused

sshd is running, and I tried disabling iptables, but I still get the error.  what's the problem?

---

### Post by Peter09 on 2008-12-11
try

```
ssh -v localhost
```

That will give you more information

---

### Post by LuserName on 2008-12-11
```
greg@greg-desktop:~$ ssh -v localhost
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused
```

---

### Post by Peter09 on 2008-12-11
Well, that looks to me that your ssh server is not running or has not attached to Port 22.

Did you install openssh-server?

---

### Post by LuserName on 2008-12-11
Fixed it.  Had to purge my config files and reinstall.  Guess I was messing with them once upon a time.  Thanks for the help

---

