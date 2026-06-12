---
title: "I was recommened to disable the firewall"
date: 2007-10-09
forum: Desktop Environments
---

### Post by battlecry on 2007-10-09
I have a bellsouth.net DSL and I am not able to connect with it.  One suggestion was to disable the firewall.  How do you do that and where do you find the firewall.

---

### Post by mivo on 2007-10-09
Ubuntu does not install a firewall by default. Unless you manually installed one (i.e. Firestarter), you are not running one. Are you using a router? It is possible that it has a built-in firewall. Brand and model would be useful to know in that case.

---

### Post by JBAlaska on 2007-10-09
Actually, Ubuntu comes with iptables by default. You can control it with a frontend app like firestarter or guarddog (KDE) .

You should however be able to access port 80 (http) without having to modify iptables.
Give us some more info on your connection problems and the output from:
```
ifconfig
```

---

### Post by 3rdalbum on 2007-10-10
The firewall that comes with Ubuntu is not configured by default; or rather, it is configured to let everything through.

Can you get into the modem's web-based configuration interface? (usually at [http://192.168.1.1](http://192.168.1.1))

---

