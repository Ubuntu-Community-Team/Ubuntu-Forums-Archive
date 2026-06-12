---
title: "Very odd networking problem..."
date: 2006-10-01
forum: Desktop Environments
---

### Post by whiterussian on 2006-10-01
I have the most confusing problem with my networking (both wired and wireless).

My computer appears to think it is the router. Yes, thats right.

My computer connects to the network, dhcp assigns it an ip address, resolv.conf is correct, and the router can see it. Here where it gets strange. 

I have no access to the outside world, and a scan of my entire network (several other perfectly functional linux boxes, including another ubuntu one...) turns up only 2 computers, with the local ip adresses of my router(192.168.1.1) and my computer(192.168.1.200). Only problem is, they look the same. In fact, if i attempt to ssh into my router's IP, i connect to my computer. Same deal if I attempt to ssh into my computer.

An NMAP of both turns up exactly the same specs... both my computer, neither my router.

This is the same on all network cards, even ones removed from other computers that I know work properly. :-k 

I'm rather experienced at using several flavours of linux, and cannot find anything that would cause this behavior, anyone got an idea?

---

### Post by lagagnon on 2006-10-01
Your routing is bad. Check the output of "sudo route -n" and see what's up.

---

