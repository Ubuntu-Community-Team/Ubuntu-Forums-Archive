---
title: "Does Firestarter work even when closed and not on applet?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by michaeljb2005 on 2006-06-03
Does firestarter work even when closed and not on applet?

---

### Post by Ramses de Norre on 2006-06-03
Yes it does.

---

### Post by jgoguen on 2006-06-03
The firewall part of it?  Yes.  Firestarter applies rules to iptables, after that the firewall is handled by iptables.  Firestarter is a management and observation tool, not the actual firewall.  Now if you want to still be warned  and observe your firewall, then you need ti have it running at least in the tray, but if you're happy with just the firewall protection then you can close it.

---

### Post by michaeljb2005 on 2006-06-03
Thanks for the reply.

---

### Post by michaeljb2005 on 2006-06-03
If I don't have it on the startup menu will it automatically start or do I need to add it?  If I need to add it, can I add it without it querying me for sudo password on startup?

---

### Post by hotani on 2006-06-03
you don't need to add it. It is a little misleading in that it disappears when not actually "open." However, it *is* doing its thing. You can test it by closing off SSH (port 22), close firestarter, try to ssh into your machine, then open it and try again.

---

### Post by jgoguen on 2006-06-03
The reason for this is that, like I said, Firestarter doesn't actually handle the firewall it just ovserves and modifys it.  If you want to verify that the firewall is in place even though Firestarter isn't there, look at the iptables rules:
```
sudo iptables -L
```
If you have no rules (and thus no firewall) you see something like this:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
If you do have rules, you'll see them in these chains.  They look something like this:
```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
```

---

### Post by michaeljb2005 on 2006-06-03
[QUOTE=jgoguen]The reason for this is that, like I said, Firestarter doesn't actually handle the firewall it just ovserves and modifys it.  If you want to verify that the firewall is in place even though Firestarter isn't there, look at the iptables rules:
```
sudo iptables -L
```
If you have no rules (and thus no firewall) you see something like this:

If you do have rules, you'll see them in these chains.  They look something like this:
```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
```[/QUOTE]

Does this mean I have the firewall or not?  This isn't all the input, only about a fourth of it.

Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:4662:4663
ACCEPT     udp  --  anywhere             anywhere            udp dpts:4662:4663
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5190
ACCEPT     udp  --  anywhere             anywhere            udp dpt:5190
LSI        all  --  anywhere             anywhere

---

### Post by jgoguen on 2006-06-03
Yes, that output means that you most certainly have a firewall in place.

---

