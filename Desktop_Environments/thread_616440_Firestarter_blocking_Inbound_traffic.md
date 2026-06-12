---
title: "Firestarter blocking Inbound traffic"
date: 2007-11-18
forum: Desktop Environments
---

### Post by garydem on 2007-11-18
I am using Firestarter 1.0.3.6

I cannot set the inbound policy to allow my LAN hosts to connect to the host running Firestarter.  I have set the inbound policy to X.X.X.X/24 but the firewall blocks my traffic.  Also tried X.X.X.X/255.255.255.0

When I disable Firestarter my traffic flows fine.  Any suggestions?.


Gary

---

### Post by Linicks on 2007-11-18
Not a solution, but I found this at work where I have to run through a proxy.  No matter what I do, firestarter blocks the sub-net range, and the only way I can get http to work is turn it off.

It is peculiar indeed.

Nick

---

### Post by hetLemming on 2008-01-13
I have only a "dangerous level of awareness" when it comes to networking, but I think you can do it three different ways, all three of which apply to the entire subnet:

1) You could add an inbound policy rule that looks like this: 192.168.0.
2) You could add an inbound policy rule that looks like this: 192.168.0.0/24
3) You could add an inbound policy rule that looks like this: 192.168.0.0/255.255.255.0

Perhaps someone more knowledgeable that me could explain how these approaches differ?  All three seem to work for me.

---

