---
title: "MultiPlayer Gaming Problem"
date: 2007-06-18
forum: Gaming &amp; Leisure
---

### Post by bamesah on 2007-06-18
Hi,

I used to have an Internet connection with an automatic IP setting and a manual Proxy,
now after changing our ISP, I have manual IP and Proxy and two DNS numbers, but from that time, I can't play any game Online.

In Armagetron: it says Timed out, it send login information and then Timesout
In Battle for Wesnoth : Just try to connect to server without any ue
In Nexuiz : Lags when trying to see available servers ( This lag continued for 40 min.)

Is there something that i should do or a setting that i should change before playing these Games??

---

### Post by bamesah on 2007-06-19
no ideas?

---

### Post by Cappy on 2007-06-19
Try turning of IPv6
```
gksudo gedit /etc/modprobe.d/aliases
```

Change the line "alias net-pf-10 ipv6" to "alias net-pf-10 off". Save & reboot.



I looked up the Nexuiz master server, it seems to be dpmaster.deathmask.net

Does ```
dig dpmaster.deathmask.net
```
output something like
```

; <<>> DiG 9.3.4 <<>> dpmaster.deathmask.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 9216
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;dpmaster.deathmask.net.                IN      A

;; ANSWER SECTION:
dpmaster.deathmask.net. 14364   IN      A       64.22.107.125

;; AUTHORITY SECTION:
deathmask.net.          14364   IN      NS      ns2.deathmask.net.
deathmask.net.          14364   IN      NS      ns1.deathmask.net.

;; Query time: 10 msec
;; SERVER: 68.1.18.237#53(68.1.18.237)
;; WHEN: Tue Jun 19 02:10:52 2007
;; MSG SIZE  rcvd: 92

```
?
Post the response if you still have trouble after disabling ipv6 and rebooting.

---

### Post by bamesah on 2007-06-19
> **Cappy said:**
> Try turning of IPv6
```
gksudo gedit /etc/modprobe.d/aliases
```

Change the line "alias net-pf-10 ipv6" to "alias net-pf-10 off". Save & reboot.



I looked up the Nexuiz master server, it seems to be dpmaster.deathmask.net

Does ```
dig dpmaster.deathmask.net
```
output something like
```

; <<>> DiG 9.3.4 <<>> dpmaster.deathmask.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 9216
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;dpmaster.deathmask.net.                IN      A

;; ANSWER SECTION:
dpmaster.deathmask.net. 14364   IN      A       64.22.107.125

;; AUTHORITY SECTION:
deathmask.net.          14364   IN      NS      ns2.deathmask.net.
deathmask.net.          14364   IN      NS      ns1.deathmask.net.

;; Query time: 10 msec
;; SERVER: 68.1.18.237#53(68.1.18.237)
;; WHEN: Tue Jun 19 02:10:52 2007
;; MSG SIZE  rcvd: 92

```
?
Post the response if you still have trouble after disabling ipv6 and rebooting.

Yes, it gives me same output when trying to connect to nexuiz server from terminal.

But still Multiplayer feature doesn't work
Seems like the problem is that games don't use the network settings to connect to the server

---

