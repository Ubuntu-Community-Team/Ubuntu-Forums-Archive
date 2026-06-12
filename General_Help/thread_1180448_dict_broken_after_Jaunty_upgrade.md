---
title: "dict broken after Jaunty upgrade"
date: 2009-06-06
forum: General Help
---

### Post by InkyDinky on 2009-06-06
Dict no longer works after upgrading from Hardy.

Here is what I get
```
dict argent
Cannot connect to any servers (use -v to see why)

```
running said gives ...
```
dict -v argent
Configuration file:
   server localhost
   server dict.org
   server dict0.us.dict.org
   server alt0.dict.org
Cannot connect to any servers

```

I don't think it is firewall related.  Here is some relevant info:

```
sudo iptables -L -v -n
Chain INPUT (policy ACCEPT 42 packets, 6644 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 45 packets, 8062 bytes)
 pkts bytes target     prot opt in     out     source               destination 

```
and
```
sudo ufw status
Status: inactive

```
I don't know anything about iptables but I don't think it is running anyway.
```
service iptables stop
$iptables: unrecognized service
```

Do I need to forward any ports? (I don't see why since it worked previously..)

---

### Post by InkyDinky on 2009-06-07
Well I didn't do anything special but dict works today.
I didn't uninstall/reinstall/remove or do anything.
I could even ping dict.org and all.  Who knows maybe my ISP didn't like it.

---

