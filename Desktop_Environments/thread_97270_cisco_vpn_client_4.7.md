---
title: "cisco vpn client 4.7"
date: 2005-11-30
forum: Desktop Environments
---

### Post by ACK!! on 2005-11-30
This is the version that should not need the interceptor.c patch and it does not even apply cleanly if I try to apply it.  

I need cisco vpn client since other free vpn clients do not seem to support the prompts that my servers are sending back.  What do I mean?  I put in username and then pass and after that my server asks me if I understand that I am breaking the law if I am not really authorized to hook into the network.

With other vpn clients (non-Cisco) I never see these prompts and all login attempts just fail.

Anyway, even with vpnclient 4.7 (whatever) from Cisco my computer occasionally and rather randomly locks completely and totally up.

Anyone else see this behavior or have any ideas what to do to prevent it?

---

### Post by WrathofthePenguin on 2006-03-16
[QUOTE=ACK!!]This is the version that should not need the interceptor.c patch and it does not even apply cleanly if I try to apply it.  

I need cisco vpn client since other free vpn clients do not seem to support the prompts that my servers are sending back.  What do I mean?  I put in username and then pass and after that my server asks me if I understand that I am breaking the law if I am not really authorized to hook into the network.

With other vpn clients (non-Cisco) I never see these prompts and all login attempts just fail.

Anyway, even with vpnclient 4.7 (whatever) from Cisco my computer occasionally and rather randomly locks completely and totally up.

Anyone else see this behavior or have any ideas what to do to prevent it?[/QUOTE]


Most likely what you are seeing here is a result of the administrators setting the server up to only allow use of the Cisco VPN client. The Nortel Contivity series has the same type of settings - you can allow all clients or only the Nortel client to connect.

---

