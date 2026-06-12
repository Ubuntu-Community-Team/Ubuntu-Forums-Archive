---
title: "How to retain IP adress obtained from DHCP server"
date: 2005-01-08
forum: Desktop Environments
---

### Post by istoyanov on 2005-01-08
I have an Ubuntu workstation on a Windows network that gets a different IP adress from the DHCP-server on every reboot. Interestingly, this is not the case with the other Linux box (running Slackware) on the same network (I can't figure out why this is so). Is it possible to retain somehow the IP of the Ubuntu-powered PC?

Tanks in advance for any advice!

---

### Post by tiiim on 2005-01-08
[QUOTE=istoyanov]I have an Ubuntu workstation on a Windows network that gets a different IP adress from the DHCP-server on every reboot. Interestingly, this is not the case with the other Linux box (running Slackware) on the same network (I can't figure out why this is so). Is it possible to retain somehow the IP of the Ubuntu-powered PC?

Tanks in advance for any advice![/QUOTE]
 i had problems on windows where it couldnt let me link Ubuntu every so oftern to i had to either repair on xp or run the network config again. However on my uni network it works fine under dchp.

Try the network properties for the connection on Ubuntu see if there anything on the tabs. There some windows networking options on it. but that all i can offer im afraid. I sure someone else must no more.

---

### Post by mrosenlof on 2005-01-08
This is usually a feature of the DHCP server, not of the clients.  All DHCP servers that I'm aware of have some way to specify if the computer with the MAC address of 'X' asks for a configuration, give it 'Y'.

Perhaps this has been set up for the slackware box, but not your ubuntu box.  Talk to the administrator of the server.

---

### Post by yahnahgi1012 on 2006-05-10
hi guys! im just a beginner, well i have same problem on how to retain my IP address, is there some one who can tell me clearly what 2 do.

thanks

---

### Post by vark on 2007-01-01
Hello fellow linuxers,

I was used to having dhcp in my modem router. 
With Suse linux 8.2 up to 10.1, pc and servers always retained their ip after reboot.
Now with Kubuntu 6.10 is see a new ip after reboot.
I did not want a static ip, because that easily leads to problems in reaching the server in question.
For me the solution was simple; in my Alcatel/speedtouch 500series modem/router 
(Menu; Advanced/DHCP), 
I can lock the ip to the MAC-adress of the ethernet card.
Problem solved,

happy tuxing,

vark

---

