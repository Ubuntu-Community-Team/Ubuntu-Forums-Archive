---
title: "firestarter works on one computer not on the other"
date: 2009-02-08
forum: General Help
---

### Post by mamboze on 2009-02-08
i have two computers connected separately to a hub and then on to a router. Both OSs intrepid, recently installed. Both connect to internet OK, but on one, firestarter runs and on the other, it doesn't, giving an error message 
'Failed to start  
The device eth0 is not ready' 

and the firestarter network display shows 
eth1 with data flow but etho with none

Iptables doesn't seem to be running here because
$ sudo iptables -L
[sudo] password for roy: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

while for the other machine

$ sudo iptables -L
[sudo] password for carlos: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dsldevice.lan        anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dsldevice.lan        anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'   
etc etc

On the firestarter-OK computer the network display shows eth0 with data flow - (eth1 is not displayed).

Sorry for the rather long-winded explanation :) But this is baffling me, why the difference between iptables?. I would be grateful for any help.

BTW I hope this is the right forum for this post topic.

---

### Post by Nepherte on 2009-02-08
On the computer where firestarter doesn't work, go to firestarter's preferences and pick device eth1 somewhere. That being said, do you need firestarter to meddle with your firewall rules? The default rules are good enough most times. I'd also use gufw instead of firestarter if you really have to change something.

---

### Post by mamboze on 2009-02-08
Hi Nepherte,

thanks, it works. talk about missing the obvious :)

---

