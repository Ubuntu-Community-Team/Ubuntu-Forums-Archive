---
title: "iptables redundancy?"
date: 2009-05-09
forum: General Help
---

### Post by tenmilez on 2009-05-09
Is it redundant to put a drop all rule on the bottom of a chain that has a drop policy? I got all wrapped up following a slew of tutorials and I'm not sure. 

```
christopher@morgan-server:~$ sudo iptables -L -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   49  3700 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  any    any     192.168.1.2          anywhere            MAC 00:1A:4D:5C:09:9E 
    0     0 ACCEPT     all  --  any    any     192.168.1.11         anywhere            MAC 00:24:21:53:B8:81 
    0     0 DROP       all  --  any    any     anywhere             anywhere 
```

---

### Post by The Cog on 2009-05-09
Yes. Provided the policy is DROP (and your post says it is) then a drop line at the end of the rules is redundant.

---

