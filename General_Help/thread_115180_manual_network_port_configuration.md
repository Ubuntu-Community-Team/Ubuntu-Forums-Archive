---
title: "manual network port configuration"
date: 2006-01-10
forum: General Help
---

### Post by nkoplm on 2006-01-10
how can i manually change my network port settings (through a gui is fine, so longas i can do it)

for instance if i wanted to open up 1538:udp or 1539:tcp

how would i do that?

---

### Post by Suger on 2006-01-10
```
sudo apt-get firestarter
``` if we're talking of opening ports on the local computer for communication with local machines, tweaking your router if you want the ports to be accessible from the WAN.

---

### Post by renzokuken on 2006-01-10
if your firewall is a part of your router though, i suggest checking out [www.portforward.com](www.portforward.com)

---

### Post by nkoplm on 2006-01-13
[QUOTE=Suger]```
sudo apt-get firestarter
``` if we're talking of opening ports on the local computer for communication with local machines, tweaking your router if you want the ports to be accessible from the WAN.[/QUOTE]


that did not work

apt-get firestarter
or
apt-get install firestarter

:(

also, this is not a router problem, only ther sytems software firewall


any more help?

thanks in advance

---

### Post by Mr_Grieves on 2006-01-13
First off. How are you connected to the Internet? Via a router?
Are you aware you running a firewall today? If not, communications are wide open to you're system.

Check on any firewall settings by running this command in a terminal.
```

sudo iptables -L

```

Please paste output in this thread.

---

