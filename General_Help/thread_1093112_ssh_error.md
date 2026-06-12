---
title: "ssh error"
date: 2009-03-11
forum: General Help
---

### Post by morficus on 2009-03-11
When trying to connect to my Ubuntu 8.04TLS box, I get the following message:

```
ssh_exchange_identification: Connection closed by remote host
```

I know sshd is up and running, because doing "ssh localhost" works fine, but if I'm on another machine or if I do "ssh my_ip_address" it fails.. :-(

Here is the output I get when I run ssh in verbose mode:
```

morficus@Lucy:~$ ssh -v morficus@my_ip_address
OpenSSH_5.1p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to my_ip_address [my_ip_address] port 22.
debug1: Connection established.
debug1: identity file /home/morficus/.ssh/id_rsa type -1
debug1: identity file /home/morficus/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
```

I have read many many pages about this issue... and 99% of them mention the hosts.allow and hosts.deny files... both which are empty, so I don't think they are doing much right now.

Any one have any ideas what could be causing this issue?

---

### Post by Peter09 on 2009-03-11
Not sure if this applies but make sure your user is in the ssh group.

---

### Post by morficus on 2009-03-11
I just checked and I am, indeed, in the SSH group

---

