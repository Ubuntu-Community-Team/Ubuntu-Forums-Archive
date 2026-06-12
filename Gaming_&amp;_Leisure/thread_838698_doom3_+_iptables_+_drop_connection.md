---
title: "doom3 + iptables + drop connection"
date: 2008-06-23
forum: Gaming &amp; Leisure
---

### Post by Dan_Dranath999 on 2008-06-23
My problem is a common one: Have a second-hand copy of Doom 3. But it keeps telling me the key is already in use, so i can't play the game. This happens because the game calls a server to check the key, and a lot of keys are cracked. If i disconnect from the web, or run the game under Windows, it works.

I read something in this thread:
[http://ubuntuforums.org/showthread.php?t=56790](http://ubuntuforums.org/showthread.php?t=56790), about not allowing a connection to that server, so my key doesn't gets checked.(i can't play the multiplayer mode, but hell, at least i should be able to play the normal stages) 

> You can prevent this automatic connection, by installing Firestarter, and dissallowing connections to:
idnet.ua-corp.com:27650 

But i don't want to install firestarter, instead, **i to want to use my azureus iptables script**, but i suppose i have something not quite correct:

This is the script:
```
(sleep 160
         /sbin/iptables -I INPUT -p tcp --dport 61316 -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport 61316 -j ACCEPT 
	 /sbin/iptables -A INPUT -p all -d 192.246.40.244 -j DROP ) &
```
The 2 first rules are for azureus and work without problems, and added a third to drop any connections to the server idnet.ua-corp.com, But it does't work.

when i enter "sudo iptables -L" at the terminal, i get this:

```
invitado@CajaBase:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:61316 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:61316 
DROP       0    --  anywhere             idnet.ua-corp.com   

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```

---

### Post by Dan_Dranath999 on 2008-06-24
wooga wooga wooga kuanga tutumanga Billguanga Gatesguanga!

---

