---
title: "how do i know if my firewall is on"
date: 2006-01-19
forum: General Help
---

### Post by njzillest on 2006-01-19
how do i know if my firewall is on? 

my p2p client (gtk gnutella sais there is a firewall blocking all tcp and udp ports) 

i downloaded firestarter through apt-get 

can somebody tell me if its my firewall, or do i have to port forward on my router (like bit torrent) 

what else do i need to know to get my GTK gnutella up and working along with MLdonkey..


I DO NOT USE P2P FOR ILLEGITMIT REASONS

---

### Post by darth_vector on 2006-01-19
[QUOTE=njzillest]how do i know if my firewall is on?[/quote]to turn the firewall off you can do something like```
sudo /etc/init.d/firestarter stop
sudo /etc/init.d/network restart
```should stop the firewall (if its running) and reset your iptables to default settings.

[QUOTE=njzillest]I DO NOT USE P2P FOR ILLEGITMIT REASONS[/QUOTE]
yeah, none of us do ;-)

---

### Post by bobyang on 2006-01-19
or you can check:
sudo iptables -L

---

### Post by grandmaster on 2006-01-20
Have a look at Webmin.

You can edit firewall settings via that.

---

### Post by frodon on 2006-01-20
you can use the policy tab to enable some ports needed for p2p clients, for example bittorent : [http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)
You can use this command to see if the firewall : ```
sudo /etc/init.d/firestarter status
```

---

### Post by John Jason Jordan on 2006-01-20
[QUOTE=frodon]you can use the policy tab to enable some ports needed for p2p clients, for example bittorent : [http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)
You can use this command to see if the firewall : ```
sudo /etc/init.d/firestarter status
```[/QUOTE]
I just tried that line and got ```
sudo: /etc/init.d/firestarter: command not found
```
This is on my Ubuntu-64 Breezy laptop. Might it be a different command on 64-bit Ubuntu?

---

