---
title: "internet problem"
date: 2006-01-26
forum: Desktop Environments
---

### Post by SaCeR on 2006-01-26
I got a problem with my linux on my laptop.. I can't connect to the internet.. but when i make static ip i can ping other users at the network, but still can connect to the internet.. Anyone who can help me?

---

### Post by Jimmey on 2006-01-26
Probably could, if you gave's some more information about how you're trying to connect to the internet...Wired, or wirelessly? Through what card? What are the error messages you're receiving?

---

### Post by SaCeR on 2006-01-26
okay, that right..
Im have tryed both my wired and wireless and its the same problem..

when im at my schools network i can only ping people on the local network. When i try to ping other IPs like google.com or 216.236.39.104 (google.com), then i get Destination Host Unreachable..

I have made statik ip, and the currently settings is:
adress 172.27.75.177
netmask 255.255.252.0
broadcast 172.27.75.255
gateway 172.27.72.2

i have tried with DHCP, and there it was no better...

When i make "route -n" i get 2 tables:
172.27.72.0  0.0.0.0 255.255.252.0
0.0.0.0  172.27.72.2  0.0.0.0

... but this does not help.. i cant ping anything on the internet but computers on the local network is no problem..

I have tryed with windows and with fedora linux, and there was no problem..
=|

---

