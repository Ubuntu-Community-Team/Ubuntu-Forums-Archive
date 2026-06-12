---
title: "Konqueror - smb:/ -  Cannot find any workgroups"
date: 2005-06-17
forum: Desktop Environments
---

### Post by kubuntuuser on 2005-06-17
Hello everyone

Before I upgraded to kde3.4.1 browing windows shares on a windows box worked correctly. 

Now whenever I goto smb:/ i get the error 
[INDENT]"Cannot find any workgroups on your local network" [/INDENT] 

If I do **smb://machine_name**  I can browse the windows boxes shares so smbd and nmbd are running. 

I have also tried reinstalling
   - konqueror packages 
   - samba packages

Has anyone else experienced the same problem and has anyone got a fix for it

---

### Post by beefsprocket on 2005-06-17
Are you in the same workgroup that you are trying to browse? I cannot browse other computers on my network unless samba is configured to be a part of the specific workgroup in which the others systems reside.

---

### Post by kubuntuuser on 2005-06-18
Yeah.

Both my kubuntu machine and win boxes are in the MSHOME workgroup.

I get a password prompt if i try to access my kubuntu box from windows.

---

### Post by skyboy on 2005-06-20
sure you dont have any firewall around ? on your ubuntu machine (ICMP servives have o be allowed)
 check iptables --list

---

### Post by kubuntuuser on 2005-06-20
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Thanks for your reply. 
This is the output from the iptables --list command. Unfortunately i dont know what I am looking for


There is no firewall that I know of running. No xp firewall and no zone alarm etc.

My linux box also does not have a firewall running

---

### Post by kubuntuuser on 2005-06-28
OK after some playing around this may be a problem not with my linux box but my network 

I have a Belkin router that put simply is a joke not a router. 


my setup at home is 
[router]
    |
    |
[switch]---->[linux box]
    |
    |
   \ /
[win box]

If I unplug the connection to the router and reboot both machines i can browse the network perfectly. 

I have also found that the windows box is suffering from the same problem it cannot browse the network. My only conclusion is that it must be the router thats up the swanny as browsing works intermitently

Am hoping to get my hands on a new router so I can test my theory

Many thanks for all those that have looked

---

### Post by gingermark on 2005-08-07
Hi, I'm having the same trouble.

I recently played around with Firestarter, but I'm hardly a security guru and it was all a little over my head.

I did iptables --list and got the following:
```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  10.0.0.2             anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  10.0.0.2             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  10.0.0.7             10.0.0.2            tcp dpt:domain
ACCEPT     udp  --  10.0.0.7             10.0.0.2            udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

``` 

I've currently got kdenetwork-filesharing, konq-plugins, libsmbclient, python2.4-samba, samba-common, smb4k, smbclient and smbfs installed - I think they're all the relevent packages.

Any help would be appreciated,
many thanks,
gingermark.

---

### Post by gingermark on 2005-08-09
Hey,

I still haven't managed to resolve this on my own. I thought I'd post in this thread as to not clutter the forum, but if the etiquette here is to start a new thread for each person's problem I could do.

Thanks,
gingermark.

---

