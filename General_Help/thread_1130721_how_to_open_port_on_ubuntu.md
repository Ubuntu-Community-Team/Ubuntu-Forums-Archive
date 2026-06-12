---
title: "how to open port on ubuntu"
date: 2009-04-20
forum: General Help
---

### Post by pow155 on 2009-04-20
I'm using Transmission bt which comes with ubuntu and listen to port 6881 which the program say its close.
How do I open the port 6881 on ubuntu?
thanks

---

### Post by Yashiro on 2009-04-20
Unless you have closed them manually, they're all open by default.

The problem probably lies with your router.

---

### Post by zvacet on 2009-04-20
Port should be open when you start Transmission.You can check ports with [Guwf]("http://www.associatedcontent.com/article/1077814/guwf_a_graphical_interface_to_uncomplicated.html") but like Yashiro said check your router first.

---

### Post by uncle-c on 2009-04-20
I know many Netgear routers have everything set to deny everything and it is up to the user to open the ports by getting into the router settings / config page.

---

### Post by kpkeerthi on 2009-04-20
> **pow155 said:**
> I'm using Transmission bt which comes with ubuntu and listen to port 6881 which the program say its close.
How do I open the port 6881 on ubuntu?
thanks

Also, I suggest you use a higher bittorrent port (56881, for instance) than the standard 6881. Most ISPs throttle the standard ones down.

---

### Post by pow155 on 2009-04-20
thanks for the reply. I use this command line, and it work. 

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

---

### Post by kevdog on 2009-04-20
It would be interesting if you actually posted your entire iptables ruleset, since obviously you have changed the default ACCEPT policy without telling us this piece of information.  Although the statement you provided does work, I also think you need an additional statement to keep ESTABLISHED connections connected within iptables.

---

### Post by Yashiro on 2009-04-20
Well done. :)
But you must have blocked all ports previously with iptables for this to solve your problem.

---

### Post by pow155 on 2009-04-20
ok, somehow when I restart, the port is close according to transmission bt.
here's my iptables if it help:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:56881 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:56881 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:6881 
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT]: ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere     
```
what can i do to fix this so transmission will show that the port is open? or is the reason not within the iptables, but somewhere else?

---

