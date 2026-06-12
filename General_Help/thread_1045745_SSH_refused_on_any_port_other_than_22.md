---
title: "SSH refused on any port other than 22"
date: 2009-01-20
forum: General Help
---

### Post by dynsight on 2009-01-20
I would like to run ssh server on a port other than 22.  

SSH works fine both inside and outside (using port forwarding).  HOWEVER,

if I go to ssh_confing and change the port to port xxxx following the guidelines here: [https://help.ubuntu.com/7.10/server/C/openssh-server.html](https://help.ubuntu.com/7.10/server/C/openssh-server.html)

I get the following message when I type ssh local host:

ssh: connect to host localhost port xxxx: Connection refused

I also issued a ufw allow xxxx, and it did update the table... but I still cannot connect on the specified port.

I am running this on Ubunto Server 8.10

Please do not respond with router issue, it is not, since I am connecting from local host.

ssh localhost (works on port 22)
ssh localhost (does not work on any other port other than 22).

Thank you

---

### Post by wirelessmonkey on 2009-01-20
you'll need to alter sshd_config appropriately and restart ssh via 

/etc/init.d/ssh restart

---

### Post by dynsight on 2009-01-20
Thanks, I was editing the wrong file 

sshd_config

Sorry, and thank you.

---

### Post by sedawk on 2009-01-20
And instead of changing the client config file file /etc/ssh/ssh_config
you can give the port on the command line:
```

ssh -p 22 localhost #default
ssh -p 1234 localhost #if sshd listens on 1234

```

To check where sshd is currently listening
```

sudo lsof |grep sshd|grep LISTEN

```
When running on the default port you should see something like
... TCP *:ssh (LISTEN)
On another port (e.g. 1234) it should look like this
... TCP *:1234 (LISTEN)
(Many ports have names, see /etc/services, that is why you sometimes
 see a string like "ssh" which means "port 22").



The output might be *:ssh (ssh in /etc/services is set to port 22)
or *:1234

---

