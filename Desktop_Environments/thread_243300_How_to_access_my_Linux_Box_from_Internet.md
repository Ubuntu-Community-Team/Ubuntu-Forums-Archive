---
title: "How to access my Linux Box from Internet?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by hukilai on 2006-08-24
I would like to be able to download files from my home Ubuntu box via ftp. I found the guide how to set up an ftp server, users, folders and permissions.

Now I have a question what should I do to make my Ubuntu accessible externally, still keeping it secure as much as possible.

I have a DSL modem for Internet and my box connected to it via Ethernet. So the modem has internal (192.168.1.1) an external IP addresses. It also acts as DHCP server for Ubuntu. Ubuntu has only internal IP address (192.169.1.2), assigned by DSL DHCP.

What are the actions to enable protected (username/encryption) ftp access to the box from the outside world and to keep all other holes secured?

When I set up my ftp server, what is going to be his address on the Internet?

Thank you in advance.

---

### Post by eternalsword on 2006-08-24
are you using proftpd if so, there should be a proftpd.conf file somewhere that you can change user and group to your username and group and it will then ask for your username and password to access the files.  for outside access, you need to know the public IP address of your modem and forward ftp traffic to your server's internal IP address.

---

### Post by hukilai on 2006-08-24
How do I forward traffic to Ubuntu? Is it done on the modem or the PC?

---

### Post by az on 2006-08-24
> **hukilai said:**
> 
What are the actions to enable protected (username/encryption) ftp access to the box from the outside world and to keep all other holes secured?

Use SSh instead of ftp if you want encryption.  You will need an SSH client if you are using windows.  Try putty.

> **hukilai said:**
> 
When I set up my ftp server, what is going to be his address on the Internet?

Thank you in advance.

Your IP address changes every time you connect to your ISP and at regular intervals, too.  Use dynamic DNS.

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by eternalsword on 2006-08-24
if it's just a **modem** and not a **router** then it should forward automatically

---

### Post by jaclynL on 2006-08-24
SSH is definitely the way to go.  I prefer the SSH Secure Shell Client to Putty when I'm remotely accessing my computer from a Windows machine.  [Here's]("http://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe") where to find it if you want to take a look.  Otherwise, in OSX you can open up a terminal and use ssh and sftp if you don't need a graphical interface.  I do this all the time using my dyndns account (mycomputername.homelinux.org or whatever) and it is very easy and convenient.

---

### Post by hukilai on 2006-08-24
Do I understand correctly that I can just use the modem IP to login into FTP and modem/router will sort the rest out automatically?

How can I see which ports are enabled/disabled in Ubuntu? I guess I will need to open FTP (21 by default) to make it work? What is the difference if I use SSH client to log in?

---

### Post by eternalsword on 2006-08-24
As long as there's a service listening on a port, it is by default open in Ubuntu unless you specifically close it.  You need to clarify whether you have a router or a modem, they are not the same.  If it is a router, you need to tweak the routers port forwarding settings.  If you are using ftp that port is 21, but if you go with ssh, it is port 22.  The IP you need is the one the outside world sees unless you are only running it over a LAN.  On the LAN it would be the IP address of the local server.  For the outside, I would recommend going to [http://www.ipchicken.com/](http://www.ipchicken.com/) to see what your public IP address is.

---

