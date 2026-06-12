---
title: "Problem with ssh"
date: 2008-12-13
forum: General Help
---

### Post by lsutiger on 2008-12-13
I did a reinstall a while back, and forgot to setup ssh. So I went ahead and installed openssh-server, edited /etc/ssh/sshd_config to accept login on an alternate port(5970) and ran /etc/init.d/ssh restart.
Then I ssh localhost and I get connection refused.
```
 ssh localhost
ssh: connect to host localhost port 5970: Connection refused

```


Did I miss a step?

---

### Post by nielz on 2008-12-14
Post the output that is added to /var/log/auth.log when you restart the server. It should look something like this:

```

Dec 14 21:32:36 stampede sshd[9303]: Received signal 15; terminating.
Dec 14 21:32:36 stampede sshd[9474]: Server listening on :: port 5970.
Dec 14 21:32:36 stampede sshd[9474]: Server listening on 0.0.0.0 port 5970.

```

---

### Post by lsutiger on 2008-12-14
```
Dec 14 15:06:22 complexity-1501 sshd[3668]: Received signal 15; terminating.
Dec 14 15:06:22 complexity-1501 sshd[32652]: Server listening on :: port 22.
Dec 14 15:06:22 complexity-1501 sshd[32652]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.

```

hmmm...#1 it is not listening on the right port (per /etc/ssh/ssh_config) and trying to listen to the wrong adapter.

Where do I change that?

Thanx for the reply!

---

### Post by lsutiger on 2008-12-14
I forgot to edit sshd_config.
But I am still not able to create a session.
ssh localhost
ssh: connect to host localhost port 5970: Connection refused

---

### Post by lswb on 2008-12-14
Have you checked your firewall settings?

---

### Post by lsutiger on 2008-12-14
Yes, I have the port open..I got a session running, I remoted into my office computer, then back to my home computer.

Now I need to find out why NX NoMachine will not authenticate. I was under the assumption that NX ran on top of ssh and those keys were used.

---

