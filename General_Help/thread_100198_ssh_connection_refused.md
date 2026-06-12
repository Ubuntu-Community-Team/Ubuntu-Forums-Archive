---
title: "ssh: connection refused"
date: 2005-12-07
forum: General Help
---

### Post by _jane_ on 2005-12-07
Hello. I've just upgraded from Ubuntu 5.04 to 5.10 and everything has been working like a dream but: 
When I tried to reach my computer from a friends computer via ssh, it kept saying "ssh: Connection refused, port 22". Ok. Was I behind a firewall? most likely yes. I started a program called firestarter and opened the port no. 22. A few days passes and I'm at that same computer again trying to get through via ssh. Again, the same message appeard and I'm clueless. Can someone help me? Is there an another firewall that still refuses the connection or..?
with the 5.04 version all of this worked just fine without any configuration needed.

---

### Post by michael_salcher on 2005-12-07
let's start at the beginning: are you sure you have a ssh server running?

---

### Post by _jane_ on 2005-12-07
Well... probably not then.. the 5.04 ubuntu probably had an ssh server installed. What should I do?

---

### Post by michael_salcher on 2005-12-18
```
sudo apt-get install openssh-server
```

---

### Post by DaMasta on 2005-12-18
Also, you need to have port 22 open in your firewall (if you have one running).

---

### Post by kosmic on 2005-12-18
Also don't forget if your computer is conected with a router to the internet, open port 22 on the router to your machine :) search for NAT :) or DMZ zone in your router configuration, or Port forward

---

### Post by alamba on 2005-12-18
you also might want to run a check by:
nmap localhost
to see if your server is configured properly and listening on port 22.

Akshay

---

