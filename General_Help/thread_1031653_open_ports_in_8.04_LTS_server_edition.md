---
title: "open ports in 8.04 LTS server edition"
date: 2009-01-05
forum: General Help
---

### Post by hosdes on 2009-01-05
How do I open ports in our ubuntu 8.04 LTS server edition?  These are port available through our ip using a browser.

---

### Post by Titan8990 on 2009-01-05
By default, all ports are open but that doesn't mean there is a service listening on those ports.

In Linux netfilter is the firewall built in to the kernel. You may see different flavors of firewalls such as ufw or Guarddog but they all do the same thing, alter IPTABLES (netfilter).

To check your current IPTABLES configuration:

```
sudo iptables -L
```

By default you will have default acceptance policies with not rules in the chains.

For more information on IPTABLES: [http://www.netfilter.org/index.html](http://www.netfilter.org/index.html)

The best way to check for ports that have services listening is nmap. Nmap is available for Windows or Linux. You can install in Ubuntu but it won't do much good running it from the local machine.


What exactly was it that you were trying to accomplish?

Also, Linux servers do not have GUIs, thus no web browser, unless you are using something like lynx.

---

### Post by lykwydchykyn on 2009-01-05
Assuming you're using ufw for the firewall, the command is:
```

sudo ufw allow portnumber_or_servicename

```

...where portnumber_or_servicename is the name of the service, or the number of the port respectively.

---

### Post by hosdes on 2009-01-05
how can I tell what firewall I am using?

---

### Post by hosdes on 2009-01-05
do I have to worry about tcp or ucp?  incoming and outgoing traffic.

---

### Post by Titan8990 on 2009-01-05
I told you in my first post. You are ALWAYS using netfilter. There are just different programs for altering netfilter.

If you have not made changes to iptables, then ALL of your ports are open.

> do I have to worry about tcp or ucp? incoming and outgoing traffic.


This depends on the program that you use to modify iptables. If you want that type of control, then you can have it. Creating IPTABLES scripts makes netfilter one of the most configurable firewalls out there. In fact, many hardware firewalls use netfilter.


If you want to use something simple like ufw mentioned above, type the following in to the terminal:

man ufw

---

