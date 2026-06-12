---
title: "Iptables?"
date: 2005-12-27
forum: General Help
---

### Post by rensu on 2005-12-27
Do i need to use iptables if i want to open port 2000? Or i need to use my router to open the port? Thnx for the advices. I would be very happy if you would write some examples too.

---

### Post by adie273 on 2005-12-27
If you router has a firewall, then you'll need to open port 2000 on it and forward whatever goes to that port, to port 2000 on your computer. Then open port 2000 on iptables aswell.

Should do the trick

Adie


(In fact, as an example, I run apache, so I when anyone accesses it from the internet, it goes to port 80 on my router, which i have to forward to the IP address of my computer on my home network at port 80, and then iptables handles everything that comes through port 80 on this actual computer. If that makes any sense)

---

### Post by greenway on 2005-12-27
[QUOTE=rensu]Do i need to use iptables if i want to open port 2000? Or i need to use my router to open the port? Thnx for the advices. I would be very happy if you would write some examples too.[/QUOTE]

This really depends on the specific aim in mind here. The only way of "opening" a port is assigning a server/deamon/service to listen on it. Say for example you would like your PC to serve as a webserver, you activite you webserver by letting it  listen to HTTP request coming in a port (usually 80 for HTTP).

The get a server/deamon/service to listen on a specific port defers per server/deamon/service. For some, just installing a certain package will already to the trick, other's have to entered manually into the internet superserver's configuration file.

IPTABLES is only used for filtering ip packets, network address translation and Quality of Services operations. You can use IPTABLES to block all kinds of incoming and outgoing traffic based on many different rules. Getting your feet wet with manully entering/editing/removing rules in IPTABLES can be a tricky business, I suggest using a more simple frontend such as Firestarter. Make sure it's not blocking incoming traffic to port 2000 and make sure you have a server/deamon/service listening on port 2000 and you're good to go!

goodluck!

-mattijs

---

