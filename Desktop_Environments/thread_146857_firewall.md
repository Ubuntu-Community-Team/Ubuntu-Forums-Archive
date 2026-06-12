---
title: "firewall"
date: 2006-03-19
forum: Desktop Environments
---

### Post by ESPOiG on 2006-03-19
does ubuntu have a inbuilt firewall... and if it does what is the command to kill it and any other commands that it may have... if ubuntu doesnt have a firewall im in trouble and ill start blaming my isp :P

---

### Post by dermotti on 2006-03-19
just iptables, but it shouldnt be blocking anything.

you can download lokkit, its a newb frontend for iptables, and have it disable all firewall rules, just in case you added some on accident.

---

### Post by ESPOiG on 2006-03-19
yeh that is fine... wen u dont have probs with actual net access... i just wanna know the commands

say the one for disabling the firewall altogether :D plz

on another note how do i stop the pinging session cuz wen i ping a machine it just keeps goin

---

### Post by Steve1961 on 2006-03-19
[QUOTE=ESPOiG]yeh that is fine... wen u dont have probs with actual net access... i just wanna know the commands

say the one for disabling the firewall altogether :D plz

on another note how do i stop the pinging session cuz wen i ping a machine it just keeps goin[/QUOTE]


Can't help you with the IP tables command I'm afraid but try using the following to ping:

ping -c 3 <ip address>

---

### Post by 5-HT on 2006-03-19
[quote=ESPOiG]the one for disabling the firewall altogether [/quote] 
Unless you've installed a firewall or are using your own iptables, ubuntu will not be blocking any outgoing connections. 
By default, only world-listening ports are closed. So there isn't really anything to turn off.
If you install something that needs to open up a port, such will be done automatically.

[quote=ESPOiG] on another note how do i stop the pinging session cuz wen i ping a machine it just keeps goin [/quote] 
 ctrl+c

(you can also specify the number to use. 'man pingman' describes all the options)

*Edit: beaten to it

---

