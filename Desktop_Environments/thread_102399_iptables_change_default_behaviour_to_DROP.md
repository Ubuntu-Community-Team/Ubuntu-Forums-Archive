---
title: "iptables change default behaviour to DROP"
date: 2005-12-11
forum: Desktop Environments
---

### Post by rjeeves33 on 2005-12-11
Hi

I'm currently learning how to use iptables (please lets not start the debate about ubuntu needing/not needing a firewall :-) I am purely attempting to learn iptables.  I written somebasic rules but I think the default for INPUT & OUTPUT is ACCEPT.  How would I change this to DROP.  I basically want to lock network connection down then test my rules to see if they are actually allowing the traffic through as intended.

Thanks for any help on this matter.

silly me: iptables --policy INPUT DROP :)

---

### Post by cwaldbieser on 2005-12-12
[QUOTE=rjeeves33]Hi

I'm currently learning how to use iptables (please lets not start the debate about ubuntu needing/not needing a firewall :-) I am purely attempting to learn iptables.  I written somebasic rules but I think the default for INPUT & OUTPUT is ACCEPT.  How would I change this to DROP.  I basically want to lock network connection down then test my rules to see if they are actually allowing the traffic through as intended.

Thanks for any help on this matter.

silly me: iptables --policy INPUT DROP :)[/QUOTE]

If you set the policy for a chain, that decomes the default rule when no other rules match.  E.g.
```

$ sudo iptables -t FILTER -P OUTPUT DROP

```
sets the policy for the OUTPUT chain to drop all packets that don't match a rule in the chain.

---

