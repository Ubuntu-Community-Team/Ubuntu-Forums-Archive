---
title: "I set up a ftp on network but i want one on the net"
date: 2006-06-06
forum: Desktop Environments
---

### Post by CameronCalver on 2006-06-06
Hello i set up a ftp with proftpd but it is only on the network
 I would like to set one up on the net for people to download from but i dont know what program to use and i dont no how to obtain a public ip address can some1 help me with a good step by step

---

### Post by timmeeej on 2006-07-11
[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

and then google for: "port mapping"

you'll have to forward port 22

edit:
maybe this could be usefull:

[http://www.ubuntuforums.org/showthread.php?t=39566&highlight=proftpd+ip](http://www.ubuntuforums.org/showthread.php?t=39566&highlight=proftpd+ip)

---

### Post by Thund3rstruck on 2006-07-11
You set up the externam one the same way as the internal one except you need to set it to listen on a seperate port (as mentioned port 22 is fine). Have your router forward traffic on port 22 to your FTP server. 

If you're using a router then look at the status tab for your internet IP address. Thats the address clients use to connect

[ftp://myUser:myPassword@MyInternetIP:Port#](ftp://myUser:myPassword@MyInternetIP:Port#)

---

