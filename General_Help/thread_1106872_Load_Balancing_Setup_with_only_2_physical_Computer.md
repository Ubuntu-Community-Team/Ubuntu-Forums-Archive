---
title: "Load Balancing Setup with only 2 physical Computers (no virtuals)"
date: 2009-03-26
forum: General Help
---

### Post by zeepal on 2009-03-26
Hello Guys,

I have been doing some research as I want to setup a load balancing environment for fun and learning.

How ever I am currently stuck with the challenge of setting up 2 physical servers to run both Apache2 and MySQL on them with no dedicated server for the "ldirectord" daemon.

I have been unable to find any HowTo's or Tutorials for this but I want to see what opinions you guys have on doing this with only 2 physical boxes and not going virtual.

I believe the following may work but I could be wrong:

_Box 1:_
_Running:_
Apache2 (synced configs and files)
MySQL (replicated etc)
ldirectord (always on as it being the primary director for the cluster)

_Box 2:_
_Running:_
Apache2 (synced configs and files)
MySQL (replicated etc)
ldirectord
Heartbeat (to check if Box 1 goes down to start up ldirectord on itself if it does go down)

_IP Addresses as follows (example):_
Cluster: 192.168.1.10
Box 1: 192.168.1.11
Box 2: 192.168.1.12

The physical connections for the servers would all be connected to the same switch with 1 NIC and the switch going to the gateway (IPCop Firewall on Orange network).

Could you guys please poke holes in my idea if you can and let me know what recommendations you have?

_Few questions I think that may need answering:_

Does the ldirectord require its own IP (like in a normal howto with 4 physical boxes, [http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04)?](http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04)?)

Do the cluster servers need to be behind a director for it to work? If so how does windows do it without the servers being behind a cluster host?


P.S. If this is in the wrong category I'm sorry...

---

### Post by jerrrys on 2009-03-27
dose not load Balancing need its own software

---

### Post by zeepal on 2009-03-29
> **jerrrys said:**
> dose not load Balancing need its own software

 - ldirectord is the program that directs the new requests to the next server inline
 - IPVS allows the cluster servers to listen to another IP (which is the cluster IP in this case from ldirectord)

The above is what I currently know and understand if anyone believes this is wrong please let me know. :D

---

