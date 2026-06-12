---
title: "Problems with LAN DNS"
date: 2005-12-24
forum: General Help
---

### Post by PryGuy on 2005-12-24
Hello everybody!
I've got a problem here, I've clean installed Ubuntu 5.10 (I had 5.04 before) and everything's great, except for the fact that the Breezy stopped recognizing my local network DNS server. It looks like this: I can't do "ping server" (and I could in Hoary), it says "unknown host" but I can do "ping 192.168.0.1" (which is server's IP) perfectly. Samba works okay.

I've got a switch with built in DHCP server, and all my PCs are using it. I haven't changed anything in my network setup. Please help!:smile:
Thank you in advance!

---

### Post by Koybe on 2005-12-24
can you do
```
cat /etc/resolv.conf 
```
and post it?

You should have the IP of your nameserver in it (so 192.168.0.1), but it should be set by the dhcp bail.

---

### Post by PryGuy on 2005-12-24
everything seems to be okay:```
search server
nameserver 192.168.0.1

```Or, probably I should use my switch/DHCP server's IP which is 192.168.0.10?

---

### Post by Koybe on 2005-12-24
OK, I'm not sure i really understand how your network stands. If I understand well 
- 192.168.0.1 is a ubuntu server (running which service?)
- 192.168.0.10 is your switch

It's a bit confusing to me, is your server a nameserver? Is it the server that route trafic from the internet?

---

### Post by PryGuy on 2005-12-24
Nope, Ubuntu is not a server and it's not on 192.168.0.1, Ubuntu is just a client. I still use Windows as server, and, what's important, I will repeat, I have not changed it's setup. 

192.168.0.10 is my switch, you are right...:)> It's a bit confusing to me, is your server a nameserver? Is it the server that route trafic from the internet?You've got me lost here. I guess that my LAN DNS is my DHCP switch 'cause it gives IPs according to the MAC addresses. I use Windows (192.168.0.1) for my internet connection and as a firewall.

---

