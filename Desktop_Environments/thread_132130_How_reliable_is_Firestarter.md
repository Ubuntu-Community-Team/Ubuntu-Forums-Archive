---
title: "How reliable is Firestarter?"
date: 2006-02-17
forum: Desktop Environments
---

### Post by Postman on 2006-02-17
I know this is a minor question more out of curiousity but since I've had to use a static IP address (the IP I use doesn't support Linux systems so I can't use DHCP) and since I've installed Firestarter, I've had alot of hits to my computer from various sources so I was wondering how reliable Firestarter is as a firewall.  I'm not paranoid or anything and I don't think I have anything of value to my computer except access to my bank and stuff through Firefox and maybe my library of MP3's but that's it.  Thanks.

---

### Post by uopjohnson on 2006-02-17
Well to start with firestarter itself is not a firewall at all it is merely a configuration tool for iptables with is the built in linux firewall.
Iptables is the best software firewall you can get and if used properly is very secure.  
As far as I know firestarter does a real good job of properly configuring iptables so you should be in real good shape.

---

### Post by Postman on 2006-02-17
Where can I find this IPtables program?  I can't seem to find in the "Add Applications" section of my computer.  Thanks.

---

### Post by ubuntu-mike022465 on 2006-02-17
[QUOTE=Postman]Where can I find this IPtables program?  I can't seem to find in the "Add Applications" section of my computer.  Thanks.[/QUOTE]

IPtables is a standard install for most Linux distros.  It's already on your system right now, just open a terminal, type in at the prompt> iptables --help and you'll see a list of commands to use with iptables. Plus, it's a commandline app.


M.

---

### Post by arctic on 2006-02-17
Before you even consider configuring iptables manually, read some documentation on iptables. "man iptables" is a good start. These links add more information:
[http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html](http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html)
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)

---

### Post by Treebeard on 2006-02-17
[QUOTE=uopjohnson]Well to start with firestarter itself is not a firewall at all it is merely a configuration tool for iptables with is the built in linux firewall.
Iptables is the best software firewall you can get and if used properly is very secure.  
As far as I know firestarter does a real good job of properly configuring iptables so you should be in real good shape.[/QUOTE]
I would not call IPtables a "firewall", It's a packet filter.
But I agree that it does it's job well..
Firestarter makes it a bit easier for you to setup the iptable rules, this could be sometimes tiresome.

---

### Post by SuTuRa on 2006-02-17
[QUOTE=Treebeard]I would not call IPtables a "firewall", It's a packet filter.
But I agree that it does it's job well..
Firestarter makes it a bit easier for you to setup the iptable rules, this could be sometimes tiresome.[/QUOTE]

A firewall is a packet filter....

---

