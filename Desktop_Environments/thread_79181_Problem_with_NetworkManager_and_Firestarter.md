---
title: "Problem with NetworkManager and Firestarter?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by gila_monster on 2005-10-19
After reading some good advice on these forums, I finally got 5.10 to where I like it. I am running networkmanager, which seems to work all right as far as it goes. When I remove the wire to go mobile, nm connects smoothly to the wireless, and vice versa.

The problem is that my applications (Thunderbird and Firefox) don't seem to pick up on the change. They do not want to use the new connection. I have to finagle with the configuration to get them to recognize the wireless. Generally, when I go back to the previous connection, they're happy.

As it happens, I am also running Firestarter. As that's basically a front end for iptables (as I understand it, correct me if I'm wrong), I would think that it would not, of itself, be causing a problem. But I wonder, because once when I was having the nm problem, I went into Firestarter and changed the "connected network device" from eth0 to eth1, which made everything recognize the wireless. I'm afraid I don't know enough about Firestarter yet to know if this is an expected behavior.

Any suggestions appreciated.

gila.

---

### Post by chanders on 2005-10-20
I think firestarter intercepts all traffic going to the internet. When you change your NIC, firestarter does not know that this is the new route to the internet.

My advice - when you change your connection, let Firestarter know. ;)

---

