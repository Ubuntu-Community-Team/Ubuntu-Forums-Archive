---
title: "nguard in lan"
date: 2006-08-22
forum: Gaming &amp; Leisure
---

### Post by jen140 on 2006-08-22
Hello all!
I have in here a lan ,with ubuntu 6.06 and windows . The linux machine is connected directly to the internet ,and the windows machine is connected to ubuntu machine with crossover cabe . I have internet configured at windows, it works well . But some pages (with iis servers) i cant see, but the problem is in the game called Priston Tale ,that has nguard (anticheat programm) that need to be updated , but it cant connect to the game server to update, it says that it is connected, but didnt do anything and shows me the "retry" button. The windows machine has ip 192.168.2.2 and linux 192.168.2.1 . 
Thise are my iptables rules -> > 
iptables -A INPUT -i ppp0 -p icmp -j DROP
iptables  -A INPUT -p tcp -m tcp --dport 25 -j DROP
iptables  -A INPUT -p tcp -m tcp --dport 111 -j DROP
iptables  -A INPUT -p tcp -m tcp --dport 443 -j DROP
iptables  -A INPUT -p tcp -m tcp --dport 3306 -j DROP
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables -t nat -A PREROUTING -p udp -i ppp0 --dport 13000 -j DNAT --to-destination 192.168.2.2:13000
iptables -t nat -A PREROUTING -p tcp -i ppp0 --dport 13000 -j DNAT --to-destination 192.168.2.2:13000

And i already have done -> echo 1 > /proc/sys/net/ipv4/ip_forward ,to  connection works. 
So if any 1 have thise problem or know how to resolve it ,please help.

---

