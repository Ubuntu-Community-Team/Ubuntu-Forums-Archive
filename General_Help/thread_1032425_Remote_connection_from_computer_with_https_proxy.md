---
title: "Remote connection from computer with https proxy"
date: 2009-01-06
forum: General Help
---

### Post by zeroed on 2009-01-06
Hi everybody!

Is it possible to connect remotely to my ubuntu from work computer?
Windows XP, no administration rights, https proxy.

I found some solution: team viewer, but it doesn't have a package for linux + all traffic goes through their server..

I tried to find vnc client (btw, do I need **vnc** client to connect?) with https support, but couldn't..

---

### Post by cmnorton on 2009-01-07
What are you going to do with this connection? Why not use ssh?

I connect to an IIS server using a Perl script. It is not a browser application in the traditional sense, but a Linux application needs to send data to an application, which runs in the context of an asp page, so http is the protocol. 

With the right Perl modules, you could probably connect using https. I have not tried it.

---

### Post by zeroed on 2009-01-07
> **cmnorton said:**
> What are you going to do with this connection? Why not use ssh?

I connect to an IIS server using a Perl script. It is not a browser application in the traditional sense, but a Linux application needs to send data to an application, which runs in the context of an asp page, so http is the protocol. 

With the right Perl modules, you could probably connect using https. I have not tried it.

All I wanna do is to control my home computer from my work computer. Simple remote desktop. 

Unfortunately, I don't know what is ssh and how to use it.

---

### Post by dcstar on 2009-01-07
> **zeroed said:**
> All I wanna do is to control my home computer from my work computer. Simple remote desktop. 


"Remote Desktop" has nothing to do with a "HTTPS Proxy", you need to ask your work IT support people what is possible because you obviously don't understand all the technical requirements - and unless you can get a connection path from your work to your home then the rest is pointless.

---

### Post by cmnorton on 2009-01-08
> **dcstar said:**
> "Remote Desktop" has nothing to do with a "HTTPS Proxy", you need to ask your work IT support people what is possible because you obviously don't understand all the technical requirements - and unless you can get a connection path from your work to your home then the rest is pointless.

Please talk with your IT staff. There are two main ways to use remote, VPN and Citrix-style web access. With VPN access, once the VPN connection is established, you can access your systems at work, because you have a LAN presense on your network, courtesy of the VPN connection.

I do not know if Citrix technology works without someone approving the connection at the other end; a machine could probably do it. Our vendors use this technology to come inside our firewall with our approval. Using web-based technology, they can control our desktop, server, and so on.

---

### Post by Spalding on 2009-02-25
I can do that, I just had to install the Citrix client. It works very well, except that the shift key doesn't always work correctly - weird.

Edit: Oops, I am going the other way, using Ubuntu at home to log into XP at work via Windows Remote Desktop Connection which I first had to ask IT to put in my Citrix apps.

---

### Post by zeroed on 2009-02-26
So, all I have to do is install Citrix client on my ubuntu home machine?

---

