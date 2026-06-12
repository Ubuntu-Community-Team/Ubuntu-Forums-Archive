---
title: "Networking issues"
date: 2005-05-25
forum: Desktop Environments
---

### Post by BinaryGrind on 2005-05-25
I'm having network issues. When I first installed Ubuntu, I could get the full 100Mbps on my local net work and could average about 315kbps on my cable connection. Now I can only average about 24kbps for both my local network and my cable.

I know its has something to do with linux because when I boot into windows (yes, I dual boot :roll: ) and the network connection is fine.

Anyone have any ideas?

---

### Post by dataw0lf on 2005-05-25
Could you give me the output of 'mii-tool -v' from a console, please?

---

### Post by BinaryGrind on 2005-05-25
```
phate@Fiend:~$ sudo mii-tool -v
eth0: negotiated 100baseTx-FD flow-control, link ok
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

```

What does that tell you?

---

### Post by BinaryGrind on 2005-05-25
*Bump*

---

