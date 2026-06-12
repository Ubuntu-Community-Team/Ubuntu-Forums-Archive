---
title: "vpnc and remote net"
date: 2006-01-16
forum: General Help
---

### Post by marjnap on 2006-01-16
Update - Took PC and router to work and setup on an outside port, everything is OK. I am working with my ISP, they are blocking something apprently.

I have breezy 5.10
vpnc 0.3.3
running amd64
smb4k

I think I have come to my wits end with this and decided to ask for help. I have set up and install vpnc with the config file, I have the tun module, and I am able vpn into work. Everything is fine up to browsing my companies network. I do a sudo vpnc job and it gives me the logon which authenicates and I get my job's legal notice in the terminal. However, when I hit ctrl + L and put in smb://172.16.1.10 I get an authenication screen, but it say to logon to 192.168.2.65, which is my IP on my machine, this does not seem right. I have tried my logon using my PC logon and my companies logon with the domain, nothing works, it just keeps poping up the logon screen. I have the one without the vpnc-connect, do I have to adjust the routes. What in the world am I missing. HELP

---Update I worked with our Linux person at work and he is having trouble with Fadora too. Not as much as me, but still not working right. He is at least able to ping the network and see the network using smb4k, but stops working after a while. I can ping the public IP I am connecting  to and the gateway at work, but cannot ping beyond that. routes look correct, made sure iptables were clean and firewall was disabled. I looked in smb4k GUI and it is showing my computer name only in network list. I set up our dns IP to see if that helps, but of course it cannot find it. It seems like it wants to look at my computer as the network and not my job's network. I am probably missing something simple I hope.

I think it may be afraid of the light at the end of the vpn tunnel--joke of course.

Thank you in advance,
Marj

---

