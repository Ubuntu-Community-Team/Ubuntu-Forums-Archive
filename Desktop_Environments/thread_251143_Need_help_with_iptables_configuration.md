---
title: "Need help with iptables configuration"
date: 2006-09-05
forum: Desktop Environments
---

### Post by anil_robo on 2006-09-05
I'm hosting a small website from a an old computer using apache on ubuntu server install. I have not configured the system at all from a security point of view, and need to configure iptables now. Ideally, I would have configured iptables using firestarter, but since I am using server install, I can't start GUI apps.

My current iptables configuration is as follows:
```

ubuntu@ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```
Is this an "empty" configuration? Is this a totally un-configured firewall?

---

### Post by Uluen on 2006-09-05
[QUOTE=anil_robo]Is this an "empty" configuration? Is this a totally un-configured firewall?[/QUOTE]Yes it is.

You don't have a router infront of it? If you're only forwarding port80 to your webserver it doesn't matter.

---

### Post by toasterofirony on 2006-09-05
It's not so much a firewall as a waiter's door :P

But yeah, it is, to all purposes a "blank" firewall.

---

### Post by anil_robo on 2006-09-05
> **Uluen said:**
> Yes it is.
Uh oh! :(

> You don't have a router infront of it? If you're only forwarding port80 to your webserver it doesn't matter.
I am behind a router, that allows ports 80 and 22. I opened port22 specifically for remote management using ssh.

Many people would say that I'm safe if behind a router, but still I want to configure iptables just in case someone is able to get past my router.

---

### Post by Uluen on 2006-09-05
You'll be fine if those are the only services you are running and they are kept up to date. I'd consider changing SSH port and use key based authentication if you don't already.

There are some (non-X) GUIs for configuring iptables, don't remember any names now though.

---

### Post by anil_robo on 2006-09-05
> **Uluen said:**
> You'll be fine if those are the only services you are running and they are kept up to date. I'd consider changing SSH port and use key based authentication if you don't already.

There are some (non-X) GUIs for configuring iptables, don't remember any names now though.

I'll try [this]("http://software.newsforge.com/software/04/03/15/211214.shtml") tomorrow.

Just an observation: When I made ssh connection to the linux box from my mac for the first time, my mac asked me something about including key in the safe-zone (or something like that). However, windows didn't ask any such questions before making an ssh connection.

Another observation: I did not install any FTP servers on the old Ubuntu box. Still, I can use dreamweaver to transfer files via "secure FTP" to this Ubuntu box. Is this "secure FTP" installed when I install SSH server?

---

### Post by Uluen on 2006-09-05
[QUOTE=anil_robo]Another observation: I did not install any FTP servers on the old Ubuntu box. Still, I can use dreamweaver to transfer files via "secure FTP" to this Ubuntu box. Is this "secure FTP" installed when I install SSH server?[/QUOTE]

[Wikipedia]("http://en.wikipedia.org/wiki/SSH_file_transfer_protocol") entry.

---

### Post by anil_robo on 2006-09-14
But the original question still remains...

How do I configure iptables for a more secure ubuntu? Perhaps someone could write "iptables configuration for dummies" ;)

---

