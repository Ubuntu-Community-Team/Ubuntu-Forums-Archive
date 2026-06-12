---
title: "Serving Half-Life"
date: 2006-03-22
forum: Gaming &amp; Leisure
---

### Post by jjrowan on 2006-03-22
I've been serving up Half Life games for years on my Red Hat Linux servers without problems.   One of my somewhat computer illiterate "friends" wanted me to install Half-Life dedicated server on his recently built SuSE 10 server.  Unfortunately the half-life executable core dumps every time it tries to load.  I downloaded and installed Ubuntu then pulled down the latest binary for Half-Life and it runs on Ubuntu but I cant get Ubuntu to open ports so gamers can connect.  I tried interactive IPTables and Firestarter but I'm left with a dedicated server running but unable to connect.  It is not my Linksys router either as I can not connect from my Windoze XP PC.

I've been Googling, searching Yahoo and Ubuntu for a week now but the only thing I've accomplished is getting secure shell to accept connections on the Ubuntu machnie. 

Can someone please tell me how I can open a range of UDP ports to host a half-life dedicated server on Ubuntu (port 27015 - 27030)?

---

### Post by frodon on 2006-03-23
Firestarter just set for you iptables rules but you seems to need an advanced use of firewalling so i really advice you to set iptables rules yourself.
Anyway the command to open port 27015 - 27030 in udp is : ```
iptables -A INPUT -p udp --sport 27015:27030 -j ACCEPT
iptables -A OUTPUT -p udp --dport 27015:27030 -j ACCEPT
```

---

### Post by jjrowan on 2006-03-23
I had tried those before without success.  I tried them again, still no joy.

I need to flush my IP Tables and start from scratch.  I can't do that unfortunately for several hours as I'm compiling a custom kernel in a secure shell window, if I flush the tables I'll lose the session I'm generating the kernel in.

I installed Webmin to manage the iptables firewall but Ubuntu apparently stores the configuration in a location Webmin is unfamiliar with.  I've created rules with Webmin, saved them then run iptables-restore <file from webmin> but that did not get gamers communicating with half-life either. 

Where does Ubuntu keep the iptables rules it uses when the server boots up?  Is there a configuration file I can modify to tell it to use different rules created by Webmin?

---

### Post by merize147 on 2006-03-29
You have to create the config files and have the system look for the new file.

I use the following structure and file name then have the interfaces file call the custom file:

/etc/iptables_rules/custom


Check out:

[https://wiki.ubuntu.com/IptablesHowTo](https://wiki.ubuntu.com/IptablesHowTo)



Happy Trails,
Merize

---

