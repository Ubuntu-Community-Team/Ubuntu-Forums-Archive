---
title: "Cisco VPN"
date: 2006-03-06
forum: Desktop Environments
---

### Post by kuppas on 2006-03-06
Hi,

  I have installed Cisco VPN (4.7) successfully and I am able to connect my VPN server and authenticate.  After I logged in successfully in  VPN, my entire network does not work.  I am not able to ping the any computer in my office network and I am not able to ping internet sites.  I have also tried to use IP address to ping instead of website name but it did not work either.  Any help would be greatly appreciated.

Thanks,
-Kuppa

---

### Post by aysiu on 2006-03-06
A couple of things:

1. What are the indications that you have that your authentication was successful?

2. It's pretty common for a VPN connection to actually disable your local internet connection ("local LAN access"). That's what happens to me when I VPN to work--no email or internet on my end until I disconnect.

---

### Post by kuppas on 2006-03-06
The indications are,  

1. I am able to login using my user name and passcode.  Entering wrong username or passcode is not authenticating..  
2. After connecting, a new network interface(cispec0, I don't remember the exact name) is up and got the right IP address.

---

### Post by WrathofthePenguin on 2006-03-06
What you are describing is not a bug. The administrator of the VPN server can set it up to lock down local access outside the tunnel. This is for security. It does not good to have a private pipeline into your trusted network if somebody can compromise a client and get access.

The administrator can also configure split tunneling or inverse split tunneling. Split tunneling allows you to send traffic for everything except certain subnets over the tunnel. Inverse split tunneling allows you to send certain subnets through the tunnel and everything else out locally.

Split tunneling is not something you have control over locally.

---

### Post by Sendervictorius on 2006-03-07
Hi kuppas, I too am interested in setting up a Cisco VPN. Its the last thing I have to do before I can stop using Windows!

Can I ask where you obtained the ubuntu VPN software, and what you had to do to set it up? You didn't use the one that comes in the synaptic repositories?

---

### Post by kuppas on 2006-03-09
Hi Sendervictorius,  

  I have installed Cisco VPN 4.7.x and I got the software from my company.  I have compiled and installed the CiscoVPN.

---

### Post by weizilla on 2006-03-20
I am having the same problem. I've gotten both the cisco vpn (v4.8 ) and vpnc working but my internet never works after I connect. I know they are working because they ask me for a user name and password and refuse to connect if I type in the wrong password.

---

### Post by Jingo on 2006-03-28
Any solution?

I am having the same issue. Connected alright, but somehow the other end is not reachable. The /etc/resolv.conf got updated. But I am not able to resolve any internet adresses.

---

### Post by Jingo on 2006-03-28
Hmmm... I just tried under Dapper!! no problems! ??
So this means I will switch to Dapper for good soon!

---

