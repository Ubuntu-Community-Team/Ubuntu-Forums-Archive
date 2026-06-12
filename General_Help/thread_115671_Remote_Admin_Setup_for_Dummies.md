---
title: "Remote Admin Setup for Dummies?"
date: 2006-01-11
forum: General Help
---

### Post by moon2js on 2006-01-11
I want to setup a file server for family with samba, ftp, apache/gallery, etc for internal family use. But they don't know anything about Linux so I'd have to administer it from afar. Also, I'd like to access this home network remotely as a user as well as an admin.

I've been a Linux newbie for going on three years now. I know of things but not necessarily how to do things. Can anyone give me any advice for seting up such a system I can administer and access securely from afar but I can't rely on anyone geographically near the actual system being able to do anything on the system other than hit the power button.

What do I need to prepare, research, familiarize myself with? ssh, ftp server, router config, firewalls?

Do cable companies give out a static IP address to subscribers? If they don't or if they change it, how find it out if I'm not geographically there?

How do I begin to set this up? Is it too much for me because I'm a "newbie"? What are security/network concerns I should be aware of?

I've got a VOIP gateway between the cable modem and the router at the moment. Is that a concern?

What can I do with what sounds like a complicated setup of VPN that I can't do with ssh and ftp?

I realize that's a lot to ask, but any advice would be greatly appreciated. I tried to google, but keywords like "remote admin" a bit too much to wade in, and I need easy-to-understand howtos for people like me who understand *nix basics but not necessarily much more. If anyone can point me to anything like, that would be fantastic.

---

### Post by nkhansen on 2006-01-11
> What do I need to prepare, research, familiarize myself with? ssh, ftp server, router config, firewalls?
ssh, router config and firewalls. You should not use ftp - it is insecure. You can use sftp/scp through ssh. Some/Most FTP-clients can handle this (gftp(GNOME) and filezilla(WinXP)).

> I've got a VOIP gateway between the cable modem and the router at the moment. Is that a concern?

You need to be able to forward a port through both the voip gateway and the router to/from your server, if you want to be able to connect to it from the outside.

> Do cable companies give out a static IP address to subscribers? If they don't or if they change it, how find it out if I'm not geographically there? It differs from cable company to cable company (It does were I am, anyways). If you only get a dynamic address, you can use services like DynDNS.com get a dynamic domain-name. You can then set up a script on the server to automatically update the domain-name with your current IP.

I think the hardest part may be the port forwarding, and the dynamic DNS setup. SSH is/can be a breeze.

Good luck!

---

### Post by moon2js on 2006-01-11
Thank you so much for the info. It's all very helpful.

What do I need to install/setup in order to do sftp/scp? I already have the ssh server setup and can use that. Do I need something like vsftpd?

---

### Post by nkhansen on 2006-01-11
As far as I can remember, scp/sftp is run directly through the SSH server in Ubuntu. I am not sure what vsftpd, I would guess, that it has a lot of more advanced features. I have never used it.

---

### Post by lamego on 2006-01-11
ssh is enough for scp/sftp .
If you are not very familiar with command line administration installing webmin is also a good option, it will allow to configure a lot of things from a web interface.

---

### Post by moon2js on 2006-01-15
I've got another question. Is it possible to remotely connect to a home network and access samba services (file share and printer) as if I'm part of the LAN too?

For example, said home network has an Ubuntu box acting server, but, say, I want to access files on a Win XP box or its printer on that home LAN (but I don't want to mess with the XP boxes).

---

