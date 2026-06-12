---
title: "Need good firewall."
date: 2006-08-06
forum: Desktop Environments
---

### Post by Scythe!? on 2006-08-06
Hi I havent tried editing the iptables but the Sygate test are failing, meaning im open on the internet. Is there anything I can do or is there a better firewall. Firestarter stopped my internet from working. Lokkit just wasnt working well either. I'm using a Speedtouch USB modem if that helps.

---

### Post by reacocard on 2006-08-06
USB modems tend to cause problems. you could give guarddog a try. its for kde, but i've used it and it works perfectly in gnome.

---

### Post by stormblue on 2006-08-06
Linux comes built in with a firewall.  There is no graphical user interface, so you should be protected.  Mind sharing the output of the sygate test to see what the problem is?

---

### Post by reacocard on 2006-08-06
as stormblue says, linux has a built-in firewall. firestarter, guarddog, etc. are the guis for setting up this firewall.

---

### Post by Scythe!? on 2006-08-07
The **probe test** is unable to find my computer name or what services are running.

**Security scan** reports that the following ports are closed but reported to probes:
[[IMG]http://img208.imageshack.us/img208/7431/securityqj9.th.png[/IMG]](http://img208.imageshack.us/my.php?image=securityqj9.png)
20,21,22,23,25,53,59,79,80,110,113,139,443,1080,8080,51790
This is all the ports used in the scan

**Trojan scan**, which only detects open probes was sucessful. No probes got in my machine.
[[IMG]http://img208.imageshack.us/img208/8425/trojanbd1.th.png[/IMG]](http://img208.imageshack.us/my.php?image=trojanbd1.png)[[IMG]http://img208.imageshack.us/img208/3383/trojan2jv6.th.png[/IMG]](http://img208.imageshack.us/my.php?image=trojan2jv6.png)

**TCP Scan** reports which only detects open probes on 0-1024 ports was sucessful. No probes got in.

**UCP Scan** reports testing UCP ports detects We have determined that you do not have any firewall blocking UDP ports!
[[IMG]http://img212.imageshack.us/img212/1324/ucper0.th.png[/IMG]](http://img212.imageshack.us/my.php?image=ucper0.png)[[IMG]http://img128.imageshack.us/img128/8766/ucp2km8.th.png[/IMG]](http://img128.imageshack.us/my.php?image=ucp2km8.png)[[IMG]http://img75.imageshack.us/img75/7018/ucp3uu6.th.png[/IMG]](http://img75.imageshack.us/my.php?image=ucp3uu6.png)[[IMG]http://img128.imageshack.us/img128/6729/ucp4qy1.th.png[/IMG]](http://img128.imageshack.us/my.php?image=ucp4qy1.png)[[IMG]http://img75.imageshack.us/img75/1598/ucp5df5.th.png[/IMG]](http://img75.imageshack.us/my.php?image=ucp5df5.png)

---

### Post by Scythe!? on 2006-08-07
Continued as forum only allows 8 pics per post.
Shields up common ports test has failed:
[[IMG]http://img128.imageshack.us/img128/8097/shieldwg2.th.png[/IMG]](http://img128.imageshack.us/my.php?image=shieldwg2.png)[[IMG]http://img128.imageshack.us/img128/7864/shield1ak5.th.png[/IMG]](http://img128.imageshack.us/my.php?image=shield1ak5.png)

Shields up All service ports failed: all ports closed but not stealthed.
[[IMG]http://img62.imageshack.us/img62/4834/shield2mu1.th.png[/IMG]](http://img62.imageshack.us/my.php?image=shield2mu1.png)

I need to stealth these ports, not for them to be closed. I don't understand any of the iptables stuff, and the GUI firewalls kill my connection.

---

### Post by Scythe!? on 2006-08-07
I just installed Firestarter and it killed it again. Can't connect to websites or nothing. Am I missing something here?

Edit: Just ran the Firestarter wizard again, but this time chose ppp0 instead of nas0. The web now works, need to check if downloading & games work.

Edit2:  Now I've done the wizard Shields Up reports all ports as stealth.

---

