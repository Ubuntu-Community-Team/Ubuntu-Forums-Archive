---
title: "Cannot Log onto the internet"
date: 2012-05-15
forum: Desktop Environments
---

### Post by cashjunkie on 2012-05-15
I'm running virtualbox with an ubuntu OS host... I'm using a damn small linux virtual machine to act as a firewall with 2 network adapters (connected to NAT and internal network). The goal is for ubuntu virtual machine to surf only in a tor only environment with dsl as a firewall but, ubuntu is not connected to internet and when I try ssh tunneling which is turned on in dsl. I am getting no where.  I've setup firefox to use the following proxy servers for tor Browser:  
10.0.2.2:9050 
10.0.2.2:8118


I put these commands in the terminal of ubuntu vm.
"ifconfig eth0 10.0.3.2"
and "ssh -N -L 9050:10.0.2.2:9050 root@10.0.3.1"
and "ssh -N -L 8118:10.0.2.2:8118 root@10.0.3.1"
and everything I do I get 
"ssh: connect to host 10.0.3.1 port 22: No route to host"
   
I hope someone can help me with this situation, I am out of ideas and the silly set up guide that I followed didn't really anticipate any changed that I would have to make for my particular situation.   Thanks in Advance.

---

