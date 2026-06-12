---
title: "Problems to make 3 virtual machine with Linux Ubuntu"
date: 2015-04-10
forum: Education &amp; Science
---

### Post by moises6 on 2015-04-10
[COLOR=#333333][FONT=Lucida Grande]]Hi i am a student and i have to do a hard homework, i have to connect 3 virtual machines= 2 PC+1 ROUTER[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I am using a Vyatta router and it has two virtual ethener wires to make two interfaces. Eth0: 10.1.1.1 Eth1:10.1.1.129 both with mask 255.255.255.128[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]The first Virtual Machine is an ubuntu 14.04 LTS it has 2 interfaces for that i created two adapters, the first one is a NAT adapter and the second is a sigle host adapter . When i type IFCONFIG i have Eth0 and Eth1, i configured Eth0 with dchp and Eth1 y type sudo nano /etc/network/interfaces and i configured it with IP:10.1.1.2 mask 255.255.255.128 gaterway 10.1.1.1.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]The second Virtual Machine is a Linux PC but it doesnt have the same commands that ubuntu because it is something called OPSVIEW but with others commands i configured with IP:10.1.1.130 mask 255.255.255.128 gaterway 10.1.1.129[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]**WHAT IS THE PROBLEM**[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]?[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I have a problem checking connection because if i make PING since Virtual Machine1 to IP: 10.1.1.1, 10.1.1.2 and 10.1.1.129 it works perfect but it doesnt have connection to 10.1.1.130 and it is the same if i make ping since Virtual Machine2 i cant make ping to 10.1.1..2,so , If i type IFDOWN eth0 i cant connect to internet, but i can now make ping to 10.1.1.130 and if i type IFUP eth0 i can connect to internet but now i cant make ping to 10.1.1.130.......[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Someone understand this? i really dont understand it, i think i did all good. I made all connection with the rights adapters, i configured with Ethx with good IP, so i really dont understand.. 

I Cant have 2 ethernet?  are there another way to configure eth0 and eth1? or i just made something wrong?

Pls Help[/FONT][/COLOR]

---

### Post by The Cog on 2015-04-10
Can you post the output of these 2 commands from both virtual machines please?
```
ifconfig
route -n
```

Are both VMs able to ping both interfaces of the router (10.1.1.1 and 10.1.1.129)?

---

