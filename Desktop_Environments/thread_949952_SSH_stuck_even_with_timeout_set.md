---
title: "SSH stuck even with timeout set"
date: 2008-10-16
forum: Desktop Environments
---

### Post by No_Germs on 2008-10-16
Hi,
I'm trying to connect to a server, and even though i set the timeout param, and some servers i try to connect to do time out, one particular server causes the ssh to get stuck. I don't care if i don't manage to connect to it, but i don't want the ssh to hang forever since it will be run inside a script.
running 
```
ssh -o ConnectTimeout=1 -v -l uname server
```
outputs 
```
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to server [IP] port 22.
debug1: fd 3 clearing O_NONBLOCK
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: identity file /home/user/.ssh/id_dsa type -1
```

after that nothing else is printed and the whole thing is stuck until I CTRL-C. The RSA key is 100% ok. 
Again, the exact same procedure does work for me for other servers - to some i manage to login and some don't respond and cause a time out, but only this one causes the ssh to hang. 
Any ideas?

---

### Post by p_quarles on 2008-10-17
I would suggest adding a couple more verbosity levels:
```
ssh -o ConnectTimeout=1 -vvv -l uname server
```
And then see what the output says at that point.

---

### Post by No_Germs on 2008-10-17
Here it is:

```
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to server [ip] port 22.
debug2: fd 3 setting O_NONBLOCK
debug1: fd 3 clearing O_NONBLOCK
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: identity file /home/user/.ssh/id_dsa type -1
```

Any thoughts?

---

### Post by No_Germs on 2008-10-24
anyone?

---

