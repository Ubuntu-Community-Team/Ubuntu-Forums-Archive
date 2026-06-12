---
title: "Ubuntu XDMCP Client for Remote Desktop"
date: 2009-03-31
forum: General Help
---

### Post by burakvarhan on 2009-03-31
Hello all,

I have two machines (Fedora and CentOS) located at the LAB on which XDMCP is enabled. I usually connect to them via Xmanager/Xbrowser on Windows machines. 

However, now I switched to Ubuntu on my PC and I need a way to get connected those machines. Unfortunately, The tutorials I found on the Internet usually focus on how to configure the XDMCP sever on Linux. As I said I need something like remote desktop access on my Ubuntu to the other machines.

I would appreciate If somebody could provide a step-by-step guide for configuring/installing an XDMCP client on Ubuntu so that in the future people can use it. In fact I don't know what are the availbale client  programs and how popular they are...

Thank you.

---

### Post by burakvarhan on 2009-04-17
Hello all, 

Iam the issuer of the question and I solved my problem I'd like to write my solution in case somebody else needs it.

Installing XDMCP service on a server machine is nothing but enabling XDMCP and its related port in the necessary configuration files and allowing port 177 traffic if you are behind a firewall. In Fedora 10 open the file /etc/gdm/custom.conf and make sure the three lines below are in the file;
[xdmcp]
Enable=1
Port=177

As for making your host to connect remote machine you have to install a client with XDMCP/XDM capability. On my Ubuntu I tried two different client softwares; the first one was Xnest, connecting to remote host with xnest is easy and it works but it is unbearably slow. So I decided to switch to nomachine nxclient, however nomachine nxclient requires you installing nomachine nxclient, nxnode, and nxserver on the remote machine. installing nxclient on your local host is enough to get connected. And everything works OK, nxclient is very very fast.

---

