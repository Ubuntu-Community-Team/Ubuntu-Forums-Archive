---
title: "Ubuntu Network Problem"
date: 2006-02-04
forum: Desktop Environments
---

### Post by jpierre on 2006-02-04
I have just installed UBUNTU on my Machine.
At the start, the Green light on my network card was not working.:( 

I Forced it to 10baseT-HD and restarted the networking and I now have the Green light on my network card on.:) 

But the Connection properties status says that the network is disconnected.:evil:  Any tips?:confused:

Could it be iptables problem?

---

### Post by gruepig on 2006-02-05
Open up a terminal and run the following commands and post the output; this will assist in debugging:

ifconfig -a
route -n
cat /etc/network/interfaces

---

