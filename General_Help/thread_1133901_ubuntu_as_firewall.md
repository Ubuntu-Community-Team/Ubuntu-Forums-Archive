---
title: "ubuntu as firewall?"
date: 2009-04-23
forum: General Help
---

### Post by JakeHinojosa on 2009-04-23
i read a post a few days ago saying that you could use ubuntu as a firewall, if thats true, how do you make it into one?

---

### Post by any.linux12 on 2009-04-23
Maybe using an Ubuntu server as DHCP and Internet server.

As ubuntu is safer than Windows it will be harder to crack it.

But I don't know if this is what you want

---

### Post by JakeHinojosa on 2009-04-23
> **any.linux12 said:**
> Maybe using an Ubuntu server as DHCP and Internet server.


huh?

---

### Post by doas777 on 2009-04-23
well basically you want to use ubuntu as a firewalling router.
to do this you need two network connections. one will be connected to your ISP network, and the other to your network.

once that is configured and both interfaces are live, you need to establish a route between them, such that all traffic for 0.0.0.0 goes out the nic attached to the ISP network.

The firewall is actually almost incidental. you would configure IPTables however you need. gufw is one gui tool for the task.

I'm thinking that ubuntu is probably heavier than you need for firewalling. I;'ve had good luck with pfSense (a bsd router os) [http://www.pfsense.org/](http://www.pfsense.org/), and there are a number of others like floppyfirewall [http://www.zelow.no/floppyfw/](http://www.zelow.no/floppyfw/)

good luck

---

### Post by Wayne_V on 2009-04-23
If you are wanting to set up a box to use as a firewall between your ISP connection and your internal network I would recommend not using your workstation.  Take a look at freesco (as in free cisco) - it will run just fine on old hardware you probably have in your closet (or can buy for < $50).

[http://www.freesco.org/index.php](http://www.freesco.org/index.php)

---

